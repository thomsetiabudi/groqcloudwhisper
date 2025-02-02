# Audio Chunking and Transcription

This project provides functionality to transcribe large audio files by breaking them into manageable chunks, processing them through the Groq API, and then merging the results back together seamlessly.

## Prerequisites

- Python 3.8 or higher
- FFmpeg installed on your system
- A Groq API key (obtain from [Groq Console](https://console.groq.com/keys))

## Installation

1. Clone the repository:
```bash
git clone [your-repository-url]
cd [repository-name]
```

2. Create and activate a virtual environment:
```bash
# On Windows
python -m venv venv
.\venv\Scripts\activate

# On macOS/Linux
python -m venv venv
source venv/bin/activate
```

3. Install required packages:
```bash
pip install groq pydub
```

## Environment Setup

1. Create a `.env` file in the project root directory
2. Add your Groq API key:
```
GROQ_API_KEY=your_api_key_here
```

## Usage

1. Place your audio file in the project directory

2. Update the audio file path in `audio_chunking_code.py`:
```python
# At the bottom of the file, change "audio_file_name.wav" to your audio file name
if __name__ == "__main__":
    transcribe_audio_in_chunks(Path("your_audio_file.wav"))
```

3. Run the script:
```bash
python audio_chunking_code.py
```

## Output

The script will create a `transcriptions` directory containing three files for each transcription:
- `[filename]_[timestamp].txt` - Plain text transcription
- `[filename]_[timestamp]_full.json` - Complete transcription data including metadata
- `[filename]_[timestamp]_segments.json` - Detailed segment information

## Features

- Automatic audio preprocessing to 16kHz mono FLAC format
- Chunked processing for large audio files
- Smart chunk overlap handling
- Automatic transcription merging
- Multiple output formats
- Progress tracking and timing information

## Technical Notes

- Default chunk length: 600 seconds (10 minutes)
- Default overlap: 10 seconds
- Audio is automatically converted to 16kHz mono FLAC format
- Temporary files are automatically cleaned up after processing

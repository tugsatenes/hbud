# HBud
Simple music / video player and karaoke app written in Python and GTK - Because why not

# [Website](https://swanux.github.io/hbud.html) | [Feedback](https://swanux.github.io/feedbacks.html)

# Features
- Video and audio playback (for supported formats, refer to GStreamer docs)
- Subtitle support
- Karaoke mode (synced lyrics needed in own srt format, see below for instructions)
- Static lyric (most of the time works automatically)
- Metadata editor (for audio files)
- Playlists (from folder structure)
- Seamlessly switch back and forth between video and audio playback (remembers where to continue)
- Native, lightweight and simple
- Native .deb package for Debian/Ubuntu based distros (updates through PPA)

# Generate synced lyrics

Here I'll show you how to generate synced lyrics for yourslef

### Requirements

* ~20GB of RAM (you can use swap to extend your memory)
* ~20GB of disk space
* node v12 or above (for ubuntu/debian based distros you can use [this](https://github.com/nodesource/distributions) repo)

### Installation

1. Install [AutoLyrixAlignService](https://github.com/gazugafan/AutoLyrixAlignService)
    - It'll guide you through downloading the neural network and the dependencies
2. Run the server as described above, connect to it and set things up
3. Select RAW output format, save to `aligned.txt` when ready (DO NOT copy into a file, use Ctrl+S to save it)
4. Save the plain lyrics to `lyrics.txt`
5. Run [tosrt.py](https://github.com/swanux/hbud/blob/master/tools/) from this repo like this: `python3 tosrt.py aligned.txt lyrics.txt output.srt`
7. Move and rename the resulted output file alongside your audio file

### Other methods

You can try to generate a word by word .lrc file ([here](https://lrcgenerator.com) for example), and you can try my experimental enhanced-lrc converter like this: `python3 lrc2srt.py lyric.lrc output.srt`

# Downloading music

I recommend using [spotDL](https://github.com/spotDL/spotify-downloader)

# Generate subtitles

You can use [AutoSub](https://github.com/abhirooptalasila/AutoSub) which is a nice tool if you want to generate your own subtitles.

A manual alternative is the GTK program [Gnome Subtitles](https://gnomesubtitles.org)

*Note: You can also use this program, to adjust already generated synced lyrics to different audio files of the same song.*

# Credits
* [GTK3](https://www.gtk.org) - For the GUI framework
* [GStreamer](https://gstreamer.freedesktop.org) - For the multimedia framework
* [PyGObject](https://pygobject.readthedocs.io/en/latest/) - For the Python bindings
* [Lazka](https://lazka.github.io/pgi-docs/) - For the documentation
* [AutoLyrixAlign](https://github.com/chitralekha18/AutoLyrixAlign) - For the neural network to align text to lyrics
* [srt](https://pypi.org/project/srt/) - For the Python srt module
* [mediafile](https://pypi.org/project/mediafile/) - For the wrapper around mutagen
* [mutagen](https://pypi.org/project/mutagen/) - For this extensive module
* [azapi](https://github.com/elmoiv/azapi) - For the AZLyrics API
* [pyacoustid](https://github.com/beetbox/pyacoustid) - For the AcoustID API
* [MusicBrainz](https://beta.musicbrainz.org/) and [AcoustID](https://acoustid.org/) - For the open databases

### Translation

First you have to clone this repo to `/home/$USER/GitRepos/hbud` - hbud is the root of this repository

You can then use the provided `translate.sh`:

- Add new translation: `./translate.sh new en_GB en`
- Generate `.mo` files: `./translate.sh add en_GB en`
- Update `.po` files: `./translate.sh update en_GB en`
- Update `.mo` files: `./translate.sh upgrade en_GB en`

It's important to use UTF-8 charset when needed (instead of ASCII).

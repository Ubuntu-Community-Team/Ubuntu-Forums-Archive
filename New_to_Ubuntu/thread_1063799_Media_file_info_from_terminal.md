---
title: "Media file info from terminal ?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by iKonaK on 2009-02-08
What should i do to list the audio or video file info that is shown in last tab of proprieties ?


[IMG]http://i43.tinypic.com/4g3pl3.png[/IMG]

---

### Post by earobinson on 2009-02-08
Like this:

earobinson@MinusOne:/media/media/music/weezer$ mminfo Weezer\ -\ We\ Are\ All\ On\ Drugs.mp3 
Weezer - We Are All On Drugs.mp3
|      title: We Are All On Drugs
|   language: English
|   langcode: eng
|      media: MEDIA_AUDIO
|     artist: Weezer
|       mime: audio/mpeg
| samplerate: 44100
|     length: 215.484081633
|      codec: MPEG Layer 3
|    bitrate: 234
|     fourcc: 0x55
|    trackno: 06
|   userdate: 2005
|    trackof: 12
|      album: Make Believe
|      genre: Rock
|  publisher: Geffen Records
| _Ripping tool: EAC
|  _Rip date: 2005-04-23
|       mode: joint stereo

---

### Post by earobinson on 2009-02-08
I found this anser like this:

earobinson@MinusOne:/media/media/music/weezer$ apropos metadata
DBI::DBD::Metadata (3pm) - Generate the code and data for some DBI metadata m...
e2image (8)          - Save critical ext2/ext3 filesystem metadata to a file
kfile (1)            - A commandline tool to read and modify metadata of files
mminfo (1)           - Kaa Metadata media info.
mysql_tableinfo (1)  - generate database metadata
tracker-extract (1)  - extract metadata from file and display them.

apropos is your friend!
apropos - search the manual page names and descriptions

---

### Post by iKonaK on 2009-02-08
@earobinson : yea, yea, yea ! thanks and thanks 4 the apropos 2, i didn't know about it :)

---

### Post by iKonaK on 2009-02-08
wait !? where u find "mminfo"; what version are u using, in hardy is not available :(
```
~$ apropos metadata
e2image (8)          - Save critical ext2/ext3 filesystem metadata to a file
kfile (1)            - A commandline tool to read and modify metadata of files
scrollkeeper (7)     - An open document cataloging and metadata management sy...
scrollkeeper-gen-seriesid (1) - generate a unique id for a document series fo...
tracker-extract (1)  - extract metadata from file and display them.
```

---

### Post by iKonaK on 2009-02-08
done!  is in synaptic at "python-kaa-metadata" if anyone cares :)

---


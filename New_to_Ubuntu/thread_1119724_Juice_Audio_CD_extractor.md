---
title: "Juice Audio CD extractor"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Bastun on 2009-04-08
Hi,

Made an enquiry about .oga default conversion output a few days ago. Wanted to encode as MP3 and wondered about .oga format as I was unfamiliar with it. I was kindly advised to set output format to mp3. Problem is the output format dropdown lists: flac, oga, wav and spx - no mp3. The Edit Profiles lists CD Quality MP3 but I am too thick to work out how I can set this as an output for the converter. I got the following from Help but am unclear on how the output is set:.

""You can click the Edit Profiles button to edit the available audio formats. The profile editor dialogue provides direct access to the audio conversion. Profiles are defined with GStreamer pipelines. GStreamer is the underlying multimedia library used by Sound Juicer and other multimedia applications. A full explanation of audio profiles is outside the scope of this document".


Can anyone advise on g=how to get mp3 files out?

By the way, have genned up on .oga now and understand that it is a new audio file extension designation for OGG Vorbis. Instead of using .OGG they are now using .oga for audio files. Trouble here again. Downloaded a little app called WMA&OGG 1.1 (converts either way). Doesnt want to know about .oga!!! Any advice cos I'd like to use OGG as OpenSource software.

Cheers

Regards,

---

### Post by zerhacke on 2009-04-08
sudo apt-get install lame

---

### Post by clive littlewood on 2009-04-08
Hi

In sound juicer go to edit > preferences > format and just select the option in the drop down list > CD quality Mp3.

Your output will now be Mp3.

Juicer is set to ogg by default.

Hope this helps

Clive

---

### Post by Bastun on 2009-04-08
Thanks. Got this description of Lame of Synaptic Package Manager: LAME Ain't an MP3 Encoder
Lame is a program which can be used to create compressed audio files. (Lame
aint MP3 encoder). These audio files can be played back by popular mp3
players such as mpg123. To read from stdin, use "-" for <infile>. To write
to stdout, use a "-" for <outfile>.

This package contains the frontend encoder binary.



I want to convert rip .wav files from a CD and encode to MP3 or WMA so that I can get the songs to play on my Creative Zen player. Will LAME do that?

---

### Post by Bastun on 2009-04-08
Thanks but that is my problem. The path you describe: edit > preferences > format wont allow cos it does not show MP3 !!!! Only thge 4 formats I described. MP3 is in Edit Profiles though and I want to know how I can select from there?

---

### Post by Bastun on 2009-04-08
All well now and MP3 output installed. Thanks

---

### Post by Jakey_TheSnake on 2009-04-08
[http://ubuntuforums.org/showthread.php?t=952807](http://ubuntuforums.org/showthread.php?t=952807)

^ You can also set it up to rip higher quality .mp3s, and VBR ones, see above.

---

### Post by nmsmith on 2009-04-17
So Bastun what did you do? I'm having the same issues - I have an option for mp3 in Edit Profiles, but it never appears in the Output Format drop-down menu.

I have tried installing lame and ubuntu-restricted-extras, and that hasn't made any difference.

What did you do?

---

### Post by nmsmith on 2009-04-25
bump

---


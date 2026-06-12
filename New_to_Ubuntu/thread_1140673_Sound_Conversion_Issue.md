---
title: "Sound Conversion Issue"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-04-27
Ubuntu version 9.04. Here is the scenario: I copied the contents of an audio CD to a folder in my home directory using rhythm player. I then wanted to transfer the music files to my Sansa M240 mp3 player. The files I had uploaded from the CD in my home music file folder as ogg vorbis type of files. I knew they would have to be converted to mp3 format if I were going to load them on to the Sansa audio player.

I downloaded Sound Converter. Went to the edit menu and set my preferences indicating the type of conversion I want to make; ie change to mp3. There is a plus button for adding files. So I selected it went to the folder where my music files were and put the cursor on one of them and it said open. I did expecting it to show up in the Sound Converter file window. No such luck. I have tried every way I can think of to get one of these files into Sound Converter in order to perform the conversion and I just can't seem to do it.

I got to be missing something. Just can't figure out what it is.

---

### Post by 123456789123456789123456 on 2009-04-27
I don't know much about sound converter.  Never had to use it yet.  One thing I can think of though is, does sound converter understand that file type, uh ogg vorbis?  I never heard of that format before.  that could be the problem there.  Try using rhythm player to save the files as something else, like acc formated files, and try converting them then.
sorry can't be of much help.

---

### Post by logos34 on 2009-04-27
it can read and encode to ogg vorbis by default, but you may need the gstreamer mp3 codecs (need to add them manually):

> sudo apt-get install ubuntu-restricted-extras

now try importing the folder again

---

### Post by Rog3236 on 2009-04-28
Thanks guys downloading the restricted extras package solved the problem.

---

### Post by NealKQ on 2009-05-01
Hi There, rhythmbox can be set to encode to mp3 as well as ogg and others which would save losing qualty by going through two lossy encodes. Alternatively you could possibly upgrade your player firmware to also play ogg files if can't already.

---


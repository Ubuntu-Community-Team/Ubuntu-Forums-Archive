---
title: "program to conver .flv to .mp3"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by nynoah on 2009-02-21
I have a few Flash videos that I want to convert into MP3 so I can listen to them in my car.  Not caring about the video part.  Just the music.  Is there a program that can do that?

---

### Post by lukjad on 2009-02-22
Yes. It's called ffmpeg. If it's not already installed run this command in the terminal (*Applications->Accessories->Terminal*):
```
sudo apt-get install ffmpeg
```
Some people prefer to compile it from source for one reason or another, but, eh, I don't have the time to spare. Once it's installed, open the terminal again and (assuming the files are in the home folder) type:
```
ffmpeg -i [filename].flv [filename].mp3
```
Also, if there are spaces in the name of the file (for example: Bach Violin Concerto in A minor.flv), you'll have to force the program for forget them with the backslash ("\"). Example:

```
ffmpeg -i Bach\ Violin\ Concerto\ in\ A\ minor.flv Bach\ Violin\ Concerto\ in\ A\ minor.mp3
```

---

### Post by daniel014 on 2009-02-22
[http://www.mediaconverter.org/]("http://www.mediaconverter.org/")

[http://www.zamzar.com/]("http://www.zamzar.com/")

---

### Post by eotakos on 2009-02-22
install Avidemux from the synaptic package manager - easy to use, nice gui.

load the video, from the audio menu click save, give a name and you're done!

---


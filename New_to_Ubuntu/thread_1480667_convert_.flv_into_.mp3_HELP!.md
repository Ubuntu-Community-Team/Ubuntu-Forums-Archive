---
title: "convert .flv into .mp3? HELP!"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by grobar87 on 2010-05-11
How to convert .flv into .mp3 file? Some program for lucid who can do that?
Thanks.

---

### Post by Dracona on 2010-05-11
there is an add on for firefox that will do this.

---

### Post by Ozymandias_117 on 2010-05-11
ffmpeg is a command line tool that should be able to do that. Audacity might be able to... not certain if you can import .flv into it, but you can try.

---

### Post by grobar87 on 2010-05-11
On karmic i used pytube and works great,but i dont know how to install on lucid...
ffmpeg is too complicated for me....and audacity works with audio files only...but thanks for help.

---

### Post by super kim on 2010-05-11
here's a little script that will convert any file in the folder into an mp3, it'll convert a nun if you can get her in the folder!

```
#!/bin/bash
mkdir out
for tune in *.* ; do
echo Converting $tune
ffmpeg -i "$tune" -ab 128k -acodec libmp3lame out/"$tune".mp3
done
```Instructions...
make yourself a new folder 
open gedit and paste that code into it
 save it in your new folder (i'd save it as "all")
copy the said .flv files to the folder
right click on your saved text file and set the permissions to run as an executable
double click the saved file (i called mine "all")

a folder named "out" should appear and the shiny new mp3 will be inside.

the code that makes it tick is fairly simple ```
ffmpeg -i "$tune" -ab 128k -acodec libmp3lame out/"$tune".mp3
``` you can change it to suit your needs, open a terminal and type "ffmpeg man" it's a massive manual but you can easily find the relevant stuff.

---

### Post by sandyd on 2010-05-11
winff is a gui for ffmpeg
try it.

---

### Post by Sealbhach on 2010-05-11
There's a package called [WinFF]("http://winff.org/html_new/"), it's a gui for ffmpeg. You can find it in Synaptic.

.

---

### Post by 3rdalbum on 2010-05-12
Audacity can do it as well, it will import the audio from the video file.

---

### Post by consindo on 2010-05-12
Try "soundconverter" It might work...

---

### Post by Ozymandias_117 on 2010-05-12
> **3rdalbum said:**
> Audacity can do it as well, it will import the audio from the video file.

+1 After you said it couldn't import audio from a vid, I double checked and it worked fine.

---

### Post by super kim on 2010-05-12
ok this is as simple as i can make it, you don't need to install any extra stuff to convert your files. you already have ffmpeg installed. ffmpeg will do the trick and will be faster than any thing else so if your doing a batch conversion this is ideal.

i don't see why you'd need a gui if your only converting to mp3.

i have attached a .tar file... in it is a simple bash script, i have set the permissions so it runs as an executable. you only need to put that file in your folder of flv's and double click. then a folder called "out" will have your mp3's in it.:popcorn:

you can use this script to convert any file type that ffmpeg can decode, which is pretty much everything. you can even be brave and edit the script to change the bitrate.

---

### Post by GaaraOfDSand on 2010-05-12
or, you can install jdownloader and you can convert .flv from youtube into .mp3, .mp4. and two more. :) It's a good proggie. try it

---

### Post by Ozymandias_117 on 2010-05-12
> **super kim said:**
> ok this is as simple as i can make it, you don't need to install any extra stuff to convert your files. you already have ffmpeg installed. ffmpeg will do the trick and will be faster than any thing else so if your doing a batch conversion this is ideal.

10.04 no longer has ffmpeg installed by default. ```
sudo aptitude install ffmpeg
``` will get you set to use his script.


Edit: Just glancing over that script... shouldn't ```
for tune in *.* ; do
``` be written as ```
for tune in *.flv ; do
``` just in case he has like... jpegs or something in the folder?

---

### Post by super kim on 2010-05-12
yes ozymandias you are quite right, but i did specify the script would convert _any_ file that ffmpeg can decode.
i tested it with a whole bunch of video and audio files, and jpgs too. it will create an empty mp3 for the jpgs as any other file without audio that ffmpeg can decode.

i have not yet upgraded to 0.04 yet and so did not know that ffmpeg isn't installed as standard. could anyone tell me what replaces it?

if your installing ffmpeg on ubuntu 10.04 to encode mp3s then you should use:
```
 sudo apt-get install ffmpeg libavcodec-extra-52
```
as the basic ffmpeg hasn't got all the codecs for legal reasons they say.

---

### Post by grobar87 on 2010-05-13
Thanks a lot to everyone...now i know how to convert files with your help guys.:P
Thanks again,this is the best forum ever!
btw..i use ffmpeg with winff.

---


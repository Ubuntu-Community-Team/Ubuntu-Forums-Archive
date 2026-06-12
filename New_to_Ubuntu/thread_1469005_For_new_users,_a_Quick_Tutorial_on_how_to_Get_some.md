---
title: "For new users, a Quick Tutorial on how to Get some needed utilities."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Nick.Sth on 2010-05-01
Hi, I've been using Ubuntu for 2-3 months, I'm no expert. But I want to share with the rest of you, what troubles I had, and how I resolved them. When I started I wanted a program to convert files, something to install Windows programs, etc. I'll explain to you now how to get some of those things.

How To Download YouTube Videos with Terminal.  
First, download required software by typing in: 
```
sudo apt-get install youtube-dl  
```And you're done. To download just type in 
```
youtube-dl video_url
```How To Convert Files Through Terminal. 
First, download required software by typing: 
```
sudo apt-get install ffmpeg 
```Turning images to a cideo sequence 
```
ffmpeg -f image2 -i image%d.jpg video.mpg 
```Then All you need is codes. 
To Convert FLV to MPG: 
```
ffmpeg -i old-file.flv new-file.mpg 
```To Convert FLV to Mp3 
```
mplayer -dumpaudio old-file.flv -dumpfile new-file.mp3 
```To Convert Mp4 to Mp3 
```
ffmpeg -i video.mp4 -vn -ac 1 audio1.mp3
```How to install Wine  
[FONT=Arial Black]Extremely simple. Just go to -> Applicatons > Ubuntu Software centre and type in wine.[/FONT]
If that doesn't suit you, open terminal and type the following.
 
```
sudo apt-get update 
``````
sudo apt-get install wine 
``````
sudo apt-get install winesetuptk  
``````
winesetuptk  or $ winesetup or winesetup
```
Program To Download Songs Easily 
Just install by typing in terminal: 
 
```
apt-get install nicotine
```Simple File Sharing Program /  
Just install by typing in terminal: 
 
```
sudo apt-get install gtk-gnutella
```
[I][SIZE=2]
I hope this helps you in any way, best of wishes, Nick.[/SIZE][/I]

---

### Post by 3rdalbum on 2010-05-01
Rather than use "Youtube-dl", you can usually find the video file in the /tmp directory after the video has completely buffered, but before you surf to another page or close the browser.

---

### Post by madjr on 2010-05-01
> **3rdalbum said:**
> Rather than use "Youtube-dl", you can usually find the video file in the /tmp directory after the video has completely buffered, but before you surf to another page or close the browser.

+1 tmp directory

anyway this is a good guide, but am not sure if new users want to type in commands all over the place

---

### Post by Nick.Sth on 2010-05-02
some people enjoy using terminal :P

---

### Post by Nick.Sth on 2010-05-02
wrong post:P

---

### Post by aaguilar4 on 2010-05-19
Hi guys, I actually wrote a little bash script that will ask how many videos you want to download, ask you the NAME, and URL of each video, then download the video and convert it to audio and save it to ~/Music/NAME.mp3
I use it to extract songs or tracks out of the videos, but I wanted some help in building a GUI or something to that effect. 
For the time being, everything is a bash script, so I was thinking to change it into Python in order to write a GUI with Glade. I'm by no means an expert in bash or Python, so I'm in need of help. 
Let me know if you are interested in the code or in helping me out with some tips. 
Thanks!

---

### Post by lisati on 2010-05-24
We don't support violating Youtube's terms and coditions.

---


---
title: "Youtube?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by R@inm@n on 2009-05-16
Is there an app for Jaunty that will let me download a video from youtube?
I use Firefox as my browser.

Thanks,

R.

---

### Post by spiderbatdad on 2009-05-16
You can use youtube-dl from synaptic package manager.
```
sudo apt-get install youtube-dl
```You use it from the command line by entering ```
youtube-dl <url>
```where in place of <url> you can paste in a link to the video.

There is a nice little script here. You can make a directory called bin in you home directory and create a document called ytube inside bin. Paste in this code and change the permissions to make it executable:
```
#!/bin/bash
echo Enter the youtube url to begin downloading the video.
read VIDEO
echo What is the artist of the song?
read ARTIST
echo What is the name of the song?
read NAME
youtube-dl $VIDEO -o "${ARTIST} - ${NAME}.flv"
ffmpeg -i "${ARTIST} - ${NAME}.flv" "${ARTIST} - ${NAME}.mp3"
rm -rf "${ARTIST} - ${NAME}.flv"
echo Your video is finally converted into a mp3!
```Contributed here:[http://ubuntuforums.org/showthread.php?t=855433](http://ubuntuforums.org/showthread.php?t=855433) by chris4585
Then you can run it from terminal with the command ytube. It will convert flv to mp3. You can modify it by commenting out the ffmpeg and rm -rf lines to eliminate the conversion.

---

### Post by goldblattster on 2009-05-16
If you do not mind the downloaded videos in the mp4 format, you can check [this]("http://googlesystem.blogspot.com/2008/04/download-youtube-videos-as-mp4-files.html") out. This method works in any web browser, works at the click of a button, and does not require any software to be installed.

---

### Post by Bölvaður on 2009-05-16
there will be about 5 people posting with firefox extentions... but I'd go for moving and renaming the videos directy from your /tmp director

if you dont find it press alt+f2 and copy and paste

```
nautilus /tmp
```

---

### Post by goldblattster on 2009-05-16
The file firefox downloads into your temporary folder is in the .flv file format which isn't very widely supported.

---

### Post by R@inm@n on 2009-05-16
Thank you all, I will try the methods out.


 R.

---

### Post by SunnyRabbiera on 2009-05-16
One I like to use is the download helper extension for firefox.

---

### Post by andrew.46 on 2009-06-12
Hi goldblattster,

> **goldblattster said:**
> If you do not mind the downloaded videos in the mp4 format, you can check [this]("http://googlesystem.blogspot.com/2008/04/download-youtube-videos-as-mp4-files.html") out. This method works in any web browser, works at the click of a button, and does not require any software to be installed.

Mind you newer versions of youtube-dl have a '-b'option which can be useful:

```
-b, --best-quality  download the best quality video possible
```

and this will usually download an mp4 with h264 video and aac sound.

Andrew

---

### Post by H2SO_four on 2009-06-12
> **goldblattster said:**
> The file firefox downloads into your temporary folder is in the .flv file format which isn't very widely supported.

VLC player recognizes .flv.

---

### Post by t0p on 2009-06-12
> **goldblattster said:**
> The file firefox downloads into your temporary folder is in the .flv file format which isn't very widely supported.

Every single video player I know of in Ubuntu can play flash video (.flv) files.  All you gotta do is install the appropriate codecs - if you go the 

```
sudo apt-get install ubuntu-restricted-extras
```

you'll be able to play .flv plus just about every proprietary format I can think of (.wmv,.wma,.mp3,.avi,.mp4...).  It ain't like Windows where you have to get a special .flv player.

---


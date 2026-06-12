---
title: "Convert mkv &gt; avi files?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-27
Hi all!
I need to convert an .mkv movie to an .avi, which is the converter for linux you suggest?

---

### Post by philinux on 2010-05-27
Please try the forum search.

[http://ubuntuforums.org/search.php?searchid=73379907](http://ubuntuforums.org/search.php?searchid=73379907)

---

### Post by ron999 on 2010-05-27
Hi
You could try WinFF first.
From here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by MrWES on 2010-05-27
> **webwiller said:**
> Hi all!
I need to convert an .mkv movie to an .avi, which is the converter for linux you suggest?

Does it need to be avi, or can you live with an mp4? If so, you can extract the tracks out of the mkv file without transcoding, thus it's much much faster. First you need some tools installed, mkvtoolnix and MP4Box

```
sudo apt-get install mkvtoolnix
```
```
sudo apt-get install MP4Box
``` -- that's a capital B

Now this process seems long, but once you do it a few times, it's pretty easy. All these commands are issues via the terminal, aka command line;

First you need to see what tracks are in the mkv container:

```
mkvinfo NameOfMkvfile.mkv
```

This will give you a list of the tracks; one will be an audio track and the other a video track -- there might be a subtitle track too. Once you have that you need to use mkvextract to remove each track. FYI, take note of the fps of the video track, you'll need it later.

```
mkvextract tracks NameOfMkvfile.mkv 1:audio.ac3 2:video.h264 
```

That process should take a couple of minutes to complete. Now all you need to do is use MP4Box to put them back together in an mp4 container. 

```
MP4Box -fps 23.976 -add video.h264 -add audio.ac3 NewFile.mp4
```

Now that will combine the audio and video tracks back together into an mp4 container. If you're using a PS3, they will play without issue. 

One note, the extensions of the video and the audio files need to be the codec of the original, which is shown in mkvinfo

Good Luck,
Bill

---

### Post by 311005901 on 2010-05-27
I would suggest installing a program called "Handbrake".
Click [here]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots") to go to the PPA page.

---

### Post by MrWES on 2010-05-27
Didn't Handbrake drop support for avi?

---

### Post by linuxman94 on 2010-05-27
> **philinux said:**
> Please try the forum search.

[http://ubuntuforums.org/search.php?searchid=73379907](http://ubuntuforums.org/search.php?searchid=73379907)

Your link returns no results.

---

### Post by ron999 on 2010-05-27
> **MrWES said:**
> Didn't Handbrake drop support for avi?
Yes it did.

---


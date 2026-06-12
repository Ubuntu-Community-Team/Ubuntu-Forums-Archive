---
title: "Your GStreamer installation is missing a plug-in"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-10
i'm trying to run DVDs on my Ubuntu 8.10 and i get this when opening a DVD with Movie Player -

Your GStreamer installation is missing a plug-in

how do i fix this? I want to be able to play these type of formats on my Movie Player and Rythmbox Music Player

.avi (all or most types if possible)
.mp4
.mp3
.acc
.wmv
.wma
.vob
.ogg
.rm
and other popular formats

---

### Post by wfp on 2008-12-10
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2
 
That's for dvd playback ^

Then just go to application on your panel and add%remove then make sure you have all available applications ticked and do a search for gstreamer you will see everything there you need.

---

### Post by wfp on 2008-12-10
> **wfp said:**
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2
 
That's for dvd playback ^

Then just go to application on your panel and add%remove then make sure you have all available applications ticked and do a search for gstreamer you will see everything there you need.

sorry should have read your post better your on intrepid just change that top line that has hardy.list and replace it with intrepid.list

---

### Post by philinux on 2008-12-10
Read this.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Click the medibuntu link below for their info.

---

### Post by manuleka on 2008-12-10
> **wfp said:**
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2
 
That's for dvd playback ^

Then just go to application on your panel and add%remove then make sure you have all available applications ticked and do a search for gstreamer you will see everything there you need.

i don't get the last paragraph... go to application?? you mean the Movie Player? can you rephrase the last paragraph to be abit simpler

cheers for your help

---

### Post by wfp on 2008-12-11
> **philinux said:**
> Read this.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Click the medibuntu link below for their info.

Just follow that link he provided. the add%remove i was referring to should be on your panel applications- places- system. click on applications, and on the bottom you should have add%remove open that up. Now you should have add/remove applications open. Now up at the top where it says show make sure you have all available applications ticked. Now do a search for gstreamer and you should see a whole list of codecs you can download and install. sorry for the late reply just getting home from work.

---

### Post by manuleka on 2008-12-11
thanks guys i fixed it :) thanks all for your help

---

### Post by nefarion_the_engineer on 2009-11-10
I've been trying to get Rhythmbox to play music (mp3, aac, m4a and whatever else I may have in my huge music library) and it just wont do it. Movies work on Movie Player because I downloaded ubuntu-restricted-extras. Both the audio and video work for movies now. What I have followed this thread and done the following.

-Go to Applications-Ubuntu Software Center-Installed Software. This shows all the software (I think) and in the search bar at the top right typed in Gstreamer. It shows I have the following installed already:
-- Movie Player
-- Multimedia Systems Selector
-- GStreamer Extra Plugins (codex to play mp3, sid, mpeg1,, mpeg2, ac-3, DVD)
-- GStreamer ffmpeg video plugin (codex to play mpex, divx, mpeg4, ac3, wmv and asf) 
-- GStreamer plugins for mms, wavpac, quicktime, musepac
-- GStreamer plugins for aac, xvid, mpeg2, faad

I'm running dual boot with Ubuntu 9.10. My music files were/ are used through itunes in windows xp. I have tried playing actual CD's and that works, but nothing from the harddrive will play in Rhythmbox. I also have an external harddrive with all the music on it and it wont play from that either. Do I need more codex? I'm new to linux, please help. Thanks

---


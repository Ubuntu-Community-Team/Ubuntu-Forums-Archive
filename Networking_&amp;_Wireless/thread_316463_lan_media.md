---
title: "lan media"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by fushorts on 2006-12-10
hello

i am using ubuntu 6.10 on two computers.  i have one of them based as a file server basically.  i can connect to the the folders i want to see but i would like to be able to listen to and watch the media that is on them without having to download it to my computer. is this possible?

error could not read from resource

the computer holding the files has 3 hard drives.  one with the OS on it   and to other two i have been using for media storage when i was using windows with them.  it will not let me change any permissions as well if that is part of the same problem then great.

any help would be greatly appreciated.

---

### Post by odinfromvalhalla on 2006-12-11
give VLC a try. [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by spd106 on 2006-12-11
I like to use daap sharing through rhythmbox to listen to my ogg vorbis collection stored on my desktop from my laptop over the WLAN. Just like on a Mac, only without iTunes.

Avahi Rocks!

---

### Post by Sten3danny on 2006-12-11
I'm having the same problems as the OP, except my media server is a Windows box.

I can browse through all the shared folders from my desktop(Ubuntu 6.10), but trying to play media files brings up the same error box.
Also thumbnails do not display.

---

### Post by fushorts on 2006-12-11
tried vlc

i may have done something wrong but still does not play music or video through the network.  

i would like to find a way to just click on the file and have it play.

any other suggestions?

i will admit i am not the best linux user around so if there is a setting i am missing that anyone thinks will work please let me know.

---

### Post by fushorts on 2006-12-13
is this just possible or is it something no one really knows.

---

### Post by spd106 on 2006-12-14
I'm not sure about video streaming as i've never tried it, but audio streaming is very easy with Rhythmbox.
Make sure you have Avahi installed and service discovery enabled in network settings on both PCs. Then just allow sharing in the Rythmbox's preferences menu. When you start up rhythmbox on client pc it should automatically discover the share, just like in iTunes on Apple Macs.

On windows you could use the tangerine daap server from [http://www.snorp.net/log/tangerine](http://www.snorp.net/log/tangerine) or iTunes + bonjour for windows, if you only need to stream MP3s.

I think you can also use vlc as a server, but i've only used it in client mode.

---

### Post by sivnik on 2006-12-15
i have the same problem. I try with vlc but it still is not working...
are there any special settings i have to do?

---


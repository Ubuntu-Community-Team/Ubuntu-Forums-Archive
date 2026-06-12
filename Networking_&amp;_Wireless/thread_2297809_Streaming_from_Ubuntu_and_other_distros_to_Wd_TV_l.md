---
title: "Streaming from Ubuntu and other distros to Wd TV live player via Samba problem"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by David_Rogers on 2015-10-06
Hi All

I hope someone will be kind enough to help me solve a Samba sharing problem

Here's the set-up. I've got 3 WD tv live boxes. That type can of box can stream audio from all sorts of places. I've also got a Windows 7 pc and all 3 WD boxes and the Windows pc are on  home network (wired) along with a Linux pc

The problem is, the Linux pc has several shared hard discs in it, containing lots of video files. On the Linux box I've tried Ubuntu, Ubuntu Studio and Linux Mint (latest version of each)

I can set up Samba and all 3 live boxes see the shared files, as does the Windows pc

But when I try and play a video file, whatever WD box is playing the file freezes up, leaving a still picture on the screen of the video file after about 20 to 30 minutes and the WD box needs re-starting to make it work again

The Windows pc plays the files perfectly

Having tried 3 different versions of Linux, i figured it must be the WD boxes, so I put Windows 7, then Windows 10 as full clean installs on the Linux box. The video files discs are formatted EXT4 so I added a free programme that gives read access to EXT4 files in Windows

The EXT4 drives show as read only in Windows 7 and 10 and if I share those drives, the 3 WD boxes all see the drive and play the video files without any problems

It's as if Samba is doing something after a period of time causing the WD boxes to crash

Does anyone have any ideas ?

---

### Post by TheFu on 2015-10-07
No  idea. I used CIFS from Linux for a few years with a WD TV Live-HD box here (stock firmware) - until the lack of format support made me switch to  Kodi running on a Raspberry-Pi connecting to a Plex Media Server. You could setup Plex and try using DLNA from the WD devices. That should work, though my WD box is retired. It worked great with wired ethernet,  but not very good using a Wifi dongle. wifi connections are always flaky.

BTW, there have been samba-kernel issues. I got hit after an update over the weekend. For streaming, using a streaming protocol is much better than file sharing IMHO.  

Might help if you searched for samba issues related to the current kernel being run. 3.13 had an issue.

---


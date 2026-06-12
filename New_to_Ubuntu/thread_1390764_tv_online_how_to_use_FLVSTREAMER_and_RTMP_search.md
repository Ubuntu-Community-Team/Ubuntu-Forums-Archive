---
title: "tv online: how to use FLVSTREAMER and RTMP search"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-26
Hello,

To record rtmp:// flash video .flv stream from embedded Adobe Flash Player may use the following RTMP Flash stream rippers:
**FLVSTREAMER** with **Wireshark** and netstat -plane can give the address of the host to play RTMP / Flash movies.
Is there anyone that knows how it works ? There is no Wiki under Ubuntu.



But one does not know any URL Finders that can reveal RTMPE URLs.
There has been 2 ways of finding RTMPE URLs:
   1. analyzing HTML, XML and other files used by the web-site
   2. getting it from the memory dump of your browser with a debugger

  

**Method: 2. getting it from the memory dump of your browser with a debugger**
Step 1. Use PMDump to dump your browser memory to your hard disk when you are watching the video you want to rip (you can pause it to avoid the lag)
Step 2. Use a hex editor to open the memory dump file,I use HxD Editor,its free and portable
Step 3. Press Ctrl + F to search keywords such as "rtmpe://" "mp4:" "stream start" "connect to",there you can find the url you want
rtmpdump 1.9 can successfully download the videos I couldn't download before
example: 
> rtmpdump -r "rtmpe://fms-edge02.omroep.nl/3v12/MP4:41944313.mp4" -o output.flv --resume
but it is important to get the --host address where RTMP can be replaced by URL in the flvstreamer command.
or with using : 
   gnash   to play the flasmplayer myfile.flv

If you would like to use rtmpdump, first apt-get remove flvstreamer, then dpkg -i rtmpdump_1.9a-0.0_i386.deb
 [http://debian-multimedia.org/pool/main/r/rtmpdump/rtmpdump_1.9a-0.0_i386.deb](http://debian-multimedia.org/pool/main/r/rtmpdump/rtmpdump_1.9a-0.0_i386.deb)

[B]
So under Ubuntu one can run: [/B]
> sudo cat /proc/kcore | strings | awk 'length > 20' | grep rtmp  | grep -o 'rtmp:[^"]*'   |  grep ".mp4"
 to get the rtmp stream


**Then use the flash player or flvstreamer**
not swfdec is buggy, and cannot play all. 

 
  
**You can test your streaming skills there:**
[http://flowplayer.org/plugins/streaming/rtmp.html](http://flowplayer.org/plugins/streaming/rtmp.html)

example 2: 
Here a wireshark example:
[http://www.youtube.com/watch?v=hNe70CbTlng](http://www.youtube.com/watch?v=hNe70CbTlng)

example 3: how to get the youtube flv, with wireshark : [http://www.youtube.com/watch?v=5miqHkco7rU&feature=related](http://www.youtube.com/watch?v=5miqHkco7rU&feature=related)

For those of you that don't know, rtmpdump is a utility used by
get_iplayer to download the flash video from the iplayer site, letting
you get access to high quality drm free tv. Apple recently issued a DMCA
takedown notice to the sourceforge site it was hosted on, they claimed
it could be used to infringe on copyright. I claim, it can't anymore
than firefox. 


Once you got the FLV file to watch the video: 
just do:

> mplayer myfile.flv

Please contribute to this thread, if it is possible to make it GNU and all right for LINUX
--

If you really cant do it with command line and mplayer, use the downloading plugin for firefox: [http://www.downloadhelper.net/tutorial.php?id=nfkFO9_SwIo](http://www.downloadhelper.net/tutorial.php?id=nfkFO9_SwIo)

---

### Post by highlandsun on 2010-04-18
On Linux systems you can just use rtmpsrv or rtmpsuck instead of manually snooping for stream info.

[http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/)

If you have more questions about how to use these programs, post them to the rtmpdump mailing list.

---


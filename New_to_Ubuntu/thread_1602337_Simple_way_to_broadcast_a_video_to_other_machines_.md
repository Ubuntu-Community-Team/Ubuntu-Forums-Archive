---
title: "Simple way to broadcast a video to other machines on my lan?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-10-21
What's the simplest way for me to broadcast a video from my Ubuntu box, to other computers on my lan?

Ideally I'd like the video to play on my server, and while playing, I can go on my other machines and go "Open Stream" and say something like, play the video that's playing on 192.168.1.1 or something like that.

What's the easiest way to accomplish this? Thank you.

---

### Post by Zzl1xndd on 2010-10-21
I believe the VIdeoLan server will let you do this. I have never set it up my self, but it looks like it will do the job.

[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

---

### Post by ivarn on 2010-10-21
well, you can either use webcam studio which allows you to add videos and play them as a webcam. or you can use use a website like ustream, livestream or justin.tv.
You don't really have to set up a whole server just to stream a video.
But it depends on what the purpose are.
An other method is to add your video to webcam studio and use camstream (both in synaptic) as a server. Then webcam studio will be the input device as a webcam.

---

### Post by papuccino1 on 2010-10-21
No, I need to broadcast video similar to Windows Server 2003 media broadcasting capabilities. I don't want something global, this is for a local intranet.

VLC says it does the job, but so far I can't get it to work even after following this tutorial to the letter.

[http://grok.lsu.edu/Article.aspx?articleId=14625](http://grok.lsu.edu/Article.aspx?articleId=14625)

---

### Post by ivarn on 2010-10-21
Oh ok, then try mythtv.

---

### Post by SeijiSensei on 2010-10-21
Looks like that tutorial assumes VLC is running on Windows.  In step 3 it tells you to select "Direct Show" for video capture.  That's a Microsoft technology.  What options appear in that drop-down box when you run it in Linux? My VLC (1.1.4-1ubuntu1 on Maverick 10.10) defaults to "Video for Linux 2".  How about if you choose "Desktop" instead, then display the video full-screen in VLC on the local machine?  Does that work?
 
Is it mandatory that all the clients view the video at the identical same time?  If not, you could simply place the file somewhere on the network where they can all open it with a video player.  If you want to reduce possible contention issues, copy the file to /dev/shm so it resides entirely in memory and distribute it from there.  

I just wonder if it's worth the effort to get [multicasting]("http://en.wikipedia.org/wiki/IP_multicast") running versus just letting each person view a separately-downloaded copy from a common internal web server.

Documentation of streaming in VLC looks pretty sparse. There's an "[old]("http://wiki.videolan.org/Documentation:Streaming_HowTo/")" HOWTO that's somewhat extensive and a "[new]("http://wiki.videolan.org/Documentation:Streaming_HowTo_New")" HOWTO that doesn't have much in it.

---


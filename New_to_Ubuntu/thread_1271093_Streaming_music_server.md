---
title: "Streaming music server?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-09-20
I'm interested in turning my home server into a streaming music server, but I can't figure out how. I found this howto: [http://ubuntuforums.org/showthread.php?t=34359](http://ubuntuforums.org/showthread.php?t=34359), but it didn't work for me (I got some weird error from Apache). I'd like to find something newer and simpler than what's in that howto. Does anyone have any ideas?

Thank you!

---

### Post by halitech on 2009-09-20
Depends on how you want to stream the music but I've used Edna in the past

[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

basically it serves a playlist and you can select what you want to play.

---

### Post by doctorbighands on 2009-09-20
I don't know about using playlists...I don't think I want to be limited by .m3u files.

---

### Post by ubersolid on 2009-09-20
tried mt-daapd? also known as firefly, you get a "iTunes stream" with that that Amarok, rhythmbox and banshee all can see. Been using that one for a long time.

---

### Post by Conzo on 2009-09-20
> **doctorbighands said:**
> I don't know about using playlists...I don't think I want to be limited by .m3u files.
 
 
Well i use XBMC and map out the files i want it to have access too ( Storage Server)  ...( video ,Pictures music ...) it has a upnp settings that can be used for PS3,Xbox And to itself via Client mode ....
 
 
 
Hope this Works for you ( Plus its 64 bit unlike Boxee! )
 
 
Conzo

---

### Post by doctorbighands on 2009-09-20
> **ubersolid said:**
> tried mt-daapd? also known as firefly, you get a "iTunes stream" with that that Amarok, rhythmbox and banshee all can see. Been using that one for a long time.

I have the tarball downloaded and extracted on my server, but I don't know how to install it. The site's FAQ is down right now. Any help??

---

### Post by halitech on 2009-09-20
> **doctorbighands said:**
> I don't know about using playlists...I don't think I want to be limited by .m3u files.

you aren't limited to .m3u files, it shows every file in the directory that you add to it. You can play all the files with an m3u or you can select individual songs on the fly. You can add more then one directory as well if you want.

---

### Post by doctorbighands on 2009-09-20
> **halitech said:**
> you aren't limited to .m3u files, it shows every file in the directory that you add to it. You can play all the files with an m3u or you can select individual songs on the fly. You can add more then one directory as well if you want.

Okay, so, I decided to try edna. I think it's running (I left the port as 8080, because I didn't know what else it should be). I don't know how to access my music server from another computer! There's no explanation on the edna website. Any help??

---

### Post by halitech on 2009-09-20
you would open a web browser and go to [http://ipaddressofserver:8080](http://ipaddressofserver:8080)

If you want to access it from outside your local network, you would need to forward port 8080 in your router (if you have one) and use the external IP address or you can get a static hostname from someplace like dynu.com

---

### Post by doctorbighands on 2009-09-20
Nevermind. I figured it out!

Thank you, Halitech, for your help!!

---

### Post by MrWES on 2009-09-20
> **ubersolid said:**
> tried mt-daapd? also known as firefly, you get a "iTunes stream" with that that Amarok, rhythmbox and banshee all can see. Been using that one for a long time.
+1 for mt-daapd -- same here been using it for a long time. Works great. Also, Windows boxs can also see it via iTunes.

Bill

---


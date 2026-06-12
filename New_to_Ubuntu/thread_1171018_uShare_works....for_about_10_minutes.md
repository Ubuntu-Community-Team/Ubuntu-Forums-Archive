---
title: "uShare works....for about 10 minutes"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Coolsaber57 on 2009-05-26
Hi guys,

I have uShare working (connecting to my xbox 360 for video sharing) but the problem is that it stops working after about 10 minutes and the xbox says something about a lost connection.

What's the deal? I changed my power settings to make sure it doens't do anything when it is idle/closing the lid/etc. but it still does the same thing.

Has anyone run into this before and how did you fix it?
Thanks!

---

### Post by rsambuca on 2009-05-26
Check to make sure that you have set static IP addresses for the XBox and your PC.  Sometimes they keep stealing the same IP address if you leave them as dynamic IP's.

---

### Post by Coolsaber57 on 2009-05-27
> **rsambuca said:**
> Check to make sure that you have set static IP addresses for the XBox and your PC.  Sometimes they keep stealing the same IP address if you leave them as dynamic IP's.

I don't understand why that would make uShare all of the sudden stop sharing in the middle of a movie.

My xbox definitely has a static IP, but my laptop currently doesn't.  I'll change that first, but are there any other ideas?

---

### Post by rsambuca on 2009-05-28
It can make ushare stop working because the IP address of one of the machines is lost.  No other ideas immediately come to mind.

---

### Post by Baelus on 2009-05-28
Is the laptop connected via ethernet cable or wireless?

Is a router involved or is it a direct connection between the laptop and the 360?

---

### Post by GroundNpound on 2009-06-27
I have an external hard drive with all my vids.  It's one of those MyBook usb external HDs with 1TB space.  It's about half full, but I found out that ushare or the linux network doesn't like the external HD's if they contain lots of data.  I moved the vids over to a 1.5 TB internal HD and now I have no problems.  With the external HD I noticed chopy playback, with the internal HD, all is well.  My network is wireless-N and my computer is up stairs around a corner and through a hallway... I've even tried streaming a high definition film through ushare... flawless.

---

### Post by Coolsaber57 on 2009-07-05
> **Baelus said:**
> Is the laptop connected via ethernet cable or wireless?

Is a router involved or is it a direct connection between the laptop and the 360?

I'm going through a Netgear router using a wireless connection.  It plays fine for a few minutes, then just drops out.

---

### Post by ardensdrunk on 2010-03-14
mine does the same except i'm using two linksys routers (setup as a wireless bridge)

windows has NO problems streaming to the xbox, however ushare seems to be a bit finicky

will work GREAT for about 20 mins or so and then the connection just drops ..
the xbox will lose the share and wont be able to find it until reboot the machine 

then it works again for another 20 mins...

something is stopping or "sleeping" after a certain amount of time and its killing the ushare connection ...

ubuntu 9.10

---

### Post by jpuddy on 2010-03-30
For the record, I have the exact same problem, but it's limited to media stored on my external hard drive. Let me detail:

I have a server running CentOS (not Ubuntu, sorry), which runs uShare, that I access via my Xbox 360. The Xbox 360 is connected via a Buffalo router that was turned into a bridge, using Tomato firmware. The wireless network is on some Netgear N router. Media sharing and movie playback works flawlessly, provided that I am playing media stored on the hard drives within the server. I also have an external drive attached via USB, but when I play media from this source, it stops playing after 5 or 10 minutes. So far, I'm stumped.

---

### Post by darthvader109 on 2010-04-10
Same here.  I tried to watch a movie from my linux box (ubuntu 9.10) on my xbox 360 and it kept freezing up.  Then it wouldn't connect.  This kept happening over and over - no idea why.

I finally switched over to sharing from my mac (using a program called Connect360) and streaming worked.  Are there alternatives to ushare?  Or is this just an ubuntu thing?

---

### Post by jpuddy on 2010-04-11
I've been playing around with things some more, and the problem for me now is not actually external storage, it's just some codecs. It's odd, I can play anything on a USB key just fine... but pretty much anything I rip using Handbrake will not play via uShare. It'll stop after 5 or 10 minutes. The vast majority of the xvid and other files I grab off the net play just fine though.

Peculiar...

---

### Post by JayMan8081 on 2010-04-27
Hmm, I'm running into the same situation. I have a bunch of rips that I made using the 264 encoder in Handbrake and ushare freezes after about 5 or 10 minutes as well. The xbox reports that the connection was lost and I have to manually kill the process on my ubuntu machine. Seems that no one has solved this yet?

---

### Post by santiagozky on 2010-05-25
Same problem here. it also works for about 10~|5 minutes and then freezes. I even have to kill -9 since ctr-c won't work. When I was using 9.10 it was working great but now with 10.04 the problem started.

I suppose this is some kind of xbox specific bug?

---

### Post by nhasian on 2010-05-25
uShare works great.  until it doesn't.  I got fed up with it and switched to [PS3MediaServer]("http://code.google.com/p/ps3mediaserver/").  couldn't be happier now.  yes it works with xbox360 too.  Actually i used it to stream videos directly to my Samsung UNB8000 LED backlit LCD TV.  I don't have a console gaming system at all.

---

### Post by jazzersaxman on 2010-05-26
This sounds great!  I will try this option before I pull my hair out.  I have a WD 1.5 TB external drive and having ushare issues too.  It seems that ushare and the xbox see each other, but I can't have it see the external drive.  so, I'll try the ps3mediaserver...


UPDATE --- I have NOOO idea how to install it from the download, and the directions for installation are non existent.  Any advice?

---

### Post by ryokea on 2010-05-27
Download the tar and unzip then make the file PMS.sh executable and run it. Should open a GUI from there so you can configure everything.

---

### Post by Stigmata13 on 2010-08-21
Just a helpful tip, instead of starting ushare by typing:
```
sudo ushare
```
or
```
sudo ushare -x
```
Try starting it using this method:
```
sudo /etc/init.d/ushare start
```
I've found it's much more reliable, and if you need to stop it, instead of opening a seperate terminal window and killing it, all you have to do is type:
```
sudo /etc/init.d/ushare stop
```
In the same terminal window.

As for the original topic, I've experienced this too... although not to the same degree. Most of the time it will play fine for hours, but there are the occasional times where it does stop after around 10 minutes. My guess it's a bug in Ushare, but I don't know.

---


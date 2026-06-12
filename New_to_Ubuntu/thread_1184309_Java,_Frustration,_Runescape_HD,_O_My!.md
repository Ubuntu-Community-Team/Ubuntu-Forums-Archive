---
title: "Java, Frustration, Runescape HD, O My!"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by R.H.H on 2009-06-11
Hello again people. This will probably make you laugh but I've cleared my hard drive and downloaded ubuntu 3 times today. Why? Well I just got ubuntu and all my files are backed up on a hard drive so I don't care what happens to these files so... Whenever I have the slightest problem I pop in my CD and reinstall!

But, to the point. I have followed the advice about Java from Mr. Chilli Bob in my past thread. Past Thread: [(http://ubuntuforums.org/showthread.php?t=1183392)]("http://ubuntuforums.org/showthread.php?t=1183392") 

O and here is the link to Mr. Chilli Bob's advice: 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This is great! I'm not sure how I did it but I guess Java is installed and so is flash player. Yay. But!! Alas to my dismay when I tried to use Java to play my stupid RuneScape game in high detail, it says "blah blah blah blash blahss.. your stuff don't work kid". Strangely enought it loads perfectly in standard detail. Standard detail is for noobs so, it would be great if you guys could help me out thank you very much.

This is also another important fact one of those three times I reinstalled, I had already installed Mr. Chilli Bob's stuff. So, if you think there is a better way for me to get all of my Java and Adobe running with RuneScape please don't be afraid to chip in.

Thank everyone very much, me.

---

### Post by Dr Belka on 2009-06-11
More detail would enable us to help you with more accuracy...  


have you tried this?

```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```


as for the flash player, maybe this will help you.

[http://tapos.wordpress.com/2008/02/13/installing-adobe-flash-player-in-ubuntu/](http://tapos.wordpress.com/2008/02/13/installing-adobe-flash-player-in-ubuntu/)

If all else fails, maybe you should install firefox 3.5 beta and try runescape on that.  When I was setting my little brother's linux computer set up to play runescape, this is what did it for me.  BTW, If you need an autoclicker....

```
sudo aptitude install kautoclick
```

---

### Post by R.H.H on 2009-06-11
I'll try the new firefox. The problem is that I can't get runescape hd to load. standard detail will load fine.

---

### Post by CJ Master on 2009-06-13
Will other java applications work in fullscreen?

---

### Post by Azuu on 2009-06-18
From the looks of it, this is not a java specific problem:

[http://forum.runescape.com/forums.ws?25,26,774,58983688](http://forum.runescape.com/forums.ws?25,26,774,58983688)

excerpt for CJ Master:
"Makoto D

	
16-Jun-2009 11:10:52
Thank you, very, very much for the heads-up, Mod Noldor.

I've been tracking this bug since late April, and while I don't have Ubuntu Jaunty or Xserver 1.7 on the machine that plays RS, my laptop can serve as a sufficient test-bed.

Allow me to contribute in any way possible.

I've noticed that other Java-games (a-la Funorb) when played in fullscreen do not suffer the same symptoms as RuneScape, which led me to doubt that it was a Linux issue to begin with. However, this regression is inconsistent across distributions (I'm able to play HD on Ubuntu 8.10 comfortably), so I have the feeling that it's related to X or mesa somehow.

I wish your tech team the best of luck in finding and killing this bug. I'd like to update to Jaunty soon...don't want to wait until October to upgrade my OS. "

The open source drivers might work better, try those and see.

---

### Post by MakotoTheKnight on 2009-06-27
> **Azuu said:**
> From the looks of it, this is not a java specific problem:

[http://forum.runescape.com/forums.ws?25,26,774,58983688](http://forum.runescape.com/forums.ws?25,26,774,58983688)

excerpt for CJ Master:
"Makoto D

	
16-Jun-2009 11:10:52
Thank you, very, very much for the heads-up, Mod Noldor.

I've been tracking this bug since late April, and while I don't have Ubuntu Jaunty or Xserver 1.7 on the machine that plays RS, my laptop can serve as a sufficient test-bed.

Allow me to contribute in any way possible.

I've noticed that other Java-games (a-la Funorb) when played in fullscreen do not suffer the same symptoms as RuneScape, which led me to doubt that it was a Linux issue to begin with. However, this regression is inconsistent across distributions (I'm able to play HD on Ubuntu 8.10 comfortably), so I have the feeling that it's related to X or mesa somehow.

I wish your tech team the best of luck in finding and killing this bug. I'd like to update to Jaunty soon...don't want to wait until October to upgrade my OS. "

The open source drivers might work better, try those and see.

When I made that post, I knew that the open source drivers wouldn't cut it - there's no 3D acceleration available with them.  If glxgears won't run, then there's no way that a JOGL applet will run.

Honestly though it might be both party's fault.  It could be some Java, and it could definitely be some X/Mesa.  All I know is that it's working just dandy in Intrepid, and that's all that matters right now.

---

### Post by The Cog on 2009-06-27
My son has the same problem. Works HD fine in Intrepid, crashes in Jaunty. This using the nVidia drivers supplied from the repositories.

---


---
title: "I've heard good things about wicd, but..."
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by boomtisk on 2008-01-20
Hi, everyone, I'm getting frequent disconnects when using nm-applet to take care of my laptop's wireless connection, so I thought I'd try something else. I've read good things about wicd so I installed that using the instructions on their site which involve adding the  [http://apt.wicd.net](http://apt.wicd.net) repository and stuff.

I use a PCMCIA wireless card and Xubuntu Gutsy on an old-ish IBM ThinkPad.

lspci | grep -i net spits out the following:

```
06:00.0 RaLink RT2561/RT61 806.11g PCI
```

Strangely enough, once I installed wicd, the OS stopped communicating with my wireless card and its "Link" LED shut off. When trying to start wicd, the program froze, obviously trying to communicate with my wireless card. This seems pretty weird to me as I read wicd doesn't contain any drivers and is supposed to communicate with the OS's inbuilt wireless drivers.

Once I took my wireless card out and put in the "wired" PCMIA network card I had lying around, wicd miraculously started coming to life! The only way to resurrect my wireless card was uninstalling wicd and bringing back network-manager.

What do you guys think of this? Any suggestions as to how I could get wicd to work with my wireless card? Thanks a lot in advance.

---

### Post by boomtisk on 2008-01-20
Let's try a slight bump.

---

### Post by imdano on 2008-01-20
I would suggest not using the version of wicd in the apt repository, it's pretty old and buggy compared to the newest release.  You can download a newer release here: [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

---

### Post by boomtisk on 2008-02-03
Thanks for the suggestion but I already tried the latest version and the problem persisted. Funnily enough, wicd works on the PC I got for my parents (it has a PCI wireless card which seems to use the same chipset as my laptop's PCMCIA card) and seems to perform better than Network Manager on it. Well, back to the drawing board, I guess.

---

### Post by boomtisk on 2008-02-19
Okay, I discovered something weird. 

lshw -C network

tells me my PCMCIA card's "logical name" is **wmaster0**.

Once I'm connected to the Net via network manager, 

iwlist scan

tells me the interface that's connected to the net is **wlan0** and wmaster0 "doesn't support scanning"!

I'm not sure how this happened but could it be that this is causing wicd to freak out?

---

### Post by boomtisk on 2008-02-19
Let's try another bump.

---

### Post by rustybronco on 2008-02-19
Thanks for the pleasant bumps, much appreciated :)   sorry you had to wait so long.

I believe it to be a driver issue with the frequent disconnects.
Personally I would give a go to  this thread by substituting the rt73 with rt61.
[http://ubuntuforums.org/showthread.php?p=2395871#post2395871](http://ubuntuforums.org/showthread.php?p=2395871#post2395871)

or if you feel like living on the edge and don't mind the re-install....
[http://ubuntuforums.org/showthread.php?p=3993033#post3993033](http://ubuntuforums.org/showthread.php?p=3993033#post3993033)

> **boomtisk said:**
> Okay, I discovered something weird. 

lshw -C network

tells me my PCMCIA card's "logical name" is **wmaster0**.

Once I'm connected to the Net via network manager, 

iwlist scan

tells me the interface that's connected to the net is **wlan0** and wmaster0 "doesn't support scanning"!

I'm not sure how this happened but could it be that this is causing wicd to freak out?
[http://ubuntuforums.org/showpost.php?p=4338334&postcount=2](http://ubuntuforums.org/showpost.php?p=4338334&postcount=2)

---

### Post by Whiffle on 2008-02-19
When you start the WICD program, you're really just starting the gui.  Make sure the wicd daemon is running

sudo /etc/init.d/wicd start

Then try the wicd gui.  You might have to change the interface name to whatever is listed in iwconfig.  If its not listed in iwconfig, you need to check your drivers.

---

### Post by boomtisk on 2008-02-20
Thanks for the advice, guys. I actually compiled the rt61 from the serialmonkey website a while ago and apparently it didn't work -- the "link" LED on my wireless card went dim after installing it while the "activity" LED was still blinking happily. I couldn't connect to the net, though.  o_O

Also, I'm positive the daemon had no problems loading as wicd managed to cooperate with my spare PCMIA card with a network cable socket for ordinary wired connections without any problems.

I guess I'll be sticking with Network Manager for now, it seems to be working okay lately as long as I don't try demanding stuff such as listening to Internet radio and things like that.

---

### Post by rustybronco on 2008-02-20
When you compiled the rt61 drivers did you use the daily cvs from serialmonkey.
if you didn't then you might want to give it a go again using the latest cvs files.

---

### Post by boomtisk on 2008-02-20
Yeah, I used the cvs one as the "normal" one wouldn't compile. I had to blacklist it to get things working again.

---

### Post by boomtisk on 2008-02-20
Super happy lucky update: I managed to get ndiswrapper working! I found the driver CD for my somewhat obscure and cheap PCMIA card which contained the driver installation as a standalone compressed .exe! The installation process wouldn't finish if I ran the .exe in wine so I had to boot into Windows. :-? Lastly, the recommended "use the Windows 98 driver" method didn't work for me, I had to use the Win XP driver to keep ndiswrapper from complaining. It seems to work great so far, though. Let's see if my troubles are solved now. :cool:

---


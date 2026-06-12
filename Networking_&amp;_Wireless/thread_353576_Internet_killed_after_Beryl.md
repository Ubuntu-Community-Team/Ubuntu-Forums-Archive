---
title: "Internet killed after Beryl"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by steveneddy on 2007-02-04
I received a new [Serval laptop from System76]("http://system76.com/index.php/cPath/1_12") Friday. Installing the new Beryl, I ran into a small problem with Beryl.

After installation, if Beryl Manager is put in the Sessions startup menu, it crashed my network connection from the laptop. I am on wireless on the laptop and i didn't test the wired connection. I can start Beryl Manager from the Applications menu and start Beryl with no problems. 

I deleted Beryl Manager from the Sessions startup menu and all problems solved. 

If someone needs me to test the wired connection also for the same problem, post here & I will get back to this post later with the results.

Ubuntu Edgy 6.10, fully updated, Beryl version 0.1.9999.1, wireless LAN connection, Network Manager 0.6.3 connection manager from Gnome, Intel 2 Ghz Core 2 Duo T7200, 2 Gig RAM, nVidia GeForce GO 7600.

I installed [Beryl from SVN ]("http://forum.beryl-project.org/viewtopic.php?f=43&t=51")off of the Beryl forums site. 

Why yes, this IS a sweet lappie. Thank you.

-SE

---

### Post by zeus77 on 2007-02-21
i report the exact same problem on a Lenovo 3000 N100 0768-A53 notebook.  It's got a Broadcom 4311 WLAN card, and I'm using ndiswrapper to get the wireless drivers to go.  Beryl and WLAN work fine if I load beryl-manager after Gnome has started up... but if beryl-manager is in Sessions/Startup, it kills my WLAN card.  

I've also tried [several other]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#Configuring_Beryl") suggested ways of starting beryl at boot without success...

It's kind of a pain to have to load beryl-manager manually each time.  Any ideas?

---

### Post by Waappu on 2007-02-21
Hi

Try if this kind startup script helps:

type in terminal:```
gksudo gedit /usr/local/bin/start-beryl.sh
```
type these lines to file and save
```
#!/bin/bash
killall beryl
killall emerald
sleep 30
beryl-manager
```
then add execute rights to file```
sudo chmod a+x /usr/local/bin/start-beryl.sh
```
and add this to startup programs```
start-beryl.sh
```Login to normal gnome session and script should start Beryl with 30sec delay giving time to other programs load first

---

### Post by SnowPunk98 on 2007-02-25
i also have the same problem on a Dell E7105 laptop, I will try that script later and see if it works.

---

### Post by Ek0nomik on 2007-02-28
My internet died the first time too.  I had to take it out of the startup.

I still can't even get Beryl to work though.  :/

---

### Post by steveneddy on 2007-03-02
I did get Beryl to work, but has to be started manually, after the wireless makes a connection. Other than that, it works great.

Looks great, also.

Thanks, SE

---


---
title: "Wireless not working"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by klato on 2005-08-25
I've done a bit of searching on the forums about this but I can't seem to find a solution.  I just downloaded the latest Ubuntu livecd iso, burned it, and booted into Ubuntu.  Everything seems fine (even my touchpad works and resolution is set to the max), although the wireless is the one thing that I can't get to work.

My card is a pcmcia Dell TrueMobile 1150 (which is supported according to the docs here)

I went into System->Administration->Networking and my card shows up as eth1. I went into its settings and put in my ESSID and WEP key, and hit DHCP (so far so good...this is what I do in XP).  Hit ok, and it sits there for a while saying "Activating...".  Wireless leds blink on...but when I try to load a webpage in firefox...no go.  

What am I doing wrong? (I also noticed that during boot, the "cardmgr" tries to do something, but it says "directory or file not found" or something similar.  Could this be causing a problem?)

Thanks

---

### Post by klato on 2005-08-25
Been reading some more and it seems that I have to use the "ndiswrapper".  I don't really have the time to screw around with mounting filesystems and writing scripts, so I guess that's the end of the line for me.  Anyway, I don't see much point in running an OS that depends on drivers from another OS...  :roll: 

I really would have liked a linux solution that works 100% out of the box but I guess that day has yet to come (and I've tried 5 or so distros over the past 8 years or so).

Oh well.

---

### Post by bionnaki on 2005-08-25
ndiswrapper isnt difficult to install...

the problem is the hardware, not linux.

---

### Post by s_p_a_r_k_y on 2005-08-25
dells are notorously bad with wireless and Linux. I had 2 friends with the same Dell model, but different wireless cards. One of them worked with linux out of the box, the other one I still can't get to work. If you have an eth1 it seems that it was recognized as I'm assuming eth0 should be your wired interface.

If that is the case see if you can see any networks by issuing the following command into your terminal

iwlist scan

if it finds some cells, then it should be working, its just a matter of setting the correct settings

sudo iwconfig eth1 ESSID YOUR_ESSID 

it should get the channel correctly. If you need wep, then 
sudo iwconfig eth1 ESSID YOUR_ESSID key open YOUR_KEY

the essid is case sensitive I believe so if you essid it netGeAr then thats how you should enter it

---

### Post by Lambert on 2005-08-25
Don't get to discouraged. I was at where you were a few weeks ago. I've tried 30 different distros if not more. ndiswrapper is not very difficult and in the upcoming release of breezy (due in october) wireless is even better supported. Your card might work out of the box (not sure of the specs but my atheros based card works)

[https://wiki.ubuntu.com/WiFiHardware](https://wiki.ubuntu.com/WiFiHardware)  - it's only a few commands and most trouble I've seen is easily resolved here in the forums. Give breezy a try when it's released.

---

### Post by jacalope on 2005-08-25
Just a quick thought, I could not get the Live cd to work with my card either. But when I installed Ubuntu on my hard drive, it worked "right out of the box". Klato, keep the faith, take the plunge, and you might be enjoying a dual boot OS puter that will make friends think that you are a godess!  :)  Which in fact, we linux users already know that you are.

---


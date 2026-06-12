---
title: "how to install ndiswrapper on the new xubuntu"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by mattrobinson999 on 2008-08-08
How do I install ndiswrapper on xubuntu hardy hereon?
I'm also not too sure what I need to download.
I have a wireless usb stick made by netgear, "WG111v2"

Any Help?
Thanks.

---

### Post by caljohnsmith on 2008-08-08
To install ndiswrapper, I would recommend going with the GUI:
```
sudo apt-get install ndisgtk
```
Also, what chipset does your USB wireless stick use? Try doing:
```
lsusb
```

---

### Post by omarabdelhaleem on 2008-08-08
Hey Caljohnsmith, 

I've formatted Xubuntu to an old Gateway M305 and have used Synaptic Package Manager to install ndiswrapper -- but unfortunately the wireless still isn't picked up.

Then I went to terminal to determine the chipset using the code you suggested. Here was the response: 

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 001: ID 0000:0000  

Any ideas on where to go from here? Thanks in advance. 

Omar

---

### Post by caljohnsmith on 2008-08-08
Hi Omar, 

Actually that lsusb command was for mattrobinson999 because he said he has a wireless USB stick. Do you have a wireless card or a wireless USB stick? I would assume you have a card since your lsusb didn't seem to return much of interest.

If you have a wireless PCI card, do the following command and post it back:
```
sudo lshw -C network
```

---

### Post by mattrobinson999 on 2008-08-10
Well thanks for the help, but now ive got an even bigger problem, linux told me it have a problem with terminal itself and asked me to re install xubuntu, i tried this with my live disk but every time i go to install it says that my hhd isnt working, it says "Error 5"

Any help?

---

### Post by caljohnsmith on 2008-08-10
Mattrobinson999, I probably can't help you, because it sounds like you may be experiencing a HDD failure. How old is your HDD? Do you have any other operating systems on that HDD (like Windows) that you can try and boot? Also, when you boot the Live CD, if you open up a terminal and do:
```
sudo fdisk -l
```
Does it show your HDD? It should be listed as /dev/hda or /dev/sda or similar.

---

### Post by mattrobinson999 on 2008-08-10
Yes, it displays /dev/hda from the live cd

I think the hhd is about 10 years old as it used to have windows 98 on it and runs successfully on a crack copy of xp.

In the past hour I have re-installed XP to see that works, and it did.

So is there anything in xp that i do to help this situation?

---

### Post by mattrobinson999 on 2008-08-10
Another small problem has occurred just now, the live disk I have for Xubuntu has stopped working, so I've switched to a Ubuntu live disk.

---

### Post by caljohnsmith on 2008-08-10
> **mattrobinson999 said:**
> I think the hhd is about 10 years old as it used to have windows 98 on it and runs successfully on a crack copy of xp.
As a rule of thumb, I've read that most HDDs are expected to last somewhere around 5 years, so being 10 years old raises a big, red flag. :wink: Do you have any diagonistic software that came with your HDD (on a CD)? I would definitely run that if you have it. Or you could download the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") which has lots of great HDD recovery utilities and HDD diagnostic software I think.

---

### Post by mattrobinson999 on 2008-08-10
thanks for your help.

and even better, ive found that i dont need to install ndiswrapper when it does work because the usb stick was recognised

---


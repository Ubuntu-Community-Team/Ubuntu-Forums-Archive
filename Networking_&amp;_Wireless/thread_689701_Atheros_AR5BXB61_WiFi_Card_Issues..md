---
title: "Atheros AR5BXB61 WiFi Card Issues."
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Mire3212 on 2008-02-06
So, i've got a fresh install of Ubuntu 6.06 LTS, Dapper. I'm running it on a Toshiba Satellite laptop. Everything so far seems to be working, I've got sound (which was an issue from 7.10), I can play video (another 7.10 issue) but I can't for the life of me get WiFi working. I've got it hooked up to harline LAN right now, but can't seem to get the card to reckonize in the network util. it is an Atheros AR5BXB61 card.

lshw -C network

*-network UNCLAIMED

description: Ethernet controller
product: Atheros Communications, Inc.
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@02:00.0
version: 01
width: 64 bits
clock: 33mhz
capabilities: cap_list
resources: iomemory:d0100000-d010ffff irq: 233
lspci

...
0000:02:00.0 Ethernet Controller: Atheros Communicatsion, Inc.: Unknow device 001c (rev 01)
...
lspci -n

...
0000:02:00.0 0200: 168c:001c (rev 01)
...
This is what i get when i run the above commands.... Anyone got any ideas why it can't recognize the card? I've followed the instructions here 

[https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

to attempt to get it to work, i did use the ndisgtk utility to try to get it to work. It will load the driver in the window, but then if i configure network configurations, it doesn't show up with a wireless card, just my built in ethernet card and modem card. 

I'd appreciate some help if anyone can. Thank you!

Mire3212

---

### Post by digitalhillbilly on 2008-02-06
have you tried in your console - 
```

$ ndiswrapper -l
```

what does it print?

---

### Post by Mire3212 on 2008-02-06
ndiswrapper -l

Installed ndis drivers:
net5211  driver present, hardware present


yet, it doesn't work with the wireless card. is it that this driver isn't for this chipset?

---

### Post by digitalhillbilly on 2008-02-06
that seems good. I have only to this point struggled through two wifi setups  and am now having issues with my third so any info from me is kinda like the blind leading the blind Since the device is loaded in ndiswrapper, I would now install wicd  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) . It will remove and replace network manager but will give you a nicer interface for managing your network connections.   Madwifi [http://madwifi.org/](http://madwifi.org/) might work well for you too. It made life easy for me on another machine.

Since your card is not showing up in the Network admin panel I would be concerned that it is not loading but try the two things above and see where your at.  Maybe someone more knowledgeable will add something.

dh

---

### Post by Mire3212 on 2008-02-06
i would try to do madwifi, but i don't know how to set it up.... i've tried reading the set up manual and just kind of get lost... it could be that i'm not trying very hard with mad wifi of course. any tips in setting it up would be helpful.

---

### Post by digitalhillbilly on 2008-02-06
First check "System -> Administration -> Restricted Drivers Manager" to see if it's already there and needs to be enabled. IIRC it was present on a computer I set up in the past.   Check here to see if it's there. If not, you would have to omile and install it. It's easier than it sounds. If it's there, make sure it's enabled. lemme know what you find.

dh

---

### Post by Mire3212 on 2008-02-06
I don't actually have the menu in my System > Admin > folder.... should it be somewhere on the machine already? This is a fresh Dapper install of 6.06

---

### Post by digitalhillbilly on 2008-02-06
ah... sry. The madwifi driver is included in Ubuntu starting with Feisty. guess you'll have to install.

I would love to help you build it but I'm really not experienced enough. instead, here are a couple links that have all the info you need:

compiling easy howto: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
more detailed compiling: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

madwifi first time howto: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

post here your progress and I'll help where ever i can.

dh

---

### Post by Mire3212 on 2008-02-06
I can't seem to get this to work right... it keeps erroring and saying

```

make

/bin/sh: line 0: cd; /lib/modules/2.6.15-51-386/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.15-51-386/build is missing, please set KERNALPATH.   Stop.


```

I don't know where the KERNELPATH is to be able to set it, so i don't know how to actually complete the make

---

### Post by digitalhillbilly on 2008-02-11
Hey Mire... Sry I haven't been around for a couple days. Make any progress?

---

### Post by Mire3212 on 2008-02-11
Eh, well.... i still can't get it to work. i even did a fresh install of the 6.06 LTS version and tried to reinstall both the 5211 atheros driver with ndiwrapper and the gui too... still doesn't work :(

---

### Post by digitalhillbilly on 2008-02-11
That sucks. Keep at it though... your card will work. Did you read the compiling howto and get madwifi built? If not, try again and keep track of the things you do. I've been struggling with a wifi card as well and it turns out the first thing I tried was the correct path, I just made a mistake in the process. I now have it working - well, mostly. lol!

dh

---

### Post by digitalhillbilly on 2008-02-11
btw... why are you using 6.06 rather than the newest 7.10?

dh

---

### Post by Mire3212 on 2008-02-11
7.10 doesn't work well with my machine. no sound and videos don't play correctly. the wi-fi card seems to be found in 7.10, but initially i also had issues connecting to my network. it always defaulted to 'linksys' but thats not my network. 6.06 works a lot better, in fact the only issue i have is the wifi card


Mire3212

---

### Post by digitalhillbilly on 2008-02-11
Do you recall what the sound and video issues were? Maybe it will be easier to get them going. What does lspci print out?

dh

---

### Post by Mire3212 on 2008-02-12
there was no audio whatsoever and the video didnt play. It was justna bunch of black lines and stuff. I don't have a printout right now. I'll check tomorrow

Mire3212

---


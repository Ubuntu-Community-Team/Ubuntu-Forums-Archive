---
title: "Just diving into Lunix, Having a few Wireless problems"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Orann on 2007-07-12
Well, I've just a few days ago bought and assembled my new computer, with an AMD Athlon 64 X2 Dual Core Processor on an AMD Asus M2N motherboard. I'm using a SATA hardrive and DVD/CD re-writable.
I decided, after having a look at vista, that I was going to try out Linux, something that I'd never tried before, and was interested in checking out.
So I installed Ubuntu (7.4, Feisty), and everything was looking good, until I ran into a difficult problem.

My internet is coming from a D-Link DI-824VUP+ AirPlus G+ wireless router, and My plan was to receive it via the DWL-120+ USB Adapter that came with the router package. Now, Unfortunately, all my efforts to get this to work haev gone in vain. I am unable to accesses the internet on my Ubuntu computer, rendering a lot of tutorials and guides available (Both forums based and in the help files0 pretty much useless. It said that NDISWrapper came packaged with the Ubuntu CD, but I was unable to find it on there, and I was prompted to connect to the internet to download it (Which is pretty circular and illogical when the guide is telling you how to connect to a wireless network, most probably used for internet...).

Anyway, I spent a good 2 days trying to install various different libraries to try and get NDISWrapper to work with the drivers packaged with the USB Adapter (Plugging it in initially, it was not recognized, so I thought that the drivers might help). Like I said, this has not really worked in the slightest. I managed to get  the following NdisWrapper installed:

Utils Version: 1.9
Driver version: 1.38

Having done this, I installed the graphical component to this to try and get it working with that. Unfortunately, this did not do anything. I added a new driver via the files I copied from the diver installation CD (that came with the USB Adapter). This comes up with an item on the list, that has an item, no title, and  the text: "Hardware Present: No".

I have also tried a Terminal installation, which has achieved just as little.

This failing, I installed wine (After making ~20 trips between an internet connected computer and the linux one to download various different libraries that I was under the impression were supposed to come installed with the OS.), and attempted to use this to install some of the drivers. This opened up the windows installer successfully and gave the impression that the drivers had been installed, however, they were not, and things are still the same.  


Quite simply, I am completely lost here, and could use some help and instructions on what to do to connect to the wireless network.

Even once that is done, I have no idea how I am going to go about installing graphics card drivers (Gigabyte  Nvidia 8600 series), Motherboard drivers, DvD Drive drivers, etc.

I have also tried to utilize ImageBurner that I installed using Wine to burn an image of Mandriva (that I transfered via USB) so I could try my luck on that, But Ubuntu has not recognised my DvD drive (Though, it can open CD'd that I use it for).

I'm completely new to all this, and I'm relatively determined to stay away from Windows as much as possible (though this whole issue has shaken my faith in Linux's ability to compete with Windows). Any help would be Greatly Appreciated.

---

### Post by drhavanger on 2007-07-12
i don't know much but i would follow [this link]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") which should lead you to [this link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"). from there you will want to find your model and what programs you will have to download.  i would use System->Administrantion->Synaptic Package Manager do a search for the recommended software and download and install that way.  much easier than finding the most current file and figuring out how to install it.  if that all works then you should see an icon the the upper right hand of your screen (by date and time) and will see your wireless and any other wireless networks in your area.  hope that helps

---

### Post by leedsdevil on 2007-07-12
well my friend i hope the best im still new to ubuntu and had the greatest luck for the most part keep on working at it. it sounds like u have one heck of a rig if you go back to windows dont go vista go xp.. i hate to saaay that i WAS a windows guy but had found a new home in ubuntu GOODLUCK:guitar:

---

### Post by kevdog on 2007-07-12
Ok lets just check out your system before recommending a course of action

In command terminal, type and cut and paste the result of:

If using PCI based wireless
lspci
lspci -n

If using USB based wireless
lsusb

lshw -C network

ndiswraper -v
ndiswrapper -l

That should give us a start!

---

### Post by Orann on 2007-07-12
> **drhavanger said:**
> i don't know much but i would follow [this link]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") which should lead you to [this link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"). from there you will want to find your model and what programs you will have to download.  i would use System->Administrantion->Synaptic Package Manager do a search for the recommended software and download and install that way.  much easier than finding the most current file and figuring out how to install it.  if that all works then you should see an icon the the upper right hand of your screen (by date and time) and will see your wireless and any other wireless networks in your area.  hope that helps

Thanks, but, For one, my USB adapter doesn't seem to feature there (I have a DWL-120+), the closest I can find is

 " D-Link
	

DWL-122
	

prism2_usb "

I think it may be because I don't actually have a network card, It's simply a USB adapter. Also, I'm unable to download a package via Synaptic, because on the given Ubuntu computer, I dont have connection to the internet (thus why I'm doing all this now).

@LeedsDevil: Thanks! I'm looking forward to really seeing what Linux can do, and if all goes well, possibly converting a few friends to it and go from there. I never liked being limited to one O.S choice anyway, Gotta' Share the love around, you know.


@Kevdog:

Thanks, Here's the info you asked for:

**lsusb**

Result:

Bus 002 Device 007: ID 067b:2517 Prolific Technology, Inc. Flash Disk Mass Storage Device
Bus 002 Device 006: ID 067b:2515 Prolific Technology, Inc. Flash Disk Embedded Hub
Bus 002 Device 004: ID 0781:5204 SanDisk Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 2001:3b00 D-Link Corp. [hex] 
Bus 001 Device 001: ID 0000:0000

**lshw -C network**

Result:
Bus 002 Device 007: ID 067b:2517 Prolific Technology, Inc. Flash Disk Mass Storage Device
Bus 002 Device 006: ID 067b:2515 Prolific Technology, Inc. Flash Disk Embedded Hub
Bus 002 Device 004: ID 0781:5204 SanDisk Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 2001:3b00 D-Link Corp. [hex] 
Bus 001 Device 001: ID 0000:0000

**ndiswraper -v**

Result:

utils version: 1.9
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload


**ndiswrapper -l**

Result:
tiacxusb : driver installed
        device (2001:3B00) present (alternate driver: acx)


Hope that's what you were looking for, Thanks.

Just a side note, I usually come onto forums like this half expecting them to be mostly dead, with maybe one or two die-hard forum junkies lurking around, but I've been really shocked at the incredible activity that's going on here. It's always good to see an active community, and especially so for such a useful and noble project as this.

---

### Post by kevdog on 2007-07-12
I dont think the output of 
lshw -C network 

was correct.  Can you repost this?

---

### Post by Orann on 2007-07-12
> **kevdog said:**
> I dont think the output of 
lshw -C network 

was correct.  Can you repost this?

Ah, you're right. I'm so used to the windows ctrl+C, ctrl+V process that I just do it normally, I must have forgotten to correct it with that one. Here's the correct result. (Edited Above too)

lshw -C network
Result:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       physical id: 3
       logical name: wlan0
       serial: 00:0f:3d:08:d4:8f
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Hope that's right.

---

### Post by kevdog on 2007-07-12
Your lshw output was not what I was expecting -- there is no driver associated with the wlan0 device.

Can you do me a favor?
Can you confirm the MAC address of: 00:0f:3d:08:d4:8f is the MAC address of your USB device -- its probably written on the device somewhere.

Did you modprobe ndiswrapper during the install?

Can you post the following:
sudo modinfo ndiswrapper
sudo modinfo acx

lsmod | grep ndiswrapper
lsmod | grep acx

And also post the contents of the file:
/etc/modprobe.d/blacklist

Where did you get the driver you installed with ndiswrapper?

---

### Post by Orann on 2007-07-12
Certainly, I'd be more than happy to, but I've installed Mandriva and Kept Ubuntu in a partition in my hard drive awaiting a response. Unfortunately, having done this, I'm not sure how to access it! If someone could give me a quick run through on how to boot into my Ubuntu partition, it'd help greatly.

I'll answer what I can though; I'm afraid I did not modpobe ndiswrapper while it was installing, though once I work out how to boot into my Ubuntu, I'll get those terminal results for you. As for blacklisting, the only think I have blacklisted so far is the wireless driver that already comes with Ubuntu (As instructed, I read that it interfered with other wireless drivers). I'll post the contents of that later when I am able to, naturally.

As for the Ndiswrapper download location, I'm afraid I couldn't give you an exact adress. I went around and downloaded several different versions of it from different sources until I found one that worked. I cannot remember exactly where I got it from.

---

### Post by kevdog on 2007-07-13
Ok just post back when you get Ubuntu up and running -- I cant help you with that one

---

### Post by djmaxmalta on 2007-07-13
well the gentleman that started this had a problem with his wireless connection, but mine is the opposite mine is established but when i disable wireless networking, my wireless card it still on and then interferes with my mums satellite wireless transmitter and so with mine!

but on windows when i do Fn + the Wireless sign it goes off and stops the " static/microwave bursts"  but on Linux i can't stop it and then it get annoying that i have to reboot onto windows xp,

how can i Disable the "non-connected transmition" ps this only happens becouse my laptops "Dual quad band antenna's are strong and continues to search on linux, while on windows i can control it, but linux no it still just keeps on searching even if i told it not to via the 7.04 network configuration gui

---

### Post by kevdog on 2007-07-13
Depending on your interface name (wlan0, eth0, eth1, ra0, etc), what happens when you try:

sudo ifconfig *interface_name* down

---

### Post by djmaxmalta on 2007-07-15
> **kevdog said:**
> Depending on your interface name (wlan0, eth0, eth1, ra0, etc), what happens when you try:

sudo ifconfig *interface_name* down


if that was for me it done nothing at all and my wireless connection is ETH1

---

### Post by Orann on 2007-07-18
Unfortunatley, I've moved away from Ubuntu, so I'm not sure it's even relevant any longer, but some knowledgable people wtill might be able to help me. I liked the feel of Mandriva more, so I swirtched over to that, but setting up wireless internet has be a complete nightmare so far, and is still not any more active than it started as.

You can see the thread about it [here](http://mandrivausers.org/index.php?showtopic=42893).
This has all been a pretty terrible experience really. I realize the nature of the comment, and really, it's a pretty bad thing to say to a project with such great ideas and ideas as linux, but erally, after all this, I would switch back to windows in a second If I had the chance, just because, for me, it Works.
It may not be preferable, but if it can get wireless internet working, I can tweak it to be at least usable.

unfortunatley, having just spent all my money on this new computer, I cant buy it, so I'm just trying to work it out. I've been at it nonstop for days now, and have found no solution. Some help, if you can, would really do me a great favor. Otherwise, it's something for th linux programmers to look into. As great as linux is, if It cant connect to my wireless network, it's useless to me.

---

### Post by djmaxmalta on 2007-07-19
> **Orann said:**
> Unfortunatley, I've moved away from Ubuntu, so I'm not sure it's even relevant any longer, but some knowledgable people wtill might be able to help me. I liked the feel of Mandriva more, so I swirtched over to that, but setting up wireless internet has be a complete nightmare so far, and is still not any more active than it started as.

You can see the thread about it [here](http://mandrivausers.org/index.php?showtopic=42893).
This has all been a pretty terrible experience really. I realize the nature of the comment, and really, it's a pretty bad thing to say to a project with such great ideas and ideas as linux, but erally, after all this, I would switch back to windows in a second If I had the chance, just because, for me, it Works.
It may not be preferable, but if it can get wireless internet working, I can tweak it to be at least usable.

unfortunatley, having just spent all my money on this new computer, I cant buy it, so I'm just trying to work it out. I've been at it nonstop for days now, and have found no solution. Some help, if you can, would really do me a great favor. Otherwise, it's something for th linux programmers to look into. As great as linux is, if It cant connect to my wireless network, it's useless to me.

great idea, but it seems that for the "early stages" of linux desktops it still has a long way to go.... for once it has to work on Compatability issues on network cards like combos in 56k, 100mbs, and wireless without interfing in any other wireless transmitions

---


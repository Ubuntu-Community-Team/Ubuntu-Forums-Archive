---
title: "Presario F730US wireless problems"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by BSG75 on 2008-07-29
I have a Compaq Presario F730US with Hardy Heron installed. I have tried every thing I could think of and nothing seems to be working. I have absolutely no idea what to do. Will I have to use ndiswrapper?

---

### Post by Ayuthia on 2008-07-29
> **BSG75 said:**
> I have a Compaq Presario F730US with Hardy Heron installed. I have tried every thing I could think of and nothing seems to be working. I have absolutely no idea what to do. Will I have to use ndiswrapper?
You might want to start off by opening the Terminal and typing:
```
lspci -nn
```
The first command will list out all your pci devices.  You are looking for something that is called Ethernet Controller or Network Controller.

---

### Post by BSG75 on 2008-07-29
This is what it said nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)

Someone told me that I did not have enough ram, I needed more anyway but I never got around to ordering it, until just a couple days ago. It hasn't arrived yet right now I have 950mb. Is that a problem?

---

### Post by Ayuthia on 2008-07-29
> **BSG75 said:**
> This is what it said nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
Is there another one?  If not, can you check lsusb and report back what it finds?

> Someone told me that I did not have enough ram, I needed more anyway but I never got around to ordering it, until just a couple days ago. It hasn't arrived yet right now I have 950mb. Is that a problem?
If you are able to use the live CD without any problems, I would think that it would be ok.  What I have done with one of my computers is create 1Gb of swap space.  The computer is not super fast, but it is still able to run everything I need.  The swap space a way that Linux uses the hard drive as memory.

---

### Post by BSG75 on 2008-07-29
There wasn't anything else about Ethernet or network listed. And when I checked the usb the only thing that showed up was a flash drive that I had plugged in at the time.

---

### Post by Ayuthia on 2008-07-29
> **BSG75 said:**
> There wasn't anything else about Ethernet or network listed. And when I checked the usb the only thing that showed up was a flash drive that I had plugged in at the time.

I just checked out the drivers at the HP site and it looks like you might have a Broadcom card.  Can you confirm this by doing:
```
lspci -nn|grep 14e4
```
If it does return something, let us know.  Also let us know if you have an internet connection working on it yet (wired).

---

### Post by BSG75 on 2008-07-29
No it doesn't return anything. I have been able to connect wired, it is just wireless.

---

### Post by Ayuthia on 2008-07-29
Ok.  One more try.  How about posting the results of:
```
lshw -C network
```

The ethernet controller that you provided was for your wired connection.  For some reason we have not spotted your wireless yet.

---

### Post by BSG75 on 2008-07-29
does that mean that my wireless card is broken?

---

### Post by Ayuthia on 2008-07-29
> **BSG75 said:**
> does that mean that my wireless card is broken?

Not necessarily.  However, HP/Compaq does have some problems with some of their laptops right now.  What has been happening is that the fan has not been running aggressively enough so the motherboard has been overheating and ends up causing problems with the wireless card.  I had problems with mine and was able to get it fixed by HP at no charge.

If you are able to get more information from lshw -C network, it might help us figure out what the card is.  If you don't get anything else, do you still have Windows installed on it?  You might want to check and see if you can still connect through the wireless.

---

### Post by BSG75 on 2008-07-29
I had my hard disk partitioned but recently deleted Windows. Now I kinda wish I hadn't because it is almost impossible to get support for Linux systems from HP. I have only had this laptop for a couple months so I'm am pretty sure it shouldn't be too much trouble getting it fixed.

---

### Post by BSG75 on 2008-07-29
They told me I should restore to factory conditions before they will replace my wireless card. How do I do that if I deleted Windows?

---

### Post by Ayuthia on 2008-07-29
> **BSG75 said:**
> They told me I should restore to factory conditions before they will replace my wireless card. How do I do that if I deleted Windows?

Did you wipe out the recovery partition or make a backup CD/DVD of it?  if so, you will need to use it to recover.

---

### Post by BSG75 on 2008-07-29
No I don't have the back up disk anymore.:confused:

---

### Post by Ayuthia on 2008-07-29
I am not for sure about what to tell you.  There is a chance that they will just replace the motherboard and not even boot your laptop but I am not for sure.  I was too chicken to find out.

---

### Post by Martin Marshalek on 2009-01-12
Upgrade to Intrepid. I have the same computer and it recognized the wireless of the bat.

---


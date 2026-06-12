---
title: "Network dead after reinstall of ubuntu"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Fiberkneip on 2007-03-20
Hello...

Have been fooling around trying to get my head around this whole linux thing (newb). 
Have learned alot the last few days. After installing ubuntu clean over the old workhorse (winxp) the internet 
and network worked perfectly, but now after a reinstall of ubuntu over 
the other ubuntu (formating and the whole package) the network is gone. It doesnt detect the networkcard. 
Did a ifconfig and the output was the "loopback" thingy.

:)

---

### Post by chili555 on 2007-03-20
It will help us help you if we knew what kind of wireless thingy you have. May we see: ```
sudo lspvi -v | grep -i Network
```If this command tells us nothing, please let us see:```
sudo lshw
```You can omit the parts that have nothing to do with you wireless device.

---

### Post by Fiberkneip on 2007-03-20
Ah great...

The first command gave nothing...

The second gave a whole heap of hardware but nothing that looked network
related.

The network I am on is wired and the networkcard itself is integrated in the 
motherboard (MSI MS-7028 from the "lshw" command).

Hm... A nutcracker is what we need..

---

### Post by chili555 on 2007-03-20
Ooooops! I didn't catch that it's an ethernet card, sorry. Let's try: ```
lspci -v | grep -i Ethernet
```
If this command is also unproductive, let us know what kind of computer it is. If it is self-built, please tell us the model and version, if any, of the motherboard.

---

### Post by Fiberkneip on 2007-03-20
That command did not do anything either...

Yes the rig is selfbuild: MSI 915P Neo2 Platinum 54G ( MS-7028 )
                                Intel P4 3,2
                                1 gig of ram
                                ATI x800

Dont know if that helps...

And by the way... Thanks for the effort so far!  :p

---

### Post by chili555 on 2007-03-20
Would you please do ```
sudo modprobe tg3
```and see if it kicks the interface eth0 to life. If so, please sudo gedit /etc/modules and add a line at the end:```
alias eth0 tg3
```Sometimes sudo insmod works when sudo modprobe doesn't, and vice-versa, so try both.

By the way, if you Google Broadcom BCM5751 Ubuntu the thing that catches my eye is BUG. If you have a newer kernel, say 2.6.17-11, you may be less likely to be infested.

Post back and let us know.

---

### Post by Fiberkneip on 2007-03-20
Sorry...

The modprobe came up with nothing...

I will check into that Broadcom deal...

How do you find out wich kernel your running...? And updating it without
internet would be a nice magictrick lol... :P

---

### Post by chili555 on 2007-03-20
If the cursor popped back with no complaints, that means the module is or was inserted successfully. Good! Now what does:```
ifconfig -a
``` tell us?

> How do you find out wich kernel your runningIssue the command:```
uname -r
```

> updating it without internet would be a nice magictrickMagic is actually our specialty here at ubuntuforums.org. But actually, you *do* have internet access; you are answering these posts, aren't you? If you have a CD burner, then we have the rabbit and the hat!

Let's take a few steps before that. How about ifconfig -a?

---

### Post by Fiberkneip on 2007-03-20
Ok just so things dont get messed up...

the "sudo modprobe tg3" nothing happend (cursor popped back or down or whatever)

the "sudo insmod tg3" said "can`t read `tg3`: No such file or directory"

Should I proceed with the "gedit /etc/modules" ?

The "ifconfig -a" said alot of things. The loopback thing and "sit0 Link encap: IPv6-in-IPv4" something.

Wish I could copy/paste it for you but you know...

---

### Post by chili555 on 2007-03-20
Please> Let's take a few steps before that. How about ifconfig -a?
Thank you.

---

### Post by Fiberkneip on 2007-03-20
Sorry I did an edit on the last post about the "ifconfig -a"  :P

Edit: Found out another thing. I dont think it is a Broadcom BCM5751, wrote something down
the other day before I switched from WinXP, the Ethernet is a Marvell Yukon 88E8053.
I think... Im not sure, but that is what it said in device manager in XP.

---

### Post by chili555 on 2007-03-20
```
sudo lspci -vv
``` says nothing about it?

If it is a Marvell Yukon, we will get it to work, after a few scary steps.

---

### Post by Fiberkneip on 2007-03-20
It did not say anything about Marvell Yukon, or Broadcom for that matter. I will check the MSI box... lol

---

### Post by Fiberkneip on 2007-03-20
Ok... I flipped through some of the documents in the MSI box. Two options where listed.
LAN: Realtek 8100/8110S (Optional)
        -Integrated Fast Ethernet MAC and PYH in one chip.
        -Compliance with PCI 2.2
        -Supports ACPI Power Management
       Marvell 8053 (Optional)
        -PCI Express bus Spec 1.0a compliant
        -X1 PCI Express interface with 2.5 GHz signaling
        -10/100/1000 IEEE 802.3 compliant

Thats what it said in some documents from MSI.

Hope that helps somehow...

---

### Post by chili555 on 2007-03-20
Before we jump through hoops only to find out we're addressing the wrong card, or chipset, in this case, I'd love to have more information about just what you have there; Marvell, Realtek or otherwise.

Since you built it, you should be comfortable taking off the side of the case and getting in there with your brightest flashlight and your newest glasses to see if you can identify the mystery chip. I'd hope it would be close to the LAN connector.

Good hunting!

---

### Post by Fiberkneip on 2007-03-21
Well took a peek inside the case and did not see the writings on the chips. 
But flipping through some of the MSI books showed a chart over the
motherboard and the chip closest to the RJ45 plug was the Marvell chip.
Lets just go with it and see what it does... Ubuntu is a clean install and reformating 
doesnt take long...  :)

---

### Post by chili555 on 2007-03-21
Here are the steps we're going to take: sudo everywhere.
1. backup /etc/apt/sources.list```
cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
2. replace temporary (!) all edgy with feisty in sources.list```
sudo gedit /etc/apt/sources.list
```In any line the is not commented out #, replace the word edgy with feisty. Save and close gedit.
3. apt-get update
4. apt-get install linux-headers-2.6.20-12 linux-headers-2.6.20-12-generic linux-image-2.6.20-12-generic. IMPORTANT! Firmly reject the offer for ALL other updates. Ignore the little orange icon.
5. restore your /etc/apt/sources.list from step 1:```
mv /etc/apt/sources.list.bak /etc/apt/sources.list
```
6. reboot

The beautiful thing about installing a new kernel is that if it does not go well (very doubtful), your grub menu, at start-up will still allow you to boot into 2.6.17-x and then remove 2.6.20-x.

Good luck and post back.

---

### Post by Fiberkneip on 2007-03-21
Crazy..

Something strange happend... Did not do any of your steps because the network just
became alive! I am now on the ubuntu computer... Just turned it on and there it was.
I did not do any reboots yesterday, maybe I should have. Did run a "ifconfig" and the
eth0 was alive and well. Do I have to go through your steps in the name of science?
I bet there was something we did yesterday that kicked in...

Thank you so much...  :)

Edit: And by the way "lshw" confirmed that it was a Marvell Yukon lol

---

### Post by chili555 on 2007-03-21
Don't fix what ain't broken! But keep the fix handy if you need it. Glad it's working for you.

---


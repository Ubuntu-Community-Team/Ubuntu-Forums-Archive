---
title: "moved hard drive to new computer udev won't write new rules"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by rt-guitar on 2014-11-08
Ubuntu 14.04 server no GUI, live disk was also 14.04 but desktop

Okay spent some time now trying this, I know unlike windows (which has to download all its drivers) Ubuntu should have all needed drivers in the kernel even for multiple systems. I wanted to test this out, I have 1 2tb HD that has 1tb filled on it. While using Plex and transcoding I use all of my 2gb of ram. I know this will slowly kill my 2tb HD and give cruddy performance.

I have a PC with 8gb of ram and an i7 quad core (vs my current dual core) I could not do a full installation due to the fact I need another HD to transfer content (I know bad practice to have no raid or back up set up but when the money comes that will too) so I took the HD from one comp to my better one. I was excpecting mostly nothing to work.......low(lo?) and behold everthing works except networking.

I know my issue lies in etc/udev/rules.d/70-persistent-net.rules I tried first deleting it(after backing it up) as it keeps the old info from the last PC. Tried resetting the udev service as well as networking, udev comes back blank but seems to do nothing...........networking fails. Ran modprob commands after udev trigger=change and =add.

Finally thought hit a stroke of genius(should have known better haha) I got a live disk and stole its .rules setting created by the disk on the new computer. Copied it to the 2tb HD and rebooted it holding it would work but the.rule the live disk created did nothing.

Im sure I've left out some things I tried and I will add them as I remember any ideas I will try. Most of what I see on the interwebs is for virtual machines but I found a few for bare machines and no thing has worked......slowly loseing hope In the world haha (I don't post much need a read out just ask I'm not sure which will help).

---

### Post by weatherman2 on 2014-11-08
You may be confused about what the udev rules are for.  They aren't drivers - they keep consistent names for device names like "eth0," "eth1, etc.  If you had your hard drive originally in one computer, it would assign eth0 originally to the first network card found.  If you move the hard drive to another computer, you'll have a new network card.  If you do nothing with the udev rules, then the new network card will get assigned eth1.  Move the hard drive to yet a third computer and it will get eth2.  Move it back to the old computer, and it will wind up back with eth0 - thanks to the udev rules.

But if you don't want the OS to remember the old network, erase the udev net rules file.  Then the next time you reboot, it starts over and assigns eth0 to the first network card it finds.

Anyway...if your Linux installation doesn't work when you moved the hard drive to the new motherboard, it's probably a driver issue, not a udev problem.  It's common for Linux not to have drivers for newer hardware.

You could start debugging by doing these terminal commands and showing the results here:

```

sudo lshw -C network
ifconfig
lspci -nn

```

This should help figure out whether your network card was detected, at all.

Also, what are the contents of the file 

/etc/network/interfaces

?

---

### Post by rt-guitar on 2014-11-08
Can I pull these commands from a live disk, with the server command line only and no networking I'm not sure how else to post them. I do know ifconfig only shows lo and lspci shows a Ethernet controller.

---

### Post by rt-guitar on 2014-11-08
I also didn't change the interfaces file and it was never static left it dchp

---

### Post by rt-guitar on 2014-11-08
Guess I didn't read your full post the "newer" computer is a 2009 Asus with an I7 and the kernel in the live disk should be the same as in the server. The live disk worked great I just took the udev rules because I could not find my Mac in anyway. Ifconfig -a shows just lo which seems odd since lspci does see an Ethernet controller.

---

### Post by weatherman2 on 2014-11-09
Remember that a live desktop CD uses Network Manager to mange networks; the server edition of Ubuntu does not.

In my Ubuntu 12.04 server edition box I use, I have these lines in my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp

```

I don't recall if I added the bottom two lines or not.  But they wouldn't be there on a desktop edition of Ubuntu that runs Network Manager, because Network Manager handles eth0.

---

### Post by rt-guitar on 2014-11-09
You probbably didn't add the last two, that calls in the dchp so if you were to switch to a static ip then you change dchp to static and add the network info below. 

But I did forget about network manager, will a ubuntu server live disk solve my issue?

---


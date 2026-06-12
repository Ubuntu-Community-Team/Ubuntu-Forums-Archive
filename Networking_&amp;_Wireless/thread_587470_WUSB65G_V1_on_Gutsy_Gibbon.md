---
title: "WUSB65G V1 on Gutsy Gibbon"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Erky on 2007-10-22
Hello,

I had my Linksys WUSB54G USB Wireless adapter working on my desktop while I was using Feisty Fawn (7.04). It took me awhile to get that working. Now that I upgraded to Gutsy Gibbon, it no longer works. Can anyone help me with my problem?

---

### Post by MariusSilverwolf on 2007-10-22
As posted here: [http://ubuntuforums.org/showthread.php?t=586017](http://ubuntuforums.org/showthread.php?t=586017)


First and foremost, Wieman1 and Zoinks, you guys wrote up some awesome tutorials for getting the Ralink drivers to work. You guys rock.

That fact nothwithstanding, here's what I've learned from following both Tutorials to the letter:

The LinksSys WUSB54Gv4 USB Wireless Network Adapter does NOT want to work in Gutsy with the AMD64 flavor. At all.

In Fiesty, the Serial Monkey rt2x00 Legacy drivers picked up the card, and as long as I dropped down to WEP instead of using WPA I could connect no problem. After the upgrade to Gutsy, I was caught in the endless loop of my Wireless network being detected, being prompted by Network Manager for the encryption password, sitting for 30 to 60 seconds, and repeating.

First, I ran through Wieman1's tutorial. Like a few others, when I Blacklist the rt2500usb driver in /etc/modprobe.d/blacklist, I see NO Wireless Network Adapters in Network Tools. I suspect this is because NDISWrapper is 32-bit, and I need to recompile it for AMD64 architecture. I tried following the NDISWrapper on AMD64 Tutorial, but there's no Debian folder within the latest package, and none of the files I need to alter to recompile exist anywhere on my system.

So, having to give up on NDISWrapper, I happened upon Zoinks tutorial and my hope was renewed. For a time. BUT, the only driver package from Serial Monkey that will bind to the card is the rt2x00 legacy version of rt2500usb. rt2500, rt2570, and rt73 all fail, no matter how many times I remove previous modules or how many alterations I make to aliases and interfaces.

So, until the rt2x00 legacy driver package can be fixed to actually let me connect to my wireless network -- which I've tried with WPA, WEP, and open without any luck -- I'm dead in the water. I may just pick up a reel of CAT5 and run a line under the house to connect from the router to the PC via hardline. For the drop on each end and the run in between I should only need about 100 feet of cable and 60 feet of pvc conduit.

Just thought I'd share my war story. If anybody else has found a way to get that confounded piece of hardware to actually connect to a wireless network and get past the router, I'd love to hear it. I'd rather not crawl around under a house in Florida when it's still 90 degrees with 70% humidity outside during the day.

---

### Post by Erky on 2007-10-23
bump. Please help! I'm really desperate at this point!

---

### Post by gwhitener on 2007-11-04
I don't know if you got this figured out yet or not, but I can tell you what worked for me.

In a different thread, someone named benfrasersimpson posted a bunch of stuff that he had to blacklist.  If you follow to my posts, you can find the thread, or click here: [http://ubuntuforums.org/showthread.php?t=418925]("http://ubuntuforums.org/showthread.php?t=418925").

Then, loading the latest ndiswrapper, and ndisgtk, he installed the driver for the wireless adapter.

I followed what he did, and it worked like a charm.


When I upgraded to Gutsy, I kept a file of the changes in the blacklist, since there were some differences.  However, even adding the items which were removed in the upgrade, my wireless did not work.  I did a clean install of Gutsy, and followed his procedure, and I am back online.

From what I have read, the ndiswrapper headers (I don't know what that means) are not copied to the new kernel once you upgrade.  So, regardless of whether you upgrade or do a clean install, make sure that you do a clean install of ndiswrapper for the new kernel, then re-install the drivers for the USB dongle.  You won't get stuff like signal strength, or any response from the applet in  the top right corner, but you will be online.

Cheers.

---

### Post by zackf on 2007-11-04
I bet you just have to recompile ndiswrapper since an upgrade to 7.10 will upgrade the kernel.

---

### Post by benfrasersimpson on 2007-11-10
Mine also has stopped working.
I did a clean install of gutsy, and blacklisted all the drivers that are listed in my other thread, and install the driver. However when i restart the computer, it stops working. Any ideas??

---


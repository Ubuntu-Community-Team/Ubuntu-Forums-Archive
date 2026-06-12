---
title: "Ubuntu -- Totally Bunk Wireless/Wired Internet? Can I fix this?"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by AmagicalFishy on 2015-07-01
Hey, guys. I've got an HP Elitebook 8460p.

I've been using Ubuntu as my main OS for about a year and a half now, and I love it. I wouldn't switch back to Windows for anything...

... but the *internet* is just so, so bad. I use WICD after having tremendous problems with the default manager; but something about Ubuntu's internet (both wired and wireless) is just complete trash. My wireless slows to a crawl randomly; some days it works excellently, most days it slows down (or disconnects) about every 20 minutes. I'm having a hard time succinctly explaining the issue because it seems like a totally random mess. I have no idea when or where my internet will work well, work badly, or not work at all. I don't know what problems I'll be presented with (whether it be a "bad password" error [when the password is 100% correct], getting stuck on "Obtaining IP Address", randomly dropping or getting an excessively weak signal). I can't even directly connect via Ethernet without some crazy problem. Right now, I'm on Windows. When I plugged the Ethernet cable logged into Ubuntu, it apparently connected successfully—but I had no access to the internet.

I **know** it isn't my network, because switching to my Windows partition (which I have just to play the occasional game \\:D/) works immediately as it should. I've moved apartments twice, and have connected to a bunch of different networks. There are only two constants: Ubuntu's internet is always terrible, and Windows is always excellent.

This doesn't come anything close to making me want to switch to Windows (Ubuntu's better by miles), but: 
Why is there such a **huge** discrepancy?
Is there anything I can do to fix it?
Do other people have this problem?

Internet's a pretty large aspect of computer use, and I'd really like to get this fixed once and for all. I've tried everything from switching DNS servers to getting a VPN to using different drivers, and nothing seems to dent the problem.

---

### Post by weatherman2 on 2015-07-01
I haven't had that same experience at all.  I've used Ubuntu on four or five different laptops now over the last few years.  With the right wireless card, I get solid, fast, reliable WiFi connections that stay connected for hours and almost never drop.

People who complain about network problems in Linux, when the same hardware works fine in Windows, usually have some sort of driver issue.  Sometimes the driver support is poor.  Sometimes you can tweak driver settings or install an updated driver and improve things.  My solution is usually to upgrade the hardware (when possible) to something that has better Linux support.  With wireless cards, I've upgraded many laptops to Intel wireless cards, and for me, at least, they have worked flawlessly with Ubuntu, at least in the last 5+ years.  I recall about ten years ago having issues with Ubuntu and wireless, but those problems are long gone.

Unfortunately for you, you don't have the option (or much of one) to upgrade your laptop's internal wireless card, because HP (like Lenovo) whitelists their wireless cards.  In other words, if you plug in a wireless card that isn't on their "approved" list (saved in BIOS), it won't even POST or allow you to boot.  Instead, it will complain until you remove the offending wireless card.  This is one reason I will never buy an HP or Lenovo laptop.  I've upgraded Dell, Acer, and Toshiba laptop wireless cards numerous times without issue, so I'll stick with those brands.

If you want to try the software route to improve your network issues, start - for wireless, anyway - by running the wireless script given in one of the "sticky" posts at the top of these forums and post the results here (probably in a new thread with a better title).  Then experts can suggest fixes depending your exact network cards - new drivers, settings changes, etc.

---

### Post by mkmasn on 2015-07-01
This issue is happening across the board with Windows, OS X, and Linux.

I have a feeling it's directly tied to the US government inserting backdoors into PC hardware.

---

### Post by QIII on 2015-07-01
Yeah, um ... No.

I have a feeling it's lack of Linux driver support from the manufacturer.  I've never had an issue with wireless.  But I check for compatibility first.

AmagicalFishy:  Please follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=370108") to provide us with some information that might help find a solution.

---

### Post by mkmasn on 2015-07-01
Is that so? How old is your hardware? Perhaps older than the recent hardware with government backdoors?

So why are these issues occurring in Windows and OS X? My specific issue with the Lenovo g50-45, I know is because the driver being used in the kernel is incorrect, but I doubt it will fix anything if the driver gets fixed.

[http://lifehacker.com/fix-yosemite-wi-fi-issues-with-a-terminal-command-1663414063](http://lifehacker.com/fix-yosemite-wi-fi-issues-with-a-terminal-command-1663414063)

---

### Post by chili555 on 2015-07-01
> I know is because the driver being used in the kernel is incorrect,What is your evidence, please?> [http://lifehacker.com/fix-yosemite-wi-fi-issues-with-a-terminal-command-1663414063](http://lifehacker.com/fix-yosemite-wi-fi-issues-with-a-terminal-command-1663414063)What, exactly, does this have to do with your Lenovo? This is purportedly a fix for OSX. That has nothing to add here.

---

### Post by NoWayWin8 on 2015-07-02
> **AmagicalFishy said:**
> I **know** it isn't my network, because switching to my Windows partition (which I have just to play the occasional game \\:D/) works immediately as it should. I've moved apartments twice, and have connected to a bunch of different networks. There are only two constants: Ubuntu's internet is always terrible, and Windows is always excellent. Since this is a dual boot, it might help a lot if you set both Windows and Ubuntu to use the same hostname. See what the hostname is in Windows and then start Ubuntu and enter that in the "DHCP Client ID" box under the connection's IPv4 settings in Network Manager. And also set IPv6 to "IGNORE".

---

### Post by QIII on 2015-07-02
mkmasn:

> My specific issue with the Lenovo g50-45

Then you are not facing the same issue as AmagicalFishy and your comments here are off topic.

Please do not hijack another user's thread to make a place for your soapbox.  I have responded in one of your threads regarding this issue.  Please confine further comments to that thread.  Any further comments you make in this thread will be removed.

Thanks.

---

### Post by AmagicalFishy on 2015-07-04
Hahaha, this thread took a... weird turn!

Anyway, excellent answer, weatherman2. Thank you so much for that writeup—when next I buy a laptop, it won't be HP (their cooling-situation sucks, too).

Q3, I ended up being Special Case 1 in the Broadcom thread.

I've attached the results of the wireless script. In my dmesg, I've got a [UFW BLOCK] thing that happens pretty often.

[ATTACH]Wireless Script Results[/ATTACH]

---

### Post by praseodym on 2015-07-04
Install the driver from 14.10. Save these files in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and activate the STA driver.

---

### Post by AmagicalFishy on 2015-07-04
Before I do that, just to make sure—is the suggested driver the one that comes w/ Ubuntu? I know I'm using the proprietary one; I've had better results in the past day or two with it than I've had w/ the default.

---

### Post by praseodym on 2015-07-05
Yes, it is the improved proprietary driver from Broadcom for 14.10.

---


---
title: "[SOLVED] BCM 4306 and ndis on 8.04"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2008-05-30
I have been going crazy the past 2 days trying to restore my system back to normal.  Long story short I had to reinstall ubuntu on my HDD (totally scrapped windows :)) but now I lost my wireless internet and I can't get it back.
I previously was using ndis wrapper on my system and I want to get it up and running again.  I tried using the automatic B43 that shows up in "hardware drivers."  It lists the networks but when I try to connect to any of them dmesg reports that it just keeps timing out.
I have tried just about every how-to I can find on ndiswrapper.  None of them have worked.  I think I have the problem in my sights but I don't know what to do to fix it.  When I boot my dmesg reports that "ndis version 1.52 loaded" and then it lists the driver loaded, all well and good.  Then I get two NdisWriteErrorLogEntry s 191 and 194.  I think that means it wrote an error in the system log.  Then I get (this I think is the problem) "Windows driver couldn't initialize the device: c0000001."  Then a little later "ndiswrapper: probe of 0000:00:09 (my device address) failed with error -22".  I googled this and error 22 is related to some HIGHMEM junk in the kernel that allows for 4G of ram.  I don't think this should be a problem because I have 512MB.

ndiswrapper -l tells me that the driver is installed and that the alternate driver is ssb which I think is wrong also.

In my /etc/modprobe.d/blacklist I have b43 and ssb and bcm43xx all blacklisted.

sudo lshw -C network reports that my card is still using the b43-pci-bridge driver with the ssb module (how I don't get because it is blacklisted)

I have a script in place that runs at start-up that rmmods and modprobes ndis and some other stuff.

I noticed that at shut down I can see very briefly that there is a terminal error message.  It says something about ssb and b44.  The red [fail] caught my attention but I am not able to read it because it is so quick.

I know this is a lot of info to sift and figure out but I would really appreciate some help.  Funny thing is I've had ndis working before on this exact hardware and ubuntu release without this much difficulty.  I also have a second computer with the same network card and ubuntu release that is running ndis if this is any help for problem solving let me know.

Also one more thing.  I used the CD to get ndis wrapper but I had to bring the router temporarily to the computer for a wired connection to extract the firmware.  So now I have the firmware, the ndis from the live cd and no internet on this computer at all.  Thank you for any and all help!

(Ubuntu rocks)

---

### Post by gspaulding on 2008-05-30
This thread totally works with BCM4306.  I have it (rev 03) on my laptop and followed the steps in the first post and had wireless working in about 10 minutes.  I used the steps in 2f following the link provided for step 2.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by yipperzz on 2008-05-30
I had a problem with my laptop also.  I was able to get it working once I uninstalled (rebooted) and reinstalled b43fwcutter.  I was getting an error at startup about the firmware.  I followed these instructions [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)  and got the Linksys drivers for my rev 02 card.

---

### Post by f37u5g0d on 2008-06-02
Thank you guys for your help.  I used this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .  It was the most official one I could find.  I was trying to do it without internet on the computer which was giving me the results I described in the first post.  I, very reluctantly moved the computer downstairs (it's a desktop) to get wired internet.  I did some updates (120mb) and ran through the ndis process again and it worked without a hitch!  Someone should really do something about the offline installation.  It's very frustrating not knowing that all you need is a wired connection for a hassle free installation.

---


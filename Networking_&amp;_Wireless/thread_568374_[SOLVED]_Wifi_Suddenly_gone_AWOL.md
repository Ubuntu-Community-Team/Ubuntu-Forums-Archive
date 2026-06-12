---
title: "[SOLVED] Wifi Suddenly gone AWOL"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by TheZergcorp on 2007-10-05
So I excitedly plotted with a friend and Linux buff of mine to order a laptop for college and finally kick windows to the curb. I discussed what hardware would work well for Ubuntu with him, and we finally settled on the HP dv6000 series, and I picked out the following specs:


- Genuine Windows Vista Home Basic (32-bit)
- Intel(R) Core(TM) Duo T2350 (1.86GHz/ 2MB L2Cache)
- 15.4" WXGA BrightView Widescreen (1280x800) 
- 512MB DDR2 System Memory (1 Dimm)
- 256MB NVIDIA(R) GeForce(R) Go 7400
- HP Imprint Finish + Microphone
- Intel(R) PRO/Wireless 3945ABG Network Connection
- 160GB 5400RPM SATA Hard Drive
- Super Multi 8X DVD+/-R/RW w/Double Layer Support 
- No TV Tuner w/remote control
- High Capacity 6 Cell Lithium Ion Battery
- Microsoft(R) Works 8.0

He wiped my harddrive of the Vista Virus, and we loaded up Feisty Fawn, It's been going swimmingly for the last few months, even though I'm a first time Linux user I've been referring to the forum when I have an issue and trying to resolve it myself. However the last few days my Wifi was really screwy, I've configured and monitored connections through the NetworkManager Applet 0.6.4 by Red Hat thusfar, and haven't really had any issues up until a few days ago. 

The first time I had an issue, I started up Ubuntu and didn't get the normal prompt that I usually do when I sign on, asking me for my keyring passcode, and the Applet wasn't showing up in my Notification Area as it usually did. In addition, the indicator light on the front of my notebook was pure orange, rather than the alternating blue/orange or solid blue I normally get with Wifi connections. I double checked that the switch was on next to the indicator light; it was. I went into System > Administration > Network to see if something was wrong with the actual signal, and only one of the local wifi networks showed up, and not the one I had been connecting to.

I didn't, at the time, know the name of the Applet that had been giving me the heads-up until that point, so I was a bit lost as to how to resolve the issue. Having to deal with networks at home with regular Ethernet, I knew that sometimes there didn't really seem to be anything one could do other than deactivating different components of the network and then reseting everything. So that's what I did. I flicked the switch off a few times, refreshed the network settings, tried to detect the network again, etc, and then shut off the computer. When I logged back in, the applet was back, however it was reading no connectivity, even though when one looked at the networks, they were at over seventy percent. That was three days ago. Since then, every time I turned the computer on and off again the network decided to do something else screwy, And I've had to keep trying to reset things and reboot to get anything to work. This persisted until last night when I booted up and everything was fine. And it's been alright since, but I don't know if I want this to stay unresolved until I have a major research project due and find my wifi suddenly inoperable.
	Finally, I noticed that seemingly at random when I went into the Network settings under Administration, and went to the properties of the wifi I found that the Wifi either had a check box reading “Enable Wireless Networking” or “Enable roaming Mode.”  The issue was, they were both in the same spot, and I didn't quite catch why one showed up at some points and why the other was nowhere to be found. I had the options both show up when the network was working and also when it wasn't.

Thanks to anyone who bothered to read through this wall of text, and I will be appreciative of any suggestions to head a possible problem off at the pass before it becomes an issue again.

---

### Post by Tripletaco on 2007-10-05
I just switched over to Gutsy Gibbon this morning.  My wifi is also dead in the water.  can't seem to make it work. A lot of things you noticed were similar to my problem.  No more Keyring for one.

---

### Post by johnnycoke on 2007-10-06
I was suddenly without my wifi as well, after an update and reboot.  My pci card was detected, but the ath0 interface was nowhere to be found.  I ended up selecting the 2.6.22-12 kernel from the grub menu at boot, and it works fine for now.

---

### Post by halclo on 2007-10-06
I had the same issue after the latest update and also had to revert back to the 2.6.22-12 kernel.  It appears to be a problem with the 2.6.22-13 kernel.  No wifi interfaces are found and no mention of ath0 or wifi0 in dmesg either.

---

### Post by kaboodle_fish on 2007-10-06
I had the same problem. Went back into the previous kernel (.12) and did an update through Synaptic which had a restricted drivers update and some other stuff and now my wireless is working fine in .13 :)

---

### Post by Lord Illidan on 2007-10-06
Are you aware that the restricted modules may not have been updated yet in your local mirror?
Switch back to the .12 kernel for now. Then, configure your software sources to use the main server, and update your restricted modules from there.

---

### Post by untjake on 2007-10-06
Pardon my ignorance, but how do you "Switch back to the .12 kernel"? Could someone post the command to revert to a previous kernel version? I'm having the same problem on my HPdv6000 laptop. 

Thanks

---

### Post by Lord Illidan on 2007-10-06
From the boot menu, GRUB, chose Ubuntu gutsy (development branch), kernel 2.6.22-12-generic

If you can't see it, you might have to press ESC.

---


---
title: "HP Stream, Broadcom BCM43142 drops connection, Xubuntu 16.10, (may have wrong driver)"
date: 2017-03-11
forum: Networking &amp; Wireless
---

### Post by el33thaxor on 2017-03-11
I definitely should have came to this forum when I first started having problems, instead I believe I did a bad fix which may have caused unnecessary trouble.

**Problem:**
About a year ago I got an HP Stream 13 (13-c010nr) and it worked essentially without major issues for several months. At some point, I forget exactly when and what changes might have occurred, the wireless started dropping regularly. It would work anywhere from 2 minutes to 2 hours to sometimes 2 days and suddenly drop and become unable to reconnect. Certain Wi-Fi connections seemed worse than others, but I haven't been able to tell why. Generally, disabling/re-enabling networking in the taskbar menu would temporarily fix it, but with no guarantee as to how long it would maintain the connection. Other times I would have to reboot the computer in order for the wireless to start working again. I've been too lazy to come on this forum for a proper fix. 

**Fix attempts:**
The first thing I did was to buy a USB Wi-Fi adapter, the Edimax EW-7811Un (Realtek based). The problem persists even with the USB inserted, but sometimes unplugging it and plugging it back in will instantly fix my wireless, if temporarily. This makes my computer somewhat more usable but doesn't solve the issue. I only use this sometimes. For example my wireless is working well enough without it for me to be posting this right now. 

The next thing I did was to follow the instructions on this Youtube video which claims to solve this issue for HP Stream laptops with Ubuntu: [https://www.youtube.com/watch?v=epaCic730Jk](https://www.youtube.com/watch?v=epaCic730Jk)
The instructions are to: 
1) Download a Realtek driver from here: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) [I now know that my laptop actually has a Broadcom wireless card]
2) Run *sudo make* and *sudo make install* in the extracted driver folder while it's still in Downloads [I'm not clear on what this does]
I have done this fix *several* times over the past few months. It has actually somehow worked, at best for a few days, but the problem always returns. 

**Information from sticked thread:**
Anyways, after those fixes here I am.

The info from the wireless-info is attached [ATTACH]274080[/ATTACH]. 
lspci lists my network controller as a Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)

**Current problem: **
So normally at this point I would follow the instructions on this forum for installing a Broadcom driver, but I'm worried that there will be some kind of conflict with the Realtek driver that I've installed so many times. What should my course of action be?

---

### Post by el33thaxor on 2017-03-21
I hate to have to bump my own thread, but I need help on this.

As the [sticked thread on installing a Broadcom driver]("https://ubuntuforums.org/showthread.php?t=2214110") explains, 
> 
If you have previously installed any drivers, have blacklisted or uncommented any driver files or configuration files or have done any changes whatsoever to the system to make the drivers work, you will need to undo them in order to follow this guide.
As I explained in the above post, I'm not quite sure what I did when installing the Realtek driver and would like some advice on how to proceed.



One new additional piece of information, I found on [an HP support forum]("http://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/HP-Stream-WLAN-module-upgrade-Wifi-card/td-p/5007734") that 
> The Service Manual for the Stream 13 says it  officially "supports" both the Broadcom BCM4312 and the Realtek 8723BE
But surely if lspci shows that I have a Broadcom card then that is what I have?



Here is my wireless-info.txt in a Pastebin for easier access: [https://paste.ubuntu.com/24222027/](https://paste.ubuntu.com/24222027/)

---

### Post by jeremy31 on 2017-03-21
See if the newer version of the driver is better [https://ubuntuforums.org/showthread.php?t=2352116&p=13605277#post13605277](https://ubuntuforums.org/showthread.php?t=2352116&p=13605277#post13605277)
See if disabling power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---


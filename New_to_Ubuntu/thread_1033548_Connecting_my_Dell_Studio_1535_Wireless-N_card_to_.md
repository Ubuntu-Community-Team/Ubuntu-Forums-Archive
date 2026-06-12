---
title: "Connecting my Dell Studio 1535 Wireless-N card to internet"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by JBrehm on 2009-01-07
Hey all!

So, I just got my Dell Studio 1535 in the mail the other day. Installed ubuntu 8.10 with no difficulties, but I can't seem to get it to connect wirelessly to the internet. The ethernet works just fine (I'm on it now), as does the wireless on the Vista portion of the comp. But no matter what I try, it won't connect in ubuntu. The laptop has a Dell 1510 wireless-N card. When I put <lspci -vvnn | grep Wireless> in the terminal, I got this 

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Does anyone know if there's anything I can do to get it to work? Or am I doomed to using wireless in Vista and wired in ubuntu?

---

### Post by RobsterUK on 2009-01-08
Have a look at this page to see if your device is listed, there may be some helpful info

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI)

---

### Post by JBrehm on 2009-01-08
That looks like it should work for me, unfortunately I'm still rather stupid when it comes to linux and knowing what someone's talking about when they give directions in linux-ese. I have the package from the broadcom corp website, but I have no idea what I need to do with it now that I've downloaded it. I also went to hardware drivers and tried to activate my Broadcom STA wireless driver, but it won't activate. I just now got my ATI driver to activate, but wasn't able to get my wireless driver to do so. What do I need to do?

BTW, I think I installed ndiswrapper, but I'm not sure, and neither am I sure how to get rid of it to continue on with this.

---

### Post by RobsterUK on 2009-01-08
Ok I think you need to follow the instructions on this page:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

When it says remove existing ndiswrapper wireless drivers, you should be able to do this by going to System > Administration > Windows Wireless Drivers

If you have a driver enabled in ndiswrapper that might be why you can't enable the one offered in Administration > Hardware Drivers

Good luck, if you get stuck post back

---

### Post by JBrehm on 2009-01-11
Ok, so here's an update on this. 

I somehow got my wireless to start working again. Not entirely sure how. I went into hardware drivers and clicked Activate the broadcom STA wireless driver, and it wouldn't activate it. I don't know why. Somehow though, my wireless just randomly starting working a few minutes later. But then I found that when I reboot or anything like that, it doesn't work when I log back into Ubuntu. I got it to work this time though by doing the same thing again, going into hardware drivers and activating the driver. Any idea why this is happening?

---

### Post by JBrehm on 2009-01-14
Kind of a bump and an update. 

My wireless works. But I have to click the activate button under hardware drivers each and every time I reboot the system. And each time I click activate, it shows the driver(s) as not being activated (they're still gray versus green), yet the wireless starts to work nonetheless. 

Any ideas?

---


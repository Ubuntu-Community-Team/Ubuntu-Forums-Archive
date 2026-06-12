---
title: "rt61pci needs restarting on gutsy"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by blurp on 2007-12-20
I'm running Gutsy Gibbon, and the rt61pci driver works fine on the latest 2.6.22-14-generic kernel.

However, whenever I reboot the machine, the wireless connection will be not be loaded automatically. I need to issue a ```
sudo /etc/init.d/networking restart
``` command to make iwconfig properly associate with the access point.

How can I debug this? I want the machine to automatically associate with the access point upon startup. I already have the line "auto wlan0" in /etc/network/interfaces since day one but obviously this doesn't work.

My wireless network is a 802.11g with essid broadcast and WPA2, TKIP-PSK. The machine has a static IP address.

---

### Post by ajmfulcher on 2007-12-22
I've posted a solution to this here:

[http://ajmf.wordpress.com/2007/12/09/hello-world/](http://ajmf.wordpress.com/2007/12/09/hello-world/)

Basically, it seems that the current Gutsy rt61pci modules are pretty old - source are dated 20070219 - and contain a bug that caused issues with DHCP, hence need ing to restart networking.  Following the steps detailed will update you to a much more recent rt61pci module set, with that bug fixed.

---

### Post by brodiepearce on 2008-02-16
> **ajmfulcher said:**
> I've posted a solution to this here:

[http://ajmf.wordpress.com/2007/12/09/hello-world/](http://ajmf.wordpress.com/2007/12/09/hello-world/)

Basically, it seems that the current Gutsy rt61pci modules are pretty old - source are dated 20070219 - and contain a bug that caused issues with DHCP, hence need ing to restart networking.  Following the steps detailed will update you to a much more recent rt61pci module set, with that bug fixed.

After completing the guide, the NetworkManager applet can't see my wireless device.  

When I try manually loading the rt61pci module, it looks like it's looking for it in /lib/modules/2.6.22-14-generic/, and not in the deeper /lib/modules/2.6.22-14-generic/ubuntu/wireless directory.  If I move it to /lib/modules/2.6.22-14-generic/ it comes up with 'unknown symbol' errors for each module.

I have a feeling that I may have incorrectly edited the rt2x00mac.c file, would you be able to post a sample of what the text needs to read after editing out the &#8220;rt2×00dev->interface.id,&#8220; references?

---

### Post by blurp on 2008-04-17
> **brodiepearce said:**
> After completing the guide, the NetworkManager applet can't see my wireless device.  

When I try manually loading the rt61pci module, it looks like it's looking for it in /lib/modules/2.6.22-14-generic/, and not in the deeper /lib/modules/2.6.22-14-generic/ubuntu/wireless directory.  If I move it to /lib/modules/2.6.22-14-generic/ it comes up with 'unknown symbol' errors for each module.

I have a feeling that I may have incorrectly edited the rt2x00mac.c file, would you be able to post a sample of what the text needs to read after editing out the “rt2×00dev->interface.id,“ references?

hi brodiepearce, did you solve the problem?

---

### Post by brodiepearce on 2008-04-17
> **blurp said:**
> hi brodiepearce, did you solve the problem?

No, not yet.  I've been using XP for the past four weeks, once Hardy is officially released I'll chuck that on as the wireless was working flawlessly in the betas.

---


---
title: "2 problems"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by olayak on 2010-09-11
Hi!
so - prob 1:
1. ubuntu is recognizing my wireless modem, but for some reason is unable to connect!!
help! internet works fine when I plug it into the modem.

prob 2: I had ubuntu on a separate partition from win (my backup os).  long story short, I erased the partition to do a clean install of ubuntu.  Somehow I put ubuntu on the same partition as windows. So - 
1. is this going to be a problem in the future? How would I even get ubuntu off of a partition that is shared with windows? (if the need ever arose)
2. is there an easy way to move ubuntu over to the other partition? Would this screw up the grub menu?
3. what do I do with a blank partition, anyway?

thanks!
Kathy

---

### Post by abs_kkk on 2010-09-11
solution 1:
You could try adding your network manually. Go to System>Preferences>Network Connections, go to the Wireless tab, then click on Add.

[LIST]
[*]In "Connection Name", you can put whatever you want.
[*]Check "Connect Automatically".
[*]In the Wireless tab, enter the SSID of your network. Make sure "Mode" is set to "Infrastructure".
[*]In the Wireless Security tab, change settings to match the security you set up on your router.
[*]In the IPv4 Settings tab, change settings to match your router's configuration; if you're using DHCP, just set "Method" to "Automatic (DHCP)", and that's all.
[/LIST]
solution 2:
1: if u need to un install ubuntu try this link
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
2: i am not sure
3: u can use it as a place to store files :P

---

### Post by olayak on 2010-09-11
Thank you!! :)

---


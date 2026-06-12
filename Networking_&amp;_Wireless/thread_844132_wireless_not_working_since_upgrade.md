---
title: "wireless not working since upgrade"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by silent the spy on 2008-06-29
Hi, hope someone can help me please.

I upgraded to Hardy from Gutsy. Now my wi fi is not working. Before I got it working here
[http://ubuntuforums.org/showthread.php?t=654694](http://ubuntuforums.org/showthread.php?t=654694)

I tried everything in that thread but no luck. Any help is greatly appreciated thanks.

John

---

### Post by ugm6hr on 2008-06-29
How did you upgrade?  Fresh install or upgrade using Update Manager?

I'm not sure what happens to ndiswrapper if you upgrade - but presumably it doesn't behave itself.

Unfortunately, if you have upgraded, I suspect the remnants of ndiswrapper and blacklisting drivers has presumably made a bit of a mess.

I believe the native Linux drivers now work (although Network Manager doesn't) - so that is an option too.  Perhaps try Wicd - or use command line.

These may help: 
[http://ubuntuforums.org/showthread.php?t=716670](http://ubuntuforums.org/showthread.php?t=716670)
[http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/](http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/)

---

### Post by silent the spy on 2008-06-29
> **ugm6hr said:**
> How did you upgrade?  Fresh install or upgrade using Update Manager?


Upgrade through Update Manager. Rest of system works fine, apart from the occasional freeze/complete lock up

> 
I'm not sure what happens to ndiswrapper if you upgrade - but presumably it doesn't behave itself.

Unfortunately, if you have upgraded, I suspect the remnants of ndiswrapper and blacklisting drivers has presumably made a bit of a mess.

I believe the native Linux drivers now work (although Network Manager doesn't) - so that is an option too.  Perhaps try Wicd - or use command line.

These may help: 
[http://ubuntuforums.org/showthread.php?t=716670](http://ubuntuforums.org/showthread.php?t=716670)
[http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/](http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/)

[/quote]

Thanks I'll try them

---

### Post by silent the spy on 2008-07-02
Late reply, sorry :)

tried it, got this far. On the first part I had to add a T to defaul as it wouldnt save. I also did not have the RTL8187 driver installed to remove in the first place. Nightmare but then you remember what im like ;)

```
john@charlie:~$ sudo gedit /etc/defaul/NetworkManager

** (gedit:15316): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

** (gedit:15316): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

** (gedit:15316): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
john@charlie:~$ sudo gedit /etc/default/NetworkManager
john@charlie:~$ sudo gedit /etc/default/NetworkManagerDispatcher
john@charlie:~$ sudo gedit /etc/network/interfaces
john@charlie:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@charlie:~$ sudo ndiswrapper -i Netrtuw.inf
driver netrtuw is already installed
john@charlie:~$ sudo ndiswrapper -m
module configuration already contains alias directive

john@charlie:~$ sudo moprobe ndiswrapper
sudo: moprobe: command not found
john@charlie:~$ sudo modprobe ndiswrapper
john@charlie:~$ sudo gedit /etc/modules
john@charlie:~$ sudo /etc/init/d/networking restart
sudo: /etc/init/d/networking: command not found
john@charlie:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       /etc/network/interfaces:26: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:26: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                                                                                                      [fail]
john@charlie:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by goforlinux on 2008-07-02
wireless always seems to have probs with ubuntu thank god mine works :)

---

### Post by silent the spy on 2008-07-02
I wish i'd asked on here what wi fi to buy instead of going to pc world in the UK

doh!!!!!!!

---

### Post by silent the spy on 2008-07-11
I guess im up **** creek with out a paddle?

---

### Post by silent the spy on 2008-09-16
this has really disappointed me, im still stuck on shitty Microsoft.  Is it 2008 or 1808? like why cant it just work!
:(:(:(:mad:

---

### Post by timcredible on 2008-09-16
if it worked before your upgrade, then you probably upgraded the kernel, which means you have to re-install your wireless driver for the new kernel.  this is because ndiswrapper is a hook into the kernel - so if you change kernels, you have to re-install the hook.  you can test this by picking your old kernel from the grub list when the machine boots.  if the old kernel still works with wireless (assuming you haven't messed with the ndiswrapper stuff), you can either just use the old kernel or re-install your wifi driver.

---

### Post by silent the spy on 2008-09-16
I cant select the old kernel. I get a GRUB list but last time I tried it either loaded normal and no change or it said it wasnt there.

Like I said in the top post I tried everything that I tried before here [http://ubuntuforums.org/showthread.php?t=654694](http://ubuntuforums.org/showthread.php?t=654694)

---


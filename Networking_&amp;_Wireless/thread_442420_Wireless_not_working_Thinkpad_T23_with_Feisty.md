---
title: "Wireless not working: Thinkpad T23 with Feisty"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by pixolet on 2007-05-13
Hi - can't find anything exactly like this on the forum, so hopefully someone can help.

I have a Thinkpad T23 with built-in wireless (PrismII chipset) which worked fine with Dapper and Edgy, but will not work with Feisty. The device driver looks loaded fine, and NetworkManager gives me the option to connect to a wireless network, but it never works.

More worringly,when I go into manually configure the network, it thinks that wlan0 is a wired network. I suspect that this is the problem.

Any ideas? I can't work out how to get it to see that wlan0 is a wireless network. I have tried manually adding the wireless options into /etc/network/interfaces but it's made no differerence.

Wired networking works fine.

Thanks

---

### Post by chili555 on 2007-05-13
Which device driver is it loading? How about letting us see:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism2
```Thanks.

---

### Post by pixolet on 2007-05-16
Thanks chili555.

The results of the lsmod commands are:
```

# **lsmod | grep orinoco**
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco

# **lsmod | grep hostap**
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  2 ieee80211,hostap

# **lsmod | grep prism2**
prism2_pci             70784  0 
p80211                 31884  1 prism2_pci

```Is it a problem  that all are being loaded?

---

### Post by chili555 on 2007-05-16
Yessir! Please *sudo gedit /etc/modprobe.d/blacklist* to add the following line:```
blacklist  prism2_pci
```Save and close gedit. Reboot and all should be well.

---

### Post by pixolet on 2007-05-17
:KS
Thanks! Spot on.

---

### Post by moa999 on 2007-05-19
Same issue here...
Worked perfectly on a T23 under Dapper... upgraded to Feisty to get NTFS-3G support.

I blacklisted prism2_pci and this is what I now get.....

mark@T23:~$ lsmod | grep orinoco
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco
mark@T23:~$ lsmod | grep hostap
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap
mark@T23:~$ lsmod | grep prism2

Wireless driver now shows up and I can see a few open networks
However when I type in my network and Hex key it does nothing

and the network icon shows "Manual Configuration" but no status or information.

Any other suggestions much appreciated


0--------------
Further background:
lspci -v | less  shows this as the relevant controller

02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Actiontec Electronics Inc Unknown device 0406
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at ec000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

---

### Post by Gatchaman on 2007-05-24
> **chili555 said:**
> Yessir! Please *sudo gedit /etc/modprobe.d/blacklist* to add the following line:```
blacklist  prism2_pci
```Save and close gedit. Reboot and all should be well.

Wow, thanks for the help.  My Thinkpad T30 built-in wireless in now working!

---

### Post by jlh on 2007-05-25
I've got this same problem on a Thinkpad T30 on Feisty.  Here's my output from the lsmod commands:

$ lsmod | grep orinoco
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco

$ lsmod | grep hostap
hostap_pci             56848  2 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap

$ lsmod | grep prism2
prism2_pci             70784  0 
p80211                 31884  1 prism2_pci

The difference from the thread above is in the lsmod | grep hostap output.

How do I edit the blacklist file?

Thanks.

---

### Post by chili555 on 2007-05-25
Exactly the way I stated above:> Please sudo gedit /etc/modprobe.d/blacklist to add the following line:
```
blacklist  prism2_pci
```

Save and close gedit. Reboot and all should be well.

---

### Post by jlh on 2007-05-25
Nope.  I did the edit.  At that point, the machine was able to scan for wireless networks, and it :(displayed them with signal strength bars.  I tried connecting to my encrypted network, but could not.  I tried to configure it manually.  Still could not connect.  Plus the scan feature has ended.  I am not even seeing the networks that I saw before.

---


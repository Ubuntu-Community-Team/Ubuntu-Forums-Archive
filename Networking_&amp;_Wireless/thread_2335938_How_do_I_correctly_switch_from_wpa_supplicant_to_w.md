---
title: "How do I correctly switch from wpa_supplicant to wicd"
date: 2016-09-02
forum: Networking &amp; Wireless
---

### Post by numeric-overflow on 2016-09-02
I had my previous wireless config setup in wpa_supplicant.conf and /etc/network/interfaces  however now that I've installed and am using wicd, how do I safely "remove"  the old settings in wpa_supplicant?  Can someone tell me what the  contents of those two files should look like for a basic setup if I'm  using wicd?  Should I clear out the wpa_supplicant.conf file contents? Essentially, I want to remove wpa_supplicant.conf completely from the mix and want wicd to completely control the wireless IP/Settings/Etc.

 I've got all the settings in wicd  (actually via wicd-curses) and can see them when I exit the app and go  back into it, so I'm fairly confident wicd is setup OK.  Here's my  issue/concern:  as a test, since I have a static IP, I configured  wpa_supplicant.conf with an IP address of *.*.*.108, and wicd with  *.*.*.107 IP address and after the reboot, the pi is accessible via the  *.108 address, so I'm hesitant to clear out wpa_supplicant as that one  seemed to take effect.  

The machine is remote and administered via SSH, so I'd rather do this correctly instead of having to crawl into the attic to reset the wireless connection.  Everything I've found while searching online seems to assume you've started fresh with wicd so doesn't mention what steps need to *switch* from wpa_supplicant to wicd.

Thanks!

---

### Post by Keith_Helms on 2016-09-03
> **numeric-overflow said:**
> I had my previous wireless config setup in wpa_supplicant.conf and /etc/network/interfaces  however now that I've installed and am using wicd, how do I safely "remove"  the old settings in wpa_supplicant?  Can someone tell me what the  contents of those two files should look like for a basic setup if I'm  using wicd?  Should I clear out the wpa_supplicant.conf file contents? Essentially, I want to remove wpa_supplicant.conf completely from the mix and want wicd to completely control the wireless IP/Settings/Etc.

 I've got all the settings in wicd  (actually via wicd-curses) and can see them when I exit the app and go  back into it, so I'm fairly confident wicd is setup OK.  Here's my  issue/concern:  as a test, since I have a static IP, I configured  wpa_supplicant.conf with an IP address of *.*.*.108, and wicd with  *.*.*.107 IP address and after the reboot, the pi is accessible via the  *.108 address, so I'm hesitant to clear out wpa_supplicant as that one  seemed to take effect.  

The machine is remote and administered via SSH, so I'd rather do this correctly instead of having to crawl into the attic to reset the wireless connection.  Everything I've found while searching online seems to assume you've started fresh with wicd so doesn't mention what steps need to *switch* from wpa_supplicant to wicd.

Thanks!

Networking under 16.04 is giving me some problems, so I set up a second system, installed wicd and uninstalled network manager.  On that system **/etc/network/interfaces** looks like this
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback
```

The **interfaces.d** subdirectory it is pulling in is empty.  **/etc/wpa_supplicant.conf** does not even exist on the system.  I'd move it to my home directory for safekeeping and if everything works using wicd, then delete it.

---

### Post by numeric-overflow on 2016-09-05
Thanks!@Keith_Helms - [**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1871481")That seems to make wicd work for me.

---


---
title: "Broadcom BCM 4311 and BCM 4401-B0 card"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by Scott_Smith on 2014-11-02
Brand new to Linux and Ubuntu.  I am having internet connection problems.  My attempts to resolve them myself has appeared to make things worse.  Any help someone is willing to give me would be greatly appreciated.  

I recently obtained an old laptop.  Dell Insprion 1501.  It has Ubuntu 14.04 installed on it.  I brought it home and found that the wireless card is not enabled.  I was able to plug in an ethernet cable and get internet access.

A lspci command reveals:
05:00.0 Network controller:  Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller:  Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

[B]From there I made things worse.  

I then went to System Settings and found Software & Updates.  I went to the Additional Drivers tab and searched for drivers.  A Broadcom driver was found and I told it to install.[/B]

After that, I can't get either the Ethernet connection or Wireless connection to work at all.  

After being unable to figure how to uninstall the driver, I tried a new installation of Ubuntu 14.04.  I am still experiencing the same issues.  

Would anyone be willing to instruct me or point me to a posting that will instruct me on a way to resolve this?  I thank you in advance for any help you can provide.

---

### Post by Bucky Ball on 2014-11-02
*Thread moved to **Networking & Wireless**.*

Welcome. Please open a terminal and paste this in:

```
sudo lshw -C network
```

That will tell us what you have installed and if it is the correct driver the card. That will tell us where to start sniffing.

In additional drivers, what driver did you install (what is it called in Add. Drivers?).

---

### Post by westie457 on 2014-11-02
Open a terminal copy and paste the following commands.```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

---

### Post by Scott_Smith on 2014-11-02
Thanks for taking up the cause.  The response I got to the lshw -c network command was:

 *-network               
       description:Network controller
       product: BCM4311802.11b/g WLAN
       vendor: BroadcomCorporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list
       configuration:driver=wl latency=0
       resources:irq:18 memory:c0200000-c0203fff
  *-network UNCLAIMED
       description:Ethernet controller
       product:BCM4401-B0 100Base-TX
       vendor: BroadcomCorporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pmbus_master cap_list
       configuration:latency=64
       resources:memory:c0300000-c0301fff

I don't recall the exact name of the driver (and didn't think to screenshot it).  I recall it said something about being a broadcom driver.

---

### Post by praseodym on 2014-11-02
Is the firmware installed? If yes, uninstall the other driver and clean-up the system:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Errors can be ignored. Reboot then.

---

### Post by Scott_Smith on 2014-11-02
Westie,

The response I got to sudo apt-get install b43-fwcutter firmware-b43 installer

Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package firmware-b43
E: Unable to locate package installer

Remember, I have no internet connection at all at this point.

When I tried sudo modprobe b43, there was no response, its like the terminal is working but can't finish.

---

### Post by praseodym on 2014-11-02
Its ok, install this one instead:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Continue then with the uninstallation as described above. You'd better c/p those lines ;)

---

### Post by praseodym on 2014-11-02
Sorry, I did not notice that there is no connection at all at the moment. Download that file directly from here:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
and install it as described.

---

### Post by Bucky Ball on 2014-11-02
Take note, helpers: OP has no internet connection. The commands given need internet.

```

capabilities: pmmsi pciexpress bus_master cap_list
configuration:driver=wl latency=0
```

No firmware.

@OP: Is there anyway you can get a cable to this machine? Would make life a LOT easier. Or the cable is not working either? And also:

---

### Post by Scott_Smith on 2014-11-02
I cut and past the instructions and that got my wired connection back.  Thank you very much for that.  I will no install the new dirver

---

### Post by Scott_Smith on 2014-11-02
Ok I have installed the broadcom firmware.  What may I do next?

---

### Post by Bucky Ball on 2014-11-02
Not sure if it's all there, but reboot (with the cable out as it will default to that).

If still no joy, try [THIS]("http://ubuntuforums.org/showthread.php?t=2251132&p=13158273&viewfull=1#post13158273"), posted on the last page. If still no joy, post back the result of that command again and let's see if you actually have the firmware there.

---

### Post by Scott_Smith on 2014-11-02
I rebooted and then ran

sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
It installed and I rebooted again.

Wi-Fi networks is now an option but it is grayed out, I cannot select it.

---

### Post by Scott_Smith on 2014-11-02
> **Bucky Ball said:**
> Not sure if it's all there, but reboot (with the cable out as it will default to that).

If still no joy, try [THIS]("http://ubuntuforums.org/showthread.php?t=2251132&p=13158273&viewfull=1#post13158273"), posted on the last page. If still no joy, post back the result of that command again and let's see if you actually have the firmware there.

I tried THAT again.  Here is what I got:
:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 206 not upgraded.


sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory

Same response for each subsequent command.  Does that give any indication about where to go from here?

---

### Post by Scott_Smith on 2014-11-02
I tried

sudo apt-get install firmware-b43-installer
And now I have the wireless working (as well as the wired connection you fixed earlier).  Thanks for all the help.  

If I may, is there anything else I need to do?

---

### Post by Bucky Ball on 2014-11-02
If it's still working in 24 hours, no.

You can mark the thread as solved with the second link in my signature when you're happy. Good luck and nice experimenting. ;)

---

### Post by Scott_Smith on 2014-11-02
Thanks so much for you kind help.

---


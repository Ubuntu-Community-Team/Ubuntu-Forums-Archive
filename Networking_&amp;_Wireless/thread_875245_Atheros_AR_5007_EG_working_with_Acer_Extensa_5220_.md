---
title: "Atheros AR 5007 EG working with Acer Extensa 5220 and Heron 8.04.1"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by merllin on 2008-07-30
How I got Acer Extensa 5220 wifi working with Ubuntu 8.04.1 :):) :)
-----------------------------------------------------------

Disable Atheros Drivers under System Administration Hardware Drivers

Reboot

Open terminal and type
sudo apt-get install build essential
to get tools to compile driver

Go to the following web address in your browser..

Read:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Read:
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

Download from:
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6)
I downloaded 24 July instance (latest image at time of writing)

I followed instructions at:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

I rebooted after modprobe command in the instructions, re-issued the modprobe command and the ifconfig ath0 up command once again after reboot and everything came alive. (Check by typing iwconfig .. as per instructions at madwifi wiki)

Note that when the instructions tell you to issue a command "as root" in Ubuntu this means you need to prefix the line with 'sudo' (and then enter your login password)

Wireless was then available and if you click network icon on top RHS menu bar you can "Connect to Other Wireless network" if your network isn't listed. My Signal strength meter works and I used it to optimise the orientation of my Wi-Fi aerials.

This post was done wirelessly.

Extensa 5220 seems to work quite well with Ubuntu and much quicker to boot than Vista..

I can't help thinking that Linux will only really become mainstream once these hardware config issues are easy for the novice, but then at least you have a lot of freedom to modify the system I suppose!

Good luck!

---

### Post by merllin on 2008-08-04
Some problems on re-boot..
Solved by re-issuing the following commands:
sudo modprobe ath_pci
sudo ifconfig ath0 up
iwconfig

If anyone can suggest how to avoid this it would be highly appreciated! Ta!

---

### Post by bogdan.veringioiu on 2008-09-08
Hi.

The solution worked for me also.

Just a few things to mention:

-The steps that I took were: remove kernel modules with the provided script inside the driver archive, after this I issued "make", "sudo make install", and then a "sudo modprobe ath_pci". After reboot, the NetworkManager was listing the wireles networks.

-Wireless led is not working.

-It was working also after reboot...I will give some other tests.

Regards.

---

### Post by mihaiadrian on 2008-11-26
> **merllin said:**
> Some problems on re-boot..
Solved by re-issuing the following commands:
sudo modprobe ath_pci
sudo ifconfig ath0 up
iwconfig

If anyone can suggest how to avoid this it would be highly appreciated! Ta!

Works for me to, thank you
I put sudo modprobe ath_pci in /etc/rc.local to avoid writing this command evrey time i reboot and it works

---


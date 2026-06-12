---
title: "ACER ASPIRE 1694 no network"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by Zhukov on 2005-05-31
A friend of mine bought an Aspire 1694 and I want to install Ubuntu on it, the installation is only possible with noacpi, pcmcia off, but now, although the eth1 is detected, thw wireless ipw2200 wasnt detected.
I've installed the firmware and now the eth0 (ipw2200) shows up but no network is detected.

With the cable he cannot connect. Even right after install. And during install both network cards are detected.

Help would be highly apreciated.

 ;-)

---

### Post by tread on 2005-05-31
This may seem a stupid suggestion, and it prolly is .. but I just want to make sure you covered all bases.
Did you go through System->Networking (I forget the exact location in the top menu .. its  in the rightmost dropdown menu) and try to set up the network there?  You will have to activate the interface, assign IP/choose DHCP etc. there ..

---

### Post by Zhukov on 2005-05-31
:D Lol :)
I did, yes I did.
I've also tryed to force acpi or remove noacpi from the menu.lst... but it hangs at Starting Ubuntu...


 ](*,)

---

### Post by Velrok on 2005-10-14
Same problem here. So I am using Ubuntu since 3 days I'am not never skillt. The etha1 witch is die Wired LAN Card gets no connection at all. I'm using an Netgeer Router so I tried getting the IP by DHCP and by setting ist statick nothig works. 

Ever hint would bee very usefull. But please mak shure its undestandable especialy for one who never realy use the terminal.

*hoping*

---

### Post by dave1111 on 2005-10-14
I had the same problem but wlan is working now.
You need to do several things.
First you have to get ACPI working. Download th custom DSDT for the ACER Aspire 1694 (I have the WLMi) from [http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php)
The compile the DSDT with the iasl from [http://developer.intel.com/technology/iapc/acpi/downloads.htm](http://developer.intel.com/technology/iapc/acpi/downloads.htm) 

compile:
iasl -tc dsdt.dsl

add to initrd:
echo -n "INITRDDSDT123DSDT123" >> /boot/initrd<...> # magic signature
cat DSDT.aml >> /boot/initrd<...>

Then you can boot without acpi=off but with noapic. But turn of starting of pcmcia at boot, because it will hang. Maybe you should copy the old initrd before appending the DSDT-table and insert an alternative grub-entry with the old initrd in case something goes wrong you can boot the old initrd.

Then you need the acerhk kernelmodule and new ipw2200 drivers and a new ieee80211-module. See [http://www.lirmm.fr/~yousfi/divers/acer/](http://www.lirmm.fr/~yousfi/divers/acer/) for more (2.2.1 for WLAN).
I had to use the option force_series=1680 unlike described in the link above where 1690 is used which didn't work. He had an older version of acerhk.

Without ACPI working the acerhk-module can't turn on the kill switch for wlan.

If you need more help just ask, it works great for me.

---

### Post by Zhukov on 2005-10-14
Ahh finally some activity here! :D Ill try this as soon as possible! Thanks!

---


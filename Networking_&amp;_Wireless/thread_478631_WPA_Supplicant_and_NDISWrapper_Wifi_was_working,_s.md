---
title: "WPA Supplicant and NDISWrapper: Wifi was working, stopped working after a reboot"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by andychaplin on 2007-06-19
Hi,

I have a Linksys WMP54G Wireless Card- PCI ID 14e4:4320. I have installed NDISWrapper using the official Linksys drivers.

I have blacklisted the bcm43xx driver.

I have installed WPA_Supplicant and correctly generated my PSK using "WPA_passphrase". I have added this information to /etc/wpa_supplicant.conf. (as per the HOWTO)

I have configured my /etc/network/interfaces file to call and load the wpa_supplicant.conf file upon boot-up and have correctly entered my IP, Subnet, ESSID etc into this file.

It all WORKED FINE until I rebooted my PC!!

Now it doesn't work at all.

Wlconfig shows my wifi card, but states that it is not connected to my Access point.

Can anyone suggest a reason why it should work first time (after following all the HOWTO's on this forum) and now not work after a reboot??

I was using the WEXT driver. But have also tried the NDIS driver to no avail.

I am using Ubuntu 7.04, hidden SSID, static IP and WPA-PSK TKIP.

Kind regards,

Andy

---

### Post by reckless2k2 on 2007-07-04
did you follow the ndiswrapper guide and add it to the startup process?

---

### Post by #Reistlehr- on 2007-07-04
run,

sudo depmod -a
sudo modprobe ndiswrapper

should be no output

i gotta run it everytime my laptop boots.

---

### Post by vertago1 on 2008-05-04
> **#Reistlehr- said:**
> run,

sudo depmod -a
sudo modprobe ndiswrapper

should be no output

i gotta run it everytime my laptop boots.

If you add ndiswrapper to a blank line in the file: /etc/modules you will no longer need to type that every time you reboot

---


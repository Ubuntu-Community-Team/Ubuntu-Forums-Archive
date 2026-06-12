---
title: "Can't boot to Ubuntu after configuring wireless connection"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by g0nzo on 2007-10-24
Hi,

I'm not sure what wireless card I have exactly, but Ubuntu says it uses Texas Instruments ACX 111 chipset. After installing Ubuntu 7.10, it correctly finds all wireless networks including mine.  Great.

My router uses WPA2 + text password. It works fine on Windows XP. I was trying to set DHCP + WPA2 for my network on Ubuntu, but it couldn't connect and the Network Tool stopped responding after I set WPA2. So I decided to reboot the system.

When booting again, it stopped when trying to start cups. Ok... CTRL+ALT+DEL and it starts to shutdown. But it stopped on wpa-supplicant and I had to use Reboot button. Just to make clear - the first booting after installation, when the wifi network was not configured, was successful.

I'm not sure how to shut down my wireless card in recovery mode, so I had to reinstall the system. Tried setting the wireless network again - exactly same thing happens.

How to shut down wireless card in recovery mode?
Do you guys have any idea what can be wrong? I could try to shutdown cups, but I don't think this is the problem here.

---

### Post by jaybee99 on 2007-10-24
> **g0nzo said:**
> Hi,

I'm not sure what wireless card I have exactly, but Ubuntu says it uses Texas Instruments ACX 111 chipset. After installing Ubuntu 7.10, it correctly finds all wireless networks including mine.  Great.

My router uses WPA2 + text password. It works fine on Windows XP. I was trying to set DHCP + WPA2 for my network on Ubuntu, but it couldn't connect and the Network Tool stopped responding after I set WPA2. So I decided to reboot the system.

When booting again, it stopped when trying to start cups. Ok... CTRL+ALT+DEL and it starts to shutdown. But it stopped on wpa-supplicant and I had to use Reboot button. Just to make clear - the first booting after installation, when the wifi network was not configured, was successful.

I'm not sure how to shut down my wireless card in recovery mode, so I had to reinstall the system. Tried setting the wireless network again - exactly same thing happens.

How to shut down wireless card in recovery mode?
Do you guys have any idea what can be wrong? I could try to shutdown cups, but I don't think this is the problem here.

boot from the live cd, mount your root directory, and edit the interfaces file e.g. 
```

sudo mkdir /mnt/linux
sudo mount -t ext3 /dev/hda1 /mnt/linux
sudo vi /mnt/linux/etc/network/interfaces
```

commenting out (with a hash) everything except 

auto lo
iface lo inet loopback

---

### Post by g0nzo on 2007-10-24
Thanks!!! It will be really helpful and speed up testing various settings.

And now how to correctly set my wifi network connection to use DHCP + WPA2? :)

---


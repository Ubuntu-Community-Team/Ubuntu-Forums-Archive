---
title: "[Pi Server 20.04] Headless WiFi Setup: Generating New Netplan YAML Config"
date: 2020-10-29
forum: Networking &amp; Wireless
---

### Post by eru2 on 2020-10-29
Hello all,

What I'm trying to do is have a headless pi easily swap between WiFi networks, SSID's will not be known in advance. The method I used to upon my first boot, using Ubuntu 20.04 server on a pi4B 4GB, is editing the `network-config` file in the boot partition of the microSD to include the wifi settings. Worked fine the first time.

What seems to be happening as part of its very first boot is it generates a .yaml file in `/etc/netplan/` with the wifi configuration entered in the boot partition's file.

But this only happens once.

So if you forget to change the file after flashing first, or did some work on the pi and need to move to another network, that file won't get replaced on subsequent boots, thus retaining the previous settings regardless.

The answer is to directly edit the yaml file. This poses a problem for a couple reasons. The SD cards will likely be edited on Windows in many instances and the `/` partition isn't readable because of the ext4 formatted partition.

Is there a way, from the boot partition, to force that yaml file to be generated on every boot and not just from the first boot? I did try deleting the yaml file in `etc/netplan` to see if that would force it but no go. 

A solution that's coming to mind is have a shell script run on boot up that would look for a new yaml file on boot in a mounted usb location, then replace the old one with that, but seems overly complicated for something that seems like it should be easier.

Thanks for reading,


Cheers!

---


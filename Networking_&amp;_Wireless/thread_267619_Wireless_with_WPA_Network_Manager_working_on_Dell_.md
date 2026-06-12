---
title: "Wireless with WPA Network Manager working on Dell laptop"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by GeoffB on 2006-09-28
Hey I just wanted to give my 2 cents for anybody using a Dell Laptop with the 1470 WLAN PCI card. I am an on again off again user of linux but have recently ran into Ubuntu after trying several other distros...This is by far the best distro yet. Anyway, I wanted to let you guys know what I did to get my wireless working with network manager and WPA.

My wireless card is a Dell 1470 WLAN PCI with a Broadcom 4319 chipset. The bcm43xx that comes with the distro does not work with the card so I blacklisted it and dl'ed the latest Windoze drivers from Dell and installed with ndiswrapper version 1.8 from synaptic.

Next I installed the latest libnl from svn. Then i ran apt-get build-dep wpasupplicant...however DO NOT install wpasupplicant from synaptic. Instead install the latest wpasupplicant from cvs...mine is 0.5.5. I will not go into specifics on how to download wpasupplicant from cvs as there are plenty af well written threads on how to do it already. [http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA) is the one that I used.

After you've installed that then you need to run apt-get build-dep network-manager...but do not install network-manager from synaptic, it did not work for me after several tries. Instead download network-manager from cvs, again refer to [http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA) for instructions on how to do this. 

After completing the few last steps in the above guide I performed a reboot. When I logged back in I clicked on the nm-applet in the taskbar and selected my wireless WPA network, i was prompted for my default keyring and VIOlA!!! I had wireless encrypted with WPA.

The only minor problem i have is the annoying prompt at login for the keyring password but I am well aware of everybody's complaints with this, hopefully it will be fixed soon. I hope this helps. This is not meant to be a step by step guide and I am no linux pro but I would be happy to help anybody with this chipset as there is not a whole lot about the 4319 on the forums.

I have finally gotten my Linux hating Dell laptop to completely work like it did with Windoze on it. DVD, wireless and acpi all working properly albeit a little buggy. Im so close to a Windoze free life. FINALLY!!! By the way my laptop is the Inspiron 2200 just for the record.

---


---
title: "nvidia driver -&gt; no internet, uninstall nvidia -&gt; internet"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Dreams on 2007-10-19
Hi

Just installed Gutsy, internet working perfect. Then installed NVidia driver using restricted driver management. Reboot, graphics all nice and fast, but no internet anymore. The ethernet card still shows up in IFCONFIG, but it has no IP address. 

Tried to find the cause, and uninstalled the NVidia driver, and my internet came back, working perfectly. I'm stumbled, don't have any idea how this could happen. In Ubuntu 7.4 internet worked perfectly good combined with NVidia driver.. :confused:

I tried 'enable roaming mode', DHCP, and even a static IP-address, 192.168.2.6, which should work in my network. All this didn't work.

The ethernet card is onboard card, don't know exactly which type. If you need more information, i will post it ASAP.

---

### Post by bclintbe on 2007-10-19
What you said got me thinking. I've already posted in a couple other threads and posted a bub (#154207) about also losing my wired internet... doesn't seem to wake up the onboard NIC when the computer boots up, since no LEDs even light up on the NIC. Then I realized, I have an nVidia card with the restricted drivers, and my NIC is nVidia when I checked it in the hardware profile. I wonder if the nVidia graphics drivers are screwing around with the nVidia NIC? Stranger things have happened. I'm going to uninstall the nVidia restricted driver, and then add anything I see to the bug report.

---

### Post by Dreams on 2007-10-20
I just did a complete reinstall, and exactly the same problem happened.

It seems i only get an IP6 address, and no IP4 address for some reason..
Anyone got any idea?

---

### Post by Dreams on 2007-10-22
I'll have to install Ubuntu 7.4 then.. :(

---


---
title: "ubuntu, 8.04 intel 2200bg"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by mr_spatel on 2008-05-13
Hi all new to ubuntu, got my 8.04 cd yesterday and installed it on my IBM r50e.  It found everything fine.  But have problem with the wireless card intel 2200bg.  It finds wireless networks, I added my settings in manually but I cannot connect to the internet?  any ideas?

The SSID is hidden, and using WPA-PSK with TKIP. The router is a netgear dg834gt

Also I cannot ping the router etc.

Please help thanks

---

### Post by helgman on 2008-05-13
First, make sure that your settings are right and that they correspond to the settings of the router. **ifconfig** might be a good start for IP-address, subnetmask and so on. (Are you using dynamic or static IP-settings?)

Next, make sure that you are associated with the access point. **iwconfig** is a handy tool here. (Look for "ESSID" and a MAC address  after "Access Point".)

I've never been to friendly with the Network Manager and I've found that I have to give the password a couple of times before the manager "gets it" (manages to associate with the AP). Tried it just now and it's work on the 4th try (with a similar setup as you are using).

Usually I use wpa_supplicant when I'm having trouble since it sometimes gives a hint as to what is wrong.

Regards,
Helgman

---

### Post by tlg on 2008-05-13
I use the Intel 2200bg card amonst others in several IBM T41, T42 laptops running Ubuntu 7.04, 7.10 and 8.04. I use WPA and WPA2 on a range of wireless routers including Billion, Asus, Netgear and DLink

After lots of difficulties with wireless networking, I finally discovered WICD at  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It replaces Network Manager and makes wireless and wired networking a breeze.

You might like to give it a try. It is easy to re-install Network Manager if you need to do so.

One other thing to try is to un-hide the SSID until you get it working. Some network cards don't handle hidden SSID well.

---

### Post by mr_spatel on 2008-05-13
hi guys / tlg

I cant download the wicd program from the link you gave me, this is the line to use to install it:

deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

but not net access from the laptop?

what can i do thanks

---

### Post by tlg on 2008-05-13
Apologies if this is already obvious, but that line is intended to add the wicd repository in the Synaptic Package manager rather than download an install file directly. The idea is to register the wicd repository, reload, then search for the wicd app and install using the Package Manager.

If you want to download a file to install from, you can download the .deb file from here:
[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

Save it to the Desktop and double click on it to launch the deb installer.

The Package Manager approach is generally preferable as it ensures that future updates to the app will be installed by the Update Manager.

---

### Post by mr_spatel on 2008-05-13
hi all guess what it is working, thanks for you help.

now need to get VPN access to my office working it is not easy to do,

---


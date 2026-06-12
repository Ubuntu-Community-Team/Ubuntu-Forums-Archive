---
title: "wpa_supplicant.conf gone in gutsy"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by logophobia on 2007-10-02
apparently wpa supplicant now starts up in gutsy without reading a config file, in feisty it used to read /etc/wpa_supplicant.conf, very nice if you wanted network-specific settings. It starts up like this now:
/sbin/wpa_supplicant -g /var/run/wpa_supplicant-global3 (from ps ax | grep wpa) not passing the -c option anymore.

also, its not in init.d anymore but is now controlled by ifupdown. I really need that config file, does anyone know a way to enable it. Ive been going through alot of shell scripts but I can't find an option to enable it. thnx.

---

### Post by kevdog on 2007-10-02
I thought you had to create the wpa_supplicant.conf file.

Im not using gusty, but can you check a few things for me:

wpa_supplicant --help  (is the -c command listed??)

What are the contents of this file:
/var/run/wpa_supplicant-global3

---

### Post by logophobia on 2007-10-03
> **kevdog said:**
> I thought you had to create the wpa_supplicant.conf file.

Im not using gusty, but can you check a few things for me:

wpa_supplicant --help  (is the -c command listed??)

What are the contents of this file:
/var/run/wpa_supplicant-global3

The -c option is there, I already checked. I never checked wpa_supplicant.conf in feisty, but existing docs indicate that it should be there, it never mentions creating one, just appending new options at the end. The file you asked is just a socket, its there but i can't open it.

What i am looking for is an relative easy way to add the -c option to wpa_supplicant when starting up. There are loads of shellscripts controlling it (in /etc/wpa_suplicant en /etc/network/*/wpa_supplicant) but I can't find anything there. It used to be in init.d, but that seems to have changed the last release.

---

### Post by predator29 on 2007-10-09
predator29@gemini:~ $ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
  wpa-driver wext
  wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0

---

### Post by luxor on 2007-10-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/122059](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/122059) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				wpa_supplicant is controlled by nm-applet/network-manager in Gutsy.  The /var/run/wpa_supplicant-global<#> file you see is the global ctrl interface that NM uses to communicate with wpa_supplicant.  You should also see a /var/run/wpa_supplicant<#> which is the local ctrl interface.  nm-applet passes the networks scanned and displays them, and you have the option to connect to one of the networks listed, and it will prompt you for authentication, and key management information.  It stores the authentication information in the keyring manager, and the network information in ~/.gconf/system/networking/wireless/networks/<network ssid>/%gconf.xml.  So the next time you connect to the same network, you use nm-applet to choose the network, and all this information is pulled, and voila.... you are connected (at least in theory).

If you want to use your own wpa supplicant conf file, and bypass NM, you need to take the following steps:
1)  create your wpa_supplicant.conf file
2)  right click the nm-applet icon, and un-check wireless network  
3)  make sure your wireless adapter module is loaded using sudo modprobe <module>
4)  use ifconfig to bring your interface up: sudo ifconfig <interface> up
5)  run your wpa_supplicant app like before

After all the bugs are out of nm and nm-applet, this should work more smoothly
Hope this helps

---


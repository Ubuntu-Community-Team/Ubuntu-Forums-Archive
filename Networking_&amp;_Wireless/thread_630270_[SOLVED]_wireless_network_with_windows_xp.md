---
title: "[SOLVED] wireless network with windows xp"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by enivrezvous on 2007-12-03
Hi all,

I'm trying to connect my two computers via wireless and am not having much success so far.  

Here's the setup: I have one computer running xp, one fesity, and no router.  The Windows machine has an internet connection through wired ethernet, and both have wireless cards.  I'm giving both machines static ip addresses (it seemed easier than setting up dhcp on windows) on the wireless network.  

ipconfig /all gives:

Windows IP Configuration

        Host Name . . . . . . . . . . . . : nexis
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Linksys Wireless-G PCI Adapter
        Physical Address. . . . . . . . . : 00-12-17-A0-9D-42
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-50-8D-7E-30-A4
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : xxx.xxx.xxx.xxx
        Subnet Mask . . . . . . . . . . . : 255.255.252.0
        Default Gateway . . . . . . . . . : 67.60.28.1
        DHCP Server . . . . . . . . . . . : 24.116.2.148
        DNS Servers . . . . . . . . . . . : 24.116.200.232
                                            24.116.2.34
        Lease Obtained. . . . . . . . . . : Monday, December 03, 2007 4:54:47 AM
        Lease Expires . . . . . . . . . . : Tuesday, December 04, 2007 6:06:24 AM

iwconfig wlan0 gives:

... hmmm, well I can't find any way to get the output from feisty (which has no internet, no floppy, no  cd burning software, and the flash drive isn't detected) to this compuer. The wireless card in the linux box is a marvell something-or-other and is loaded via ndiswrapper; no problems there.  The IP address (statically set) is 192.168.0.5, Subnet mask is 255.255.255.0, it's connected to the same essid as the windows machine, the mode is set to ad-hoc ... I hope that's enough info.

Both computers report being connected to the same essid, but I can't ping either one.  Any help would be greatly appreciated; I can't think of where to go from here.

---

### Post by enivrezvous on 2007-12-03
It appears now that windows can ping ubuntu, but not vice-versa :?

---

### Post by enivrezvous on 2007-12-08
Well, I got it up and running and am now writing this on ubuntu.  

There were a few issues: the first was that I couldn't get the network applet to correctly configure, so I just manually configured everything using iwconfig and ifconfig.  The second was a firewall on the other computer (darn mcaffee).  The last was that I needed a default gateway pointing to the xp computer.

---


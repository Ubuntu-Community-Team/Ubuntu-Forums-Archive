---
title: "Have Wireless but No Wired Connection"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by shuknjive on 2008-08-18
I just recently converted a Dell D600 to 8.04LTS with a fresh install. Upon startup, I had neither wired or wireless connection. After installing b43 driver and firmware (transferred from one computer to this one on a USB drive), I have wireless. Unfortunately, I still cannot connect to the internet using my wired connection. Any help? BTW, I'm a newbie, so any command line requests should be specific and well detailed.
I'm connected to a Belkin 4-port router - NAT firewall enabled, mac address filtering enabled, pinging disabled, WPA2 encryption enabled.
Wired NIC is a Broadcom BCM5705.

---

### Post by Sam Lars on 2008-08-18
Do you know if the wired connection works with another OS?  Is it enabled in the BIOS?

---

### Post by Iowan on 2008-08-18
Check [this]("http://ubuntuforums.org/showthread.php?t=890531") one. It's about two NIC's, but technique is the same - manually edit **/etc/network/interfaces** file.  More details available *_if_* you need them.  :)

---

### Post by shuknjive on 2008-08-18
the wired connection was working fine when the laptop was running XP.  It stopped working only after the conversion to 8.04LTS.

---

### Post by shuknjive on 2008-08-18
thanks Iowan for the link.  However, my knowledge of linux is very limited.  I understand that the etc/network/interfaces should be edited, but I don't understand how or what to edit (what to input that is).

---

### Post by bukwirm on 2008-08-18
Can you post your /etc/network/interfaces file?

Generally, you just need to add a line like "iface eth0 inet dhcp" (assuming you're using DHCP). It's a little more complicated if you're using a static IP address. Read the man page for interfaces for more information.

---

### Post by shuknjive on 2008-08-19
bukwirm:

Below is what is contained in my /etc/network/interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

The line you mentioned appears to be there.  BTW, sorry for the long delays in replies, but I can only do this after work - they haven't been enlightened by Linux yet.

---

### Post by bukwirm on 2008-08-25
Type the command "sudo lshw -C network" into a terminal; you should get a list of network cards installed in your computer and some information about them. Find the wired one and its logical name. Add the lines "auto *logical_name*" and "iface *logical_name* inet dhcp" to the /etc/network/interfaces file, then restart networking (with sudo /etc/init.d/networking restart).

---

### Post by shuknjive on 2008-08-29
Here is the output of the "sudo lshw -C network" command.  I've x-out my mac addresses for security reasons.  Also, what is odd that I have performed this command before and the onboard NIC has been identified.  Now it is saying that the product has an illegal vendor ID.  I'm really confused.  Furthermore, in the network tools (gnome-nettool 2.22.0) , I have a loopback interface (lo), an unknown interface (wmaster0), and a wireless interface (wlan0).  However sometimes it lists the onboard NIC (eth0) and another device listed as eth0(avahi).  Any help with this.  BTW, restarting the network using the "sudo /etc/init.d/restart networking" does not remedy the situation.

  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: ff
       serial: XXXXXXX
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.16 latency=255 link=yes maxlatency=255 mingnt=255 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: XXXXXXXXXXXX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.3 multicast=yes wireless=IEEE 802.11g

---

### Post by bukwirm on 2008-08-31
That's interesting...

Does the lshw command give the same output after you reboot?

---

### Post by shandiddy on 2008-09-19
I am also having a similar problem.  I was trying to get my logitech camera to work. i was installing some spca5xx and qc-usb packages and my wired connection stopped working.  The icon is the same when I click on the icon everything say the same things but it does not connect.  I put in the liveCD again and the internet works perfectly. 

how can I reinstall or revert back to my old setup?

---


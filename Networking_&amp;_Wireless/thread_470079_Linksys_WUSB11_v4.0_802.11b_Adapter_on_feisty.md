---
title: "Linksys WUSB11 v4.0 802.11b Adapter on feisty"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by MightyMouse on 2007-06-10
Dear all,

I have a Linksys WUSB11 v4.0 802.11b Adapter that used to work with ndsiwrapper.
I have done a fresh installation of Feisty and now the adapter is no longer seen as wlan0, but it is at least present as a USB device. Anybody with a suggestion how to get this particular USB-wirelss device working?

Here some information on the device when plugged in

----------------------------------------------------------------------------------------
anja@anja-maus:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

----------------------------------------------------------------------------------------
anja@anja-maus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
----------------------------------------------------------------------------------------
anja@anja-maus:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:50:bf:e3:15:ec arp 1
----------------------------------------------------------------------------------------
One problem, I don't have a LAN connection, thus apt0get or synaptic are no options. If I need additional programs I have to use the old-fashioned tar.gz files.

Cheers, Anja

---

### Post by markeee on 2007-07-20
hej Anja,

I have the same problem-im running Kubuntu 7.04 fisesty with the exact same Linksys WUSB11 V4, lsusb shows it like with you but lshw -c networjk does not show it and nor does ifconfig/iwconfig



do you have any other drivers installed with ndiswrapper?!

---

### Post by MightyMouse on 2007-07-23
Hi Markeee,
I only saw today that you sent a request. In fact I have solved the problem, the adapter is now working fine.
I am currently at work, but I will post a walk through here as soon as I have time.

---

### Post by MightyMouse on 2007-07-24
Ok, this is what I did.

I installed ndiswrapper, someone suggested it had to be version 1.8, but it might work with 1.9 too(?).
I don't remember the site I got this information from, so you have to trust me on this.

Next I did the usual routine (there are many instructions on the forum, you probably already know how to do it).
I used the Windows driver WUSB11v4, in the inf-file it says 
DriverVer   = 05/13/2004, 3.110.0513.2004

You should then see the wlan0, probably already your AP, but you can't connect.

Now you un-install the gnome network-manager and instead install wifi-radar. And then suddenly it worked!

If you need more details I have to dug into my bookmarks and Log-book and check the version of the packages I installed. But I think that the trick was the removal of the network-manager, because one can see that the wlan0 is already up and running and is also seeing the AP, it just can't connect.

Cheers, Anja

---


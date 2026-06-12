---
title: "Linksys Wusb11 linux driver problems"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by Dcastle on 2006-08-28
Hi, I just purchased a Linksys USB WiFi 802.11b adapter. I found a linux driver for it, and downloaded it, Now I am trying to install the .tar.gz
I tar xvzf it then cd into the directory, after I do ./Configure and I am asked if I want to build 4 different things. I choose to build the PRISM2.5 USb driver, then I get this:

Linux source directory [/usr/src/linux]: 
Linux source tree  is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

 


I navigated to /usr/src and the last part of the directory is missing "/linux" what do I do? Help is appreciated.

---

### Post by az on 2006-08-28
You already have the driver in Ubuntu.

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28prism2%29](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28prism2%29)

You need to configure the /etc/network/interfaces by hand because of the way the driver was written.

---

### Post by Dcastle on 2006-08-28
Thanks, but in the list of supported devices, it lists 3 linksys devices as WUSB11 v1.1 , 2.5, and v3. I have the v4, Will the driver still work? and if so how do I go about configuring the /etc/network/interfaces? thanks. Dcastle

---

### Post by az on 2006-08-29
> **Dcastle said:**
> Thanks, but in the list of supported devices, it lists 3 linksys devices as WUSB11 v1.1 , 2.5, and v3. I have the v4, Will the driver still work? 

I dunno.  Is it the same chipset?  When you plug it in for the first time afte ryou boots, what does
tail /var/log/messages
say?  (post the output - that will tell you what the kernel does with the hardware and you will see what device it is)

> **Dcastle said:**
> 
and if so how do I go about configuring the /etc/network/interfaces? thanks. Dcastle

sudo gedit /etc/network/interface

and edit the wlan0 stanza to look like this:

auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_enc on
 wlan_ng_key0 aa:bb:cc:11:22
 wireless-essid myhouse


where "myhouse" is your essid and your WEP is aabbcc1122.  You need to seperate the characters with colons in the file like that.

---

### Post by Dcastle on 2006-08-30
Plugged it on and used tail /var/log/messages , it gave me this: 

 tail /var/log/messages
Aug 30 11:18:38 localhost gconfd (david-4767): starting (version 2.14.0), pid 4767 user 'david'
Aug 30 11:18:39 localhost gconfd (david-4767): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 30 11:18:39 localhost gconfd (david-4767): Resolved address "xml:readwrite:/home/david/.gconf" to a writable configuration source at position 1
Aug 30 11:18:39 localhost gconfd (david-4767): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 30 11:18:39 localhost gconfd (david-4767): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 30 11:18:39 localhost gconfd (david-4767): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 30 11:18:47 localhost gconfd (david-4767): Resolved address "xml:readwrite:/home/david/.gconf" to a writable configuration source at position 0
Aug 30 11:23:55 localhost exiting on signal 15
Aug 30 11:23:56 localhost syslogd 1.4.1#17ubuntu7: restart.
Aug 30 11:28:09 localhost kernel: [  780.094503] usb 1-2: new full speed USB device using uhci_hcd and address 2




Ok, changed the file, except my network is currently non existing due to some router problems [http://www.ubuntuforums.org/showthread.php?p=1441629#post1441629](http://www.ubuntuforums.org/showthread.php?p=1441629#post1441629) . So is there anyway that I can test to see if its working such as check for other networks in my area etc. The device still hasnt shown up in system>administration>networking. Thanks for your help

---

### Post by Dcastle on 2006-08-30
Thanks for all your help. Today I gave up and turned it in for a wired router and a cable. It saved me half of my money and worked out of the box! Imagine that!

---


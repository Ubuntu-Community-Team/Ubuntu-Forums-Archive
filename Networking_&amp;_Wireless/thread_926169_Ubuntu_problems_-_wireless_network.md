---
title: "Ubuntu problems - wireless network"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by horgzter on 2008-09-21
Hi,

I have just installed ubuntu (Hardy version if I understand correctly) and have a problem with my network. It works, but really slow. I can have my other computer reboot and upload a new webpage before mine can even load the webpage. 

I'm new to Ubuntu and the unix platform in general, so if someone can help me with this in a step-by-step form, I appreciate it!
I have only tried the wireless, since my port on the computer is physically damaged. 

What is my first thing to check for?

The specs below are from the computer brochure: 


 Built-in 56K, .V92 fax modem (MDC (AC’97)
 10/100Mpbs LAN (Broadcom BCM4401

Integrated wireless LAN (WLAN) solution 802.11 b/g
speeds up to 54Mbps
industry standard wireless LAN security support

---

### Post by horgzter on 2008-09-22
Hi, 

I am trying using the procedure in this linK:
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

In the last steps I get this error:

command:
 sudo ndiswrapper -i "/home/jtwe/amsn_received/Wireless Lan/Rt2500.inf"


Error message
couldn't open /home/jtwe/amsn_received/Wireless Lan/Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

Contents of line 219

# load inf and split into different sections.
sub read_sections {
    my $filename = shift;
    open(INF, $filename) or die "couldn't open $filename: $!";

    my $name = "none";
    @{$sections{$name}} = ();
    while (my $line = <INF>) {
	# convert from unicode
	$line =~ s/\xff\xfe//;
	$line =~ s/\0//g;



What kan I do?

---

### Post by Crafty Kisses on 2008-09-22
I'd like to see the results of this command:
```
lshw -C network
```

---

### Post by Kevbert on 2008-09-22
> **horgzter said:**
> Hi, 

I am trying using the procedure in this linK:
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

In the last steps I get this error:

command:
 sudo ndiswrapper -i "/home/jtwe/amsn_received/Wireless Lan/Rt2500.inf"


Error message
couldn't open /home/jtwe/amsn_received/Wireless Lan/Rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


What kan I do?

You're trying to install a Ralink RT2500 driver instead of the Broadcomm B43 driver.  You might want to take a look at this [COLOR="Red"][post.]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")[/COLOR]

---

### Post by horgzter on 2008-09-22
> **Codename said:**
> I'd like to see the results of this command:
```
lshw -C network
```

 *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wmaster0
       version: 01
       serial: 00:14:a5:06:df:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.0.155 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 02
       serial: 00:40:ca:d5:ab:4c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

---

### Post by Kevbert on 2008-09-23
OK.  You are trying to install the file RT2500.inf which is correct for your wireless adapter.  Have you copied this file from a windows disk (or downloaded it) to your /home/jtwe/amsn_received/Wireless Lan/ directory ?

---

### Post by horgzter on 2008-09-23
> **Kevbert said:**
> OK.  You are trying to install the file RT2500.inf which is correct for your wireless adapter.  Have you copied this file from a windows disk (or downloaded it) to your /home/jtwe/amsn_received/Wireless Lan/ directory ?

Hi,

It is a downloaded zip-file unpacked to the directory in the address.

Thank you for the help so far!

---


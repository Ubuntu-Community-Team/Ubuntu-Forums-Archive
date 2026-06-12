---
title: "wireless not working with Lucent/Orinoco PCMCIA card"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by ramblasur on 2008-04-20
Hi,

I have an old Thinkpad T21 with a Lucent PCMCIA wireless card. It works fine on Windows and it used to work fine on Mandrake 8.1. I've just installed Xubuntu 7.10 (and wiped out Mandrake), and the wireless is not working.

I read many threads with similar problems and tried everything with no luck. A brief overview:

a) the orinoco drivers are loaded (actually lsmod|grep orinoco lists as a result orinoco, orinoco_cs, hermes, psmcia and pcmcia_core)

b) probable conflicting drivers are not loaded (I blacklisted prism2, prism2_cs, prism2_pci, hostap and hostap_pci)

c) ifconfig shows the interface eth0 with correct MAC address but no ipaddress. It also shows another interface eth0:avah with the same MAC address.

d) iwconfig shows the interface eth0 with correct ESSID and correct MAC address for the access point.

e) I use WEP and the encyption key is correct, I tried many combinations with and without dashes, etc

f) dhclient fails to get an ip address ("No DHCPOFFERS received.")

g) I tried static IP but didn't work either.

h) ping 192.168.1.1 doesn't get a response from the access point.

i) it didn't work with network-manager, so I killed it and tried manually modifying /etc/network/interfaces with no luck. I also tried wicd with no luck.

j) I added the following options to the kernel loading: noapic nolapic acpi=off apm=on. It didn't solve the problem.

Can someone help me with this problem? I want my wireless working!

Thank you.

---

### Post by chili555 on 2008-04-20
I would un-blacklist the whole hostap group, reboot and then post:```
iwconfig
```This should be as easy as:```
sudo iwlist eth1 scan
```Learn your case-sensitive ESSID```
sudo iwconfig eth1 essid <what_u_found>
sudo iwconfig eth1 key 012345xyz
sudo dhclient eth1
```Let us know what you get.

---

### Post by ramblasur on 2008-04-20
Thank you for your response.

I unblacklisted the hostap drivers and rebooted.

Then I entered the commands you indicated:

```



#iwconfig

lo        no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"myessid"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:39:C2:A5:4E   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:0123-ABCD-EF   Security mode:open
          Power Management:off
          Link Quality=36/92  Signal level=-58 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# iwlist eth0 scan
eth0      Failed to read scan data : Resource temporarily unavailable


# iwconfig eth0 essid myessid
# iwconfig eth0 key 0123abcdef
# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:02:2d:1d:a4:1a
Sending on   LPF/eth0/00:02:2d:1d:a4:1a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

It's still not working. Any ideas?

---

### Post by chili555 on 2008-04-20
Please try:```
**sudo** iwlist eth0 scan
```I'm a bit concerned by 'Resource temporarily unavailable.'

Your *iwconfig* shows a healthy interface that is ready to connect! Is your network 'open' and not 'restricted' for sure?

---

### Post by ramblasur on 2008-04-20
I issued the commands as root (first I typed "sudo su"), so "sudo iwlist eth0 scan" is basically the same.

I also tried both open and restricted with the same result.

Thank you for your efforts. What can 'Resource temporarily unavailable.' mean? Can I try something else?

---

### Post by chili555 on 2008-04-20
> What can 'Resource temporarily unavailable.' mean?I don't know yet I am Googling as we speak! Could we please take a look at:```
sudo lshw -C network
```Maybe we can see something interesting about your Prism.

Another strategy is to eject and reinsert the card while you watch:```
sudo tail -f /var/log/messages
```

WEP hex keys are either 10 or 26 characters. Is that what you have?

Finally, once in a while, cards will respond better to:```
sudo ifup eth0
```

It is a bit puzzling that this is eth0, usually eth0 is ethernet and eth1 is wireless. Is the ethernet jack disabled or defective?

---

### Post by ramblasur on 2008-04-20
Regarding the scan not working, I read somewhere that this type of cards don't support it, so probably we don't have to worry about that now.

Regarding eth0 and not eth1, this laptop has no wired ethernet port (nor wired ethernet card) so it makes sense.

Now, this is the result for the lshw command:

```

$ sudo lshw -C network
  *-network               
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:02:2d:1d:a4:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.16 link=no multicast=yes wireless=IEEE 802.11b

```

This is what happens when I eject/reinsert the card:

```

$ sudo tail -f /var/log/messages

Apr 20 19:10:09 castalia kernel: [  206.820000] pccard: card ejected from slot 0
Apr 20 19:10:09 castalia kernel: [  206.840000] hermes @ 00010100: Card removed while issuing command 0x0002.
Apr 20 19:10:09 castalia kernel: [  206.840000] eth0: Error -19 disabling MAC port
Apr 20 19:10:22 castalia kernel: [  218.960000] pccard: PCMCIA card inserted into slot 0
Apr 20 19:10:22 castalia kernel: [  218.960000] pcmcia: registering new device pcmcia0.0

```

And this is what happens when I run the ifup command:

```

$ sudo ifup eth0
ifup: interface eth0 already configured

```

It looks like this is going to be hard. Thank you for your support!

---

### Post by chili555 on 2008-04-21
> *-network               
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:02:2d:1d:a4:1a
       capabilities: ethernet physical wirelessDo you have *two* wireless cards, one built-in and one PCMCIA? Is the built-in not working correctly? Can you disable it in the BIOS to see if we get a better result?> I read somewhere that this type of cards don't support itMy Prism/orinoco card is a champ scanner, works quite well with Kismet, etc.> It looks like this is going to be hard.My specialty!

---

### Post by ramblasur on 2008-04-22
> 
Do you have two wireless cards, one built-in and one PCMCIA? Is the built-in not working correctly? Can you disable it in the BIOS to see if we get a better result?


I have only one wireless card and it is PCMCIA. There is no internal card (wireless nor wired ethernet). The only internal thing is a 56K modem. Also, the wireless PCMCIA card is the only PCMCIA card inserted.

The MAC address shown in the second entry is correct. The description shown in the first entry corresponds to the card I have. Do you think the driver is attached to the first entry and the eth0 interface to the second? Is there a way to check this?

Thank you!

---

### Post by chili555 on 2008-04-22
Well, it's surely a possibilty that someone is bound to the wrong thing! Let's see:```
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```Let's see if they are consistent with each other and we'll cautiously amend if necessary.

---

### Post by ramblasur on 2008-04-23
Here we go:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:2D:1D:A4:1A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

eth0:avah Link encap:Ethernet  HWaddr 00:02:2D:1D:A4:1A  
          inet addr:169.254.2.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 b)  TX bytes:592 (592.0 b)

```

```

$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x104c:0xac1b (yenta_cardbus)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:02:2d:1d:a4:1a", NAME="eth0"

```

Thank you.

---

### Post by chili555 on 2008-04-23
Bad news. It looks perfect! That's bad news because I don't see an 'Ah haaa!' that we can fix.

Please try:```
iwconfig eth0 key 0123abcdef restricted
sudo dhclient eth0
```This thing ought to jump out of bed and connect before you pour your coffee!

I don't have any ideas left.

---

### Post by ramblasur on 2008-04-24
Well, still no luck.

```

& sudo iwconfig eth0 key 0123abcdef restricted
& sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:02:2d:1d:a4:1a
Sending on   LPF/eth0/00:02:2d:1d:a4:1a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I tried both restricted and open, key with dashes and without, with quotes and without, etc.

You've been great chili, thank you. I might try another distro.

If anyone else has any idea please let me know!

---

### Post by ramblasur on 2008-05-13
Just for the record, I installed Fedora Core 6 and the wireless card works fine.

---

### Post by ramblasur on 2008-05-20
Again, for the record, the wireless card DOES NOT WORK with Fedora 9. At this point I think it is not a distribution issue but a kernel issue.

I've read in other threads about doing a firmware upgrade on the card. I couldn't find information on how to do it. Any help?

The wireless card is Lucent Gold PC24E-H-FC.

Thank you.

---

### Post by ramblasur on 2008-05-23
I found the solution to this problem in this thread:

[http://sourceforge.net/mailarchive/forum.php?thread_name=47A8BD2A.5040608%40research.telcordia.com&forum_name=orinoco-users](http://sourceforge.net/mailarchive/forum.php?thread_name=47A8BD2A.5040608%40research.telcordia.com&forum_name=orinoco-users)

Basically, there was an IRQ conflict between the infrared (IRDA) port and the PCMCIA card. This is not handled correctly in the pcmcia driver, so the solution is to either remove the irda module (nsc_ircc) or modify /etc/pcmcia/config.opts so that a specific irq is not used (adding the line 'exclude irq 3').

I'm happy to report that my card is working now!

I've seen many threads reporting this problem, please help spread the word.

---


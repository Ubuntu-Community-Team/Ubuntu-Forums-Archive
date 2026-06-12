---
title: "Static IP address changes"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by infoseeker on 2006-12-28
My onboard LAN connection was taken out by lightning a few days back and I installed a PCI LAN card.  My problem is that my static IP address (in 192.168..... range) for some reason changes to an IP address in the 169.254..... range on bootup, without any action from me, and I then need to reconfigure it back when it does.

I disabled whats left of the onboard connection in the cmos setup. The replacement LAN card is listed as eth1.

Any suggestions as to what is happening here?

---

### Post by bernied on 2006-12-28
This is probably a dhcp assigned IP. You probably had your old eth0 set up in /etc/network/interfaces but that setup won't apply to eth1. Have a look at that file.

You can also do this in a GUI (somewhere)

---

### Post by infoseeker on 2006-12-28
cat /etc/network/interfaces
```

iface eth1 inet static
address 192.168.*.*
netmask 255.255.255.0

auto eth1

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto lo
```

No mention of eth0 there. In fact I deleted the file (after backing it up) and rebooted and reconfigured the network (eth1) as a test, but no change.
Thanks anyway.

---

### Post by bernied on 2006-12-28
Are you sure it's eth1?

What is the output from 'ifconfig'?

---

### Post by infoseeker on 2006-12-29
```
# ifconfig
eth1      Link encap:Ethernet  HWaddr -----------
          inet addr:192.168.*.*  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:2 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000
          RX bytes:359781 (351.3 KiB)  TX bytes:37464 (36.5 KiB)
          Interrupt:217 Base address:0x9000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13892 (13.5 KiB)  TX bytes:13892 (13.5 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:348840 (340.6 KiB)  TX bytes:25308 (24.7 KiB)

```
No listing for eth0 there. :(

Oh and BTW this incorrect IP address appears before KDE starts up (when in recovery mode)

In a shell under KDE if I type```
# /etc/init.d/networking restart
``` I get >  * Reconfiguring network interfaces...                                                                                            SIOCSIFADDR: File exists
Failed to bring up eth1.

but the network IP address changes to the required 192....... address nonetheless.

---

### Post by bernied on 2006-12-29
Too weird. 
Any clues in /var/log/messages or dmesg (grasping at straws now)
Something other than /etc/init.d/networking is messing with you.

Have you installed anything else network related? You haven't got a wireless card installed by chance?

Another vague thought - do you need to specify a default route for DNS? 
What's in your /etc/resolv.conf ?
There should be at least one nameserver line with the IP address of your router.

EDIT: maybe this doesn't apply to you - is your default route through ppp0 ? Sorry 'tis beyond me.

Sorry I can't be of more help.

---

### Post by infoseeker on 2006-12-29
Everything worked perfectly well until the onboard got zapped.  I'll somehow try and configure the eth1 card as eth0 and see what happens.

---

### Post by infoseeker on 2006-12-29
Found something interesting.  When I go to 'Menu---> System---> Kinfocenter' I get this which I find very weird :confused:
eth1 appearing twice but with different IP address but same HW address.

---

### Post by bernied on 2006-12-29
Can you change this in Menu -> System Settings

---

### Post by dbott67 on 2006-12-29
The 169.254.x.y addresses are part of the [APIPA]("http://www.tcpipguide.com/free/t_DHCPAutoconfigurationAutomaticPrivateIPAddressingA.htm") address range (used when an unconfigured NIC can't reach a DHCP server).

-Dave

---

### Post by infoseeker on 2006-12-30
> Can you change this in Menu -> System Settings

'Menu --> System Settings --> Network Settings' acts very weirdly.  The PC always boots up with the '169.254.......' IP address. I select 'configure interface', enter the admin password, enter configure interface (shows up as eth1 with no eth0 listed as eth0 is disabled in bios), enter the new (required) IP address and select ok and everything looks normal, but on clicking 'apply', the IP address displayed changes back to the '169.254.......' address.  If I then click apply the '169.254.....' address is saved (no further option to apply), and the network starts up (knemo still works fine :)).  I then change the IP address to the one I want (192.168.....) and click apply and the required IP address is now saved correctly.

I found the quickest way to do all this is to create 3 aliases in .bashrc, viz.:

alias n1='sudo /etc/init.d/networking stop'
alias n2='sudo ifconfig eth1 192.***.***.***'
alias n3='sudo /etc/init.d/networking start'

Is there somewhere where detected hardware is saved for future use? a database maybe? I'd like to kill the presence of the original eth0 in the system somewhere/somehow.
Using the Kubuntu 6.06 Live CD lists the new PCI card as eth0 and there is no indication of the disabled onboard ethernet port.

---

### Post by infoseeker on 2006-12-31
> Is there somewhere where detected hardware is saved for future use? a database maybe? I'd like to kill the presence of the original eth0 in the system somewhere/somehow.
I thought I'd have a last attempt before .......... ?  reinstall ?

---

### Post by infoseeker on 2006-12-31
> Is there somewhere where detected hardware is saved for future use? a database maybe? I'd like to kill the presence of the original eth0 in the system somewhere/somehow.
I thought I'd have a last attempt before .......... ?  reinstall ?

EDIT - Double Post:confused:

---


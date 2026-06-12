---
title: "Networking between Win 2K and Ubuntu"
date: 2005-07-04
forum: Networking &amp; Wireless
---

### Post by Sethleben on 2005-07-04
I have a cable modem connection that is connected directly to a Linksys router (IP 192.168.1.1). The router has connections to two PCs, one of which is running Windows 2000. This PC has two ethernet adapters, and the one connected to the router has IP 192.168.1.100. I am trying firstly to connect the second network adapter to my Ubuntu system using a crossover cable, and secondly to share the internet connection between the two computers. 

I have set the IP of the second  network adapter to 192.168.0.1 and the eth0 IP to 192.168.0.2, with Gateway 192.168.0.1. 

I have plugged the crossover cable into both computers, but neither card is lighting up, and the Win 2K machine claims that the LAN 2 connection is unplugged. 

What could be causing this problem? I know the cable not to be faulty, as I have used it before. 

Furthermore, once the two computers are able to see each other, does anyone know how to set up internet connection sharing (ICS) with a Linux machine? Does it work the same as with another Windows machine?

Any help would be most appreciated.

Cheers.

---

### Post by Lunde on 2005-07-04
[QUOTE=Sethleben]I have a cable modem connection that is connected directly to a Linksys router (IP 192.168.1.1). The router has connections to two PCs, one of which is running Windows 2000. This PC has two ethernet adapters, and the one connected to the router has IP 192.168.1.100. I am trying firstly to connect the second network adapter to my Ubuntu system using a crossover cable, and secondly to share the internet connection between the two computers. 

I have set the IP of the second  network adapter to 192.168.0.1 and the eth0 IP to 192.168.0.2, with Gateway 192.168.0.1. 

I have plugged the crossover cable into both computers, but neither card is lighting up, and the Win 2K machine claims that the LAN 2 connection is unplugged. 

What could be causing this problem? I know the cable not to be faulty, as I have used it before. 

Furthermore, once the two computers are able to see each other, does anyone know how to set up internet connection sharing (ICS) with a Linux machine? Does it work the same as with another Windows machine?

Any help would be most appreciated.

Cheers.[/QUOTE]
 Does'nt this router already share the Internet and LAN? No use for the X-cable.

Internet connection sharing works the same way as with 2 windows machines, you just have to configure the linux to get dhcp from Win2000. I think it's the same as with XP..

---

### Post by Sethleben on 2005-07-05
The reason for not adding the Linux box onto the router is purely one of practical considerations: the router is a long way away from the Win 2K machine and I don't really want to lay down huge lengths of cable when I can easily just plug the Linux box into the 2K box directly.

However, as yet I still haven't even managed to get Windows 2000 to recognise that the second cable is plugged in.

Is there anything obviously wrong with the network settings I described in the previous post? I have never networked a Linux box directly to another PC using a crossover cable before, so I'm not sure if I've got it all right.

Cheers.

---

### Post by Lunde on 2005-07-05
[QUOTE=Sethleben]The reason for not adding the Linux box onto the router is purely one of practical considerations: the router is a long way away from the Win 2K machine and I don't really want to lay down huge lengths of cable when I can easily just plug the Linux box into the 2K box directly.

However, as yet I still haven't even managed to get Windows 2000 to recognise that the second cable is plugged in.

Is there anything obviously wrong with the network settings I described in the previous post? I have never networked a Linux box directly to another PC using a crossover cable before, so I'm not sure if I've got it all right.

Cheers.[/QUOTE]
 can you post the output of: 
$ ifconfig
$ gedit /etc/network/interfaces

Here's some more info on networking:
[http://www.ubuntuforums.org/showthread.php?t=25557](http://www.ubuntuforums.org/showthread.php?t=25557)

---

### Post by Sethleben on 2005-07-05
[QUOTE=Lunde]can you post the output of: 
$ ifconfig
$ gedit /etc/network/interfaces

[/QUOTE]

seth@Speshal:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:4F:10:86:C3
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe10:86c3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:16 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15640 (15.2 KiB)  TX bytes:15640 (15.2 KiB)


gedit /etc/network/interfaces   appears to be completely blank.

Cheers for the help,

Sethleben

---

### Post by Lunde on 2005-07-05
Can you ping yourself on 192.168.0.2 in Ubuntu?

Have you set the eth0 to active? 
$ ifconfig eth0 up

Add your interface to /etc/network/interfaces and then bring it up. 
More info here:
[http://www.linuxquestions.org/questions/archive/63/2005/04/3/315175](http://www.linuxquestions.org/questions/archive/63/2005/04/3/315175)

---

### Post by Sethleben on 2005-07-05
[QUOTE=Lunde]Can you ping yourself on 192.168.0.2 in Ubuntu?
[/QUOTE]

Yes, I can.

> 
Have you set the eth0 to active? 
$ ifconfig eth0 up


I set it to active using System | Administration | Networking


> 
Add your interface to /etc/network/interfaces and then bring it up. 


Here it is:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```

However, the two computers still cannot talk.

Cheers,

Sethleben

---

### Post by Lunde on 2005-07-05
If they are in the same IP-range, netmask and on the same gateway. What about Workgroup and Domain?

Maybe you have to set up Samba filesharing first. I connected directly with no problems. 
[http://ubuntuguide.org/#changecomputerdomainworkgroup](http://ubuntuguide.org/#changecomputerdomainworkgroup)

Are you sure that ping from outsied is allowed? Do you have a software firewall? that blocks ping on any of the computers?

---

### Post by Imerio on 2005-07-05
sounds like one of your two NICs might be disabled. You've confirmed the Ubuntu box NIC is enabled. Might be worth ensuring the second NIC on your Windows box is enabled.

---

### Post by Sethleben on 2005-07-05
[QUOTE=Imerio]sounds like one of your two NICs might be disabled. You've confirmed the Ubuntu box NIC is enabled. Might be worth ensuring the second NIC on your Windows box is enabled.[/QUOTE]

Yeah I had just thought perhaps I should check. I'm going to plug the straight cable from the router into NIC #2 on the Win 2K box now rather than NIC #1 and see what happens.

---

### Post by Sethleben on 2005-07-06
I plugged my internet connection into NIC #2 on the Win 2K box (the one that was previously connected to the Linux box) and the light on the connector lit up, showing that the connection was active. 

Furthermore, as I think I mentioned previously, when I plugged the straight cable from the router directly into the NIC on the Linux box and changed the settings on it to DHCP I was able to get an internet connection with the Linux box. 

Yet, when I plug the straight cable back into NIC #1 on the Windows box and then connect the crossover cable between NIC #2 and the Linux box, both act as if there is no cable plugged in at all.

I did restore the eth0 settings back to what they were originally (i.e. not DHCP), and made sure that the Windows settings were also back to how I described them earlier, but still nothing when I boot both PCs up.

Any ideas?

Cheers,

Sethleben

---

### Post by Imerio on 2005-07-06
So, ignoring settings for the moment, if you connect cable from router to either of  Windows NIC1 or Windows NIC2 they activate. And if you connect same cable from router to Linux NIC, that activates. You then leave this cable connected from router to Windows NIC1 but now connect cross-over cable between Windows NIC2 and Linux NIC and these latter two NICs do NOT activate.

I would check that you've not mixed your cables incase your router supports NDIX on LAN ports (swap the cables - see what occurs). Or you don't have a cross-over cable (!) or your cable is faulty perhaps?

---

### Post by Sethleben on 2005-07-07
[QUOTE=Imerio]So, ignoring settings for the moment, if you connect cable from router to either of  Windows NIC1 or Windows NIC2 they activate. And if you connect same cable from router to Linux NIC, that activates. You then leave this cable connected from router to Windows NIC1 but now connect cross-over cable between Windows NIC2 and Linux NIC and these latter two NICs do NOT activate.
[/QUOTE]

Correct.

> 
Or you don't have a cross-over cable (!) or your cable is faulty perhaps?


Pretty sure that neither of these is the problem - the crossover cable was working fine recently.

> 
I would check that you've not mixed your cables incase your router supports NDIX on LAN ports (swap the cables - see what occurs). 


I'm going away tomorrow for two weeks, but when I return I may investigate the NDIS settings and also read up the details of the router.

Cheers,

Sethleben

---

### Post by Imerio on 2005-07-10
Sorry, I meant to write MDIX, the ability for a LAN switch port to autodetect the sense of the LAN (uplink etc.) - just in case you got your cables swapped.

---


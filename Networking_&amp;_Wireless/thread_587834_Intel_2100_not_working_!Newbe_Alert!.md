---
title: "Intel 2100 not working !Newbe Alert!"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Britax on 2007-10-23
Hello!
I just started using Ubuntu, and have about zero experience with Linux so please, help..

My Wireless networkcard do not work.. and I have no idea why.

The card is on a Dell Inspiron 8600, and is a PRO/Wireless LAN 2100 3B Mini PCI Adapter.

My wired network card work flawless..

---

### Post by dagowop on 2007-10-23
Could you paste in the result when you run iwconfig.  Also make sure you have a wireless client installed like kwlan.  Also maybe paste in a result from running lspci.  

[http://ubuntuforums.org/showthread.php?t=473873](http://ubuntuforums.org/showthread.php?t=473873)

Another option is to go to intel's site and see if they have linux drivers for download.

In my experience if the card shows up in iwconfig it's a configuration problem.

---

### Post by Britax on 2007-10-23
This is what i get!

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Jensen AirLink 7954"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:78:EC:D7:4C   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

Any thoughts?

---

### Post by Britax on 2007-10-23
lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by Lambert on 2007-10-23
What happens when you type the following at the terminal?

```

sudo dhclient eth1

```

The device and driver look to be working at some level if not completely. Your device is associated with an AP. Currently you don't have an IP assigned. Are you using encryption. A quick way to test things and narrow down the area of trouble is to start with encryption off to verify everything is working then add encryption back into your network.

---

### Post by Britax on 2007-10-23
To be honest I do not know how to go on..

Tried to install Kwlan, but got this error: Conflicts with the installed package 'dhcdbd'

---

### Post by Lambert on 2007-10-23
> **Britax said:**
> To be honest I do not know how to go on..

Tried to install Kwlan, but got this error: Conflicts with the installed package 'dhcdbd'

Keep coming here. It could be something simple or something a little complicated. You'll get help.

So go back to my last post. What happens if you type the command I gave and what type of encryption are you using?

Usually when you can associate to an AP, the problem is in the encryption. To test this I suggested turning encryption off and connecting to narrow down what's happening, then add it back into the equation. If you can not turn encryption off, then we'll just have to work from there.

---

### Post by Britax on 2007-10-23
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:3e:dd:9f
Sending on   LPF/eth1/00:0c:f1:3e:dd:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.38 -- renewal in 42148 seconds.


But where can i find settings for encryption, in windows I had a program, here in ubuntu I cant find anything related to the wireless connection..

---

### Post by Lambert on 2007-10-23
According to this output after running dhclient. You are now connected. Open up a browser and see if you can visit a web page.

---

### Post by Britax on 2007-10-23
Hmm, yes, Now it works... but I don't know why it suddenly is ok.

But who cares! It's working!

Thank you for your time!

---

### Post by Britax on 2007-10-23
On thing!

Is there anyway to see signalstrenght etc?

---

### Post by Lambert on 2007-10-23
> **Britax said:**
> Hmm, yes, Now it works... but I don't know why it suddenly is ok.

But who cares! It's working!

Thank you for your time!

I find that networkmanager is buggy. You were connected to the router but it didn't receive the configuration information with ip/dns etc...

> **Britax said:**
> On thing!

Is there anyway to see signalstrenght etc?

I don't use network manager but you should see something on the panel showing internet connection. Right click and choose the option that looks to show connection information.

---

### Post by JoJerome on 2007-10-23
I've been in a very closely related boat with a friend's Dell Inspiron 6000 and an Intel 2200bg wifi device.

Been working on it for days here...
[http://ubuntuforums.org/showthread.php?p=3587124#post3587124](http://ubuntuforums.org/showthread.php?p=3587124#post3587124)

Just tried the dhclient test here, although I'm not near a wifi access point...

```

~$ sudo dhclient eth1
[sudo] password for dave:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:97:ce:e8
Sending on   LPF/eth1/00:12:f0:97:ce:e8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Can someone tell me if this means wifi is on, active, and looking for an AP? Because it sure looks like it to this hopeful newbie's eyes! Is there anything else I can check before hitting the hotspot tomorrow? Tomorrow being the deadline before proving to the user how wonderful Linux is or reinstalling Window$ for him.

Thanks,

- Jo

---

### Post by Lambert on 2007-10-24
JoJerome-

When connecting to a network the steps are to

1. First associate with a router
2. request and recieve network parameters

Running the commnad dhclient eth1 is manually running step 2 in the equation. With out knowing if you are associated to a router i can't tell entirely what's going on but the possible causes are.

1. you are not associated to the router so there is no path for dhcp to submit a request and receive information from the router.
2. If you are associated to a router and get that output, usually there is a problem with encryption.

So from this point I suggest the following.

run the following command

```

sudo iwconfig eth1 essid ________

```

In the blank insert the ssid of the router you're trying to connect to. This should set up association.

Then run the dhclient command again. If you get no dhcpoffer again then run this command and post output here. Include in your post what type of encrytion you have set up on your router along with wireless device and driver you're using.

```

sudo iwconfig

```

---

### Post by JoJerome on 2007-10-24
Thanks Lambert - I'm definitely noting all the help on securing my home network should I ever use my wireless router again.

Although, if the user will be primarily using wifi to connect at public hotspots, is there any configuration needed? I'm too poor to have ever owned a laptop myself but isn't the idea that it's looking for an 'open' signal such as one you'd find at the local coffee/internet joint?

- Jo

---

### Post by elbono on 2007-11-03
Hey I'm having the same problem but worse, I posted up on  this thread but i didn't get a solution [http://ubuntuforums.org/showthread.php?t=584737&highlight=2100]("http://ubuntuforums.org/showthread.php?t=584737&highlight=2100")
maybe you could help me lambert, you seem to know all!!!

the output from iwconfig is```
eoin@Willo-The-Whisp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

and for lspci it is ```
eoin@Willo-The-Whisp:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

and when i runsudo dhclient eth1 i get ```
eoin@Willo-The-Whisp:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6071
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

I'm totally stumped, I have even reinstalled the linux-ubuntu-modules package to no effect

Please help me, I am totally lost

---

### Post by Lambert on 2007-11-03
> **elbono said:**
> Hey I'm having the same problem but worse, I posted up on  this thread but i didn't get a solution [http://ubuntuforums.org/showthread.php?t=584737&highlight=2100]("http://ubuntuforums.org/showthread.php?t=584737&highlight=2100")
maybe you could help me lambert, you seem to know all!!!



Far from knowing all :neutral:  I learn a lot from the forum and helping others.

In your case it doesn't look like the driver is loaded.

Run these two commands.

```

sudo lshw -C network

lsmod | grep ipw

```


when you run the lsmod command you should see output showing ipw2100 and ieee80211. If not then try this command then run iwconfig to see if eth1 shows up now.

```

sudo modprobe ipw2100

```

I found my ipw2100 and the firmware was very buggy with ubuntu, kept getting firmware errors. I stopped using it and plugged in my atheros pcmcia card.

---

### Post by elbono on 2007-11-04
Thanks for the help, 

here is the output for sudo lshw -C network
 > eoin@Willo-The-Whisp:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:27:12:2f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.36 latency=32 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=34 mingnt=2


and for  lsmod | grep ipw
>  eoin@Willo-The-Whisp:~$ lsmod | grep ipw
ipw2100                71344  0 
ieee80211              34248  1 ipw2100


and nothing happens when I run sudo modprobe ipw2100, and eth1 still doesn't show up from iwconfig, how do I reinstall the ipw2100 driver and firmware? I really appreciate all the help.

---

### Post by alex.de on 2007-11-25
> **elbono said:**
> Thanks for the help, 

here is the output for sudo lshw -C network
 

and for  lsmod | grep ipw


and nothing happens when I run sudo modprobe ipw2100, and eth1 still doesn't show up from iwconfig, how do I reinstall the ipw2100 driver and firmware? I really appreciate all the help.

Same thing here. I really need help. I'm on Gutsy.

---


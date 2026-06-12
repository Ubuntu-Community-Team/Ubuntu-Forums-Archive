---
title: "help me am new to Ubuntu"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by D330 on 2008-08-31
i just downloaded Ubuntu and installed it. Am having trouble connecting with wireless internet. I have a D-Link DWL- 122 wireless adapter, and it doesn't work. I have been reading on how to fix it, but i am really confused. If someone can give me a detailed explanation on how to fix it i would really appreciate it.

---

### Post by D330 on 2008-08-31
bump 

can anyone help??

---

### Post by tamoneya on 2008-08-31
can you tell us the output of these commands:```
sudo lshw -C network
ifconfig
lspci
```

Then we can help you move forward on getting things working.

Also please do not bump a post for 24 hours.

---

### Post by D330 on 2008-08-31
sorry for the bump. This is what i got 

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by tamoneya on 2008-08-31
you seem to be typing it in wrong.  It is a capital C and terminal is case sensitive.  Can you try to copy out the line that says exactly what you typed as well as the output.  That way I can spot any mistakes.

---

### Post by D330 on 2008-08-31
ok is this it?

 *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:5f:5f:ef
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 8b
       serial: 00:40:d0:64:2e:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.104 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wlan0
       serial: 00:0d:88:7e:83:e4
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by tamoneya on 2008-08-31
okay i dont see it anywhere in there.  Lets check to see if it isnt getting detected for some reason.  make sure it is plugged in and run these two commands:```
lsusb
dmesg | tail
```

---

### Post by anvec on 2008-08-31
Sorry for geting into this conversation, but it is the same problem I am having, maybe you can help two newbbies to ubuntu/linux at the same time...I have a Linksys USB wirelles adapter model WUSB54G v.2 which I cant make it work. I am posting the answers to the questions you had for the other  

sudo lshw -C network

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:50:fc:fb:5a:aa
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.68 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:50:fc:fb:5a:aa  
          inet dirección:192.168.1.68  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::250:fcff:fefb:5aaa/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:35389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25685 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:38922321 (37.1 MB)  TX bytes:3576813 (3.4 MB)
          Interrupción:17 Dirección base: 0xb800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1936 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:96800 (94.5 KB)  TX bytes:96800 (94.5 KB)
lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 02)

lsusb

Bus 005 Device 003: ID 03e0:6830  
Bus 005 Device 002: ID 13b1:000a Linksys 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg | tail
[   37.376360] Bluetooth: RFCOMM socket layer initialized
[   37.376381] Bluetooth: RFCOMM TTY layer initialized
[   37.376384] Bluetooth: RFCOMM ver 1.8
[   39.819655] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   39.819673] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.819707] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   41.525868] NET: Registered protocol family 17
[   46.496070] NET: Registered protocol family 10
[   46.496563] lo: Disabled Privacy Extensions
[   56.788036] eth0: no IPv6 routers present

HEEEEEEEEELP!!!! Thanks!!!!!

---

### Post by D330 on 2008-08-31
ok ran those 2 commands and got this:

danny@danny-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
danny@danny-laptop:~$ dmesg | tail
[   50.512631] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[   50.512636] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   50.512690] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   78.715629] NET: Registered protocol family 10
[   78.716251] lo: Disabled Privacy Extensions
[   78.717067] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   91.872742] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   91.873430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   95.250836] NET: Registered protocol family 17
[  110.933577] eth0: no IPv6 routers present

---

### Post by anvec on 2008-08-31
I got it, it took all afternoon but I finally got the wireless adapter running.

Here it is how I did it....

1.- Downloaded a .zip file with the driver (as if it were in Windows) from the wireless adapter manufacturers page...in my case Linksys.
2.- Right-click the .zip icon and choose the "Extract Here" option.
3.- Got to System/Administration and choose Windows Wireless Drivers
4.- When the application starts, choose the "Install new controller" button
5.- The application will ask for a .inf file, so you should go to the newly extracted folder, and look for the appropiate .inf file for your device.
6.- On the Network Manager (topm right corner of your screen, where two small screens are) you should now be able to see the wireless connections you have nearby.
7.- Choose yours and connect!!!!

---

### Post by mikeruck on 2008-09-01
Thanks, but my problem is i cannot connect to the internet so i dnt kno how i can download the drivers from their page.

---

### Post by Bucky Ball on 2008-09-01
That is fantastic news, Anvec.

---

### Post by overdrank on 2008-09-01
> **Bucky Ball said:**
> That is fantastic news, Anvec.

Hi and Anvec is not the OP and can not mark it as solved, :)
Edit I see you edited before my post

---

### Post by Dougie187 on 2008-09-01
@mikeruck:
You will probably need to hardline your computer and download them. Or download them somewhere else and drop them onto a usb stick or something to transfer them over.

---

### Post by Bucky Ball on 2008-09-01
haha, yea, I was getting confused overdrank! lol And Dougie187 beat me to what I was going to say! :)

---

### Post by mikeruck on 2008-09-01
ok thanks.

---

### Post by mikeruck on 2008-09-01
sry bout the trouble but i have one more question. do i need to download my wireless routers drivers? or wut drivers do i need to download? i think you said network adapter drivers, but wut is that and how can i find out which one i have? 

thanks in advance.

---

### Post by Dougie187 on 2008-09-01
you don't want your wireless router drivers, mainly because they don't have any. Thats called firmware. But you want the drivers for you wireless network adapter. One question that i have though.

In post six you gave the output of
```
lshw -C network
```
and it details that you have an intel pro wireless 2200 card, which has built in support in ubuntu. So I was curious if there was any reason why you are trying to get a dlink usb wireless adapter to work.

Anyways, you can most likely find the drivers on the dlink website, which is [www.dlink.com](www.dlink.com)

---

### Post by mikeruck on 2008-09-02
im not sure which network adapter i have how can i find out? i have a gateway laptop model-4026zc it is all stock exept for my harddrive. i doesnt make sense to me that in windows it fins my network that we have set up and that it finds the router and lets me connect but in ubuntu is does not find anything?? i am kinda confused with this lol. if anybody could walk me through how i could fix this i would really appreciate it.

thanks in advance

---

### Post by Bucky Ball on 2008-09-03
Not sure if this is any good. That card should work out of the box. It could be this simple:

Open a terminal and type this:
[B]
dmesg | grep ipw2200[/B]

If there are signs of a kill switch, go here:

[http://ubuntuforums.org/showthread.php?t=765319](http://ubuntuforums.org/showthread.php?t=765319)

Kill switch on? Not sure what laptop you're using but this could get you closer. This link gives you more information about he kill switch codes and key combinations to switch it off:

[http://debianletters.blogspot.com/2008/02/acpi-and-wifi-card-intel-prowireless-on.html](http://debianletters.blogspot.com/2008/02/acpi-and-wifi-card-intel-prowireless-on.html)

---


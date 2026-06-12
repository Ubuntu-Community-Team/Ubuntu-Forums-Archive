---
title: "Internet not working"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Blobface on 2010-05-19
I have installed Ubuntu 10.04 alongside windows proffesional as a dual boot system. for some reason the internet in Ubuntu does not work even though it does in Windows. It says it is connected to the ethernet but the internet wont work.
 
does anyone know what the problem is?
 
I am completely new to ubuntu so you will have to explain things in a very simple way

---

### Post by kingpoiuy on 2010-05-19
Go to your terminal (Applications Menu) and type ```
ifconfig
```
Tell us what you have for your IP address (if there is one), or better yet copy and paste the whole thing (might be hard without internet access).

---

### Post by ajgreeny on 2010-05-19
Wired, wireless?  Much more info needed, please, about your hardware, then we can get trying various things.

In the meantime can you post the output from these 4 commands in terminal, one at a time.
```
lspci
ifconfig
iwconfig
sudo lshw -C network

```

---

### Post by Blobface on 2010-05-19
thanks for the replys
 
while I do those commands i'll tell you about my system (which is about 5-6 years old)
 
Pentium 4 2.8ghz
1gb ram
200gb hard drive (split 185gb for windows and 15gb for ubuntu)
256mb  geforce grafics card 
Belkin F5D7000uk version 1133uk (which i cant get the driver working for but i have read online that a lot of people are having trouble with it)
connected to a belkin 54g modem/router
 
the wireless card has not been detected so I have connected my computer to the router with a network cable. This connection has been detected but the internet does not work, even though both ways work in windows.

---

### Post by Blobface on 2010-05-19
[FONT=Times New Roman][SIZE=3]lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ifconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ ifconfig[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:11:2f:0b:89:2b  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: fe80::211:2fff:fe0b:892b/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:14 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:30 errors:0 dropped:5 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:1881 (1.8 KB)  TX bytes:5139 (5.1 KB)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Interrupt:19 Base address:0xe400[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:18 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:1462 (1.4 KB)  TX bytes:1462 (1.4 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]iwconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ iwconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]eth0      no wireless extensions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wlan0     IEEE 802.11bg  ESSID:off/any  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Power Management:off[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]          [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Sudo lshw –c network[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ sudo lshw -c network[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network:0             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: SiS900 PCI Fast Ethernet[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Silicon Integrated Systems [SiS][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 4[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:00:04.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: eth0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: 91[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 00:11:2f:0b:89:2b[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       size: 100MB/s[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capacity: 100MB/s[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.4 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       resources: irq:19 ioport:e400(size=256) memory:febfb000-febfbfff memory:febc0000-febdffff(prefetchable)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  *-network:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Network controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: BCM4306 802.11b/g Wireless LAN Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 9[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:00:09.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: 03[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: driver=b43-pci-bridge latency=64[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       resources: irq:17 memory:febf8000-febf9fff[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  *-network DISABLED[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Wireless interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: wlan0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 00:30:bd:fe:98:9a[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: ethernet physical wireless[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE]

---

### Post by NeoQBirdie on 2010-05-19
My wireless internet isn't working in Ubuntu 10.04 either, but I've gotten around it for now by just plugging in my internet cable directly into my router. This is what I get when I type ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:19:b9:6c:c0:54  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe6c:c054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44545567 (44.5 MB)  TX bytes:5837996 (5.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

When I try to find my wireless network, it just lists that it's disconnected.

---

### Post by Blobface on 2010-05-20
I have also tried booting up from the cd in the trial version but it still doesnt work

---

### Post by Blobface on 2010-05-20
this is what I get if I ping [[COLOR=#000000]www.google.com[/COLOR]]("http://www.google.com")

[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ ping [[COLOR=#000000]www.google.com[/COLOR]]("http://www.google.com")[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ping: unknown host [[COLOR=#000000]www.google.com[/COLOR]]("http://www.google.com")[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$[/SIZE][/FONT]

And I have enabled the network connections. it detects the connection through the ethernet cable but the internet does not work. It works fine in windows.

---

### Post by 3rdalbum on 2010-05-20
> **Blobface said:**
> this is what I get if I ping [[COLOR=#000000]www.google.com[/COLOR]]("http://www.google.com")

[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ ping [[COLOR=#000000]www.google.com[/COLOR]]("http://www.google.com")[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ping: unknown host [[COLOR=#000000]www.google.com[/COLOR]]("http://www.google.com")[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$[/SIZE][/FONT]

And I have enabled the network connections. it detects the connection through the ethernet cable but the internet does not work. It works fine in windows.

Try this:

[www.chrislees.info/ubuntu/opendns.shtml](www.chrislees.info/ubuntu/opendns.shtml)

Sometimes is needed for this situation, when you have a network connection but when the router has not correctly passed DNS information.

---

### Post by Peter09 on 2010-05-20
Your wireless will be disabled while you are connected through your wired link.
 
As a sanity check make sure that any hardware switches for your wireless are 'on'. Check that you have enabled any drivers in System->Administration->Hardware
 
and also if you haven't already do an update and upgrade.
 
Then with no wired connection do 
 
```
ifconfig
```
 
if you see a valid IP address in the output then you should be connected.

---

### Post by ctimko on 2010-05-20
Try pinging your Gateway.  It should be 192.168.1.1 or 192.168.0.1 (or look at your ifconfig, that should tell you).  If you can ping your gateway, what does your /etc/resolv.conf file have in it?  Also what does your /etc/network/interfaces say?

---

### Post by Blobface on 2010-05-20
3rdalbun - I've tried that but it still does not work
 
peter09 - I have posted my results for ifconfig earlier (post 5) but I dont know what I am supposed to be looking for
 
ctimko - when I ping the gateway this is what i get:
 
[COLOR=black][SIZE=3][FONT=Times New Roman]hab@hab-desktop:~$ ping 192.162.2.1[/FONT][/SIZE][/COLOR]
[FONT=Times New Roman][SIZE=3]PING 192.162.2.1 (192.162.2.1) 56(84) bytes of data.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=2 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=3 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=4 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=7 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=8 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=9 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=10 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=12 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=13 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=16 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=17 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Liberation Serif]From 192.168.2.4 icmp_seq=18 Destination Host Unreachable[/FONT]
 
[FONT=Liberation Serif]and it just keeps going on for ever, I had to close down the terminal screen to stop. This also happened for 192.168.1.1 and 192.168.0.1[/FONT]
 
[FONT=Liberation Serif]Does anyone elso have any ideas?[/FONT]
 
[FONT=Liberation Serif]this is a picture of Firefox and my network connection informaion if it helps[/FONT]
 
[FONT=Liberation Serif][[IMG]http://img710.imageshack.us/img710/2180/screenshot1w.th.png[/IMG]]("http://img710.imageshack.us/i/screenshot1w.png/")[/FONT]
[FONT=Liberation Serif]Uploaded with [ImageShack.us]("http://imageshack.us")[/FONT]

---

### Post by kingpoiuy on 2010-05-20
When you boot into your Windows partition what does this command give you?

```
ipconfig /all
```

You can put this command in the command prompt by going to start > run then type "cmd".

From this information we can find out what your IP settings are for a working computer on the network, then ensure your Ubuntu settings are similar.

---

### Post by Blobface on 2010-05-20
Hi kingpoiuy, I coulnt copy and paste it so i did a screen shot
 
[[IMG]http://img256.imageshack.us/img256/5536/screen2fs.th.jpg[/IMG]](http://img256.imageshack.us/i/screen2fs.jpg/)
Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Peter09 on 2010-05-20
Your ifconfig command was done while you had a wired connection - can you post the output of ifconfig when you do not have a wired connection connected.

---

### Post by Blobface on 2010-05-20
I unplugged my network cable and did ipconfig /all
 
[[IMG]http://img710.imageshack.us/img710/7136/screen3ob.th.jpg[/IMG]]("http://img710.imageshack.us/i/screen3ob.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
or did you mean ifconfig in Ubuntu?
 
also, Ubuntu does not detect my wireless card which is why I am trying to connect through a wired connection

---

### Post by Peter09 on 2010-05-20
I cannot easily read this but it appears that you have an ip address, if so then your wireless card is connected. To get the output into a cut and paste thing use the command

```
ifconfig >~/Desktop/ifconfig.txt
```

This should put the output of ifconfig into a file on your desktop called ifconfig.txt

---

### Post by Blobface on 2010-05-20
I tried that command but it gives the error message 'The system cannot find the path specified'
 
I did this in windows or was I supposed to do it in Ubuntu?
 
I have put a bigger image of post 16 below
 
[[IMG]http://img710.imageshack.us/img710/7136/screen3ob.jpg[/IMG]]("http://img710.imageshack.us/i/screen3ob.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by Peter09 on 2010-05-20
If you look at that output it shows that your wireless connection has an ip address of 192.168.2.2  and has identified your gateway, so it appears you are connected to your router at least.

What happens when you do
```
ping 192.168.2.1
```

---

### Post by Blobface on 2010-05-20
[[IMG]http://img706.imageshack.us/img706/9687/screen4f.jpg[/IMG]]("http://img706.imageshack.us/i/screen4f.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
but in ubuntu it does this
 
[COLOR=black][SIZE=3][FONT=Times New Roman]hab@hab-desktop:~$ ping 192.162.2.1[/FONT][/SIZE][/COLOR]
[FONT=Times New Roman][SIZE=3]PING 192.162.2.1 (192.162.2.1) 56(84) bytes of data.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=2 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=3 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=4 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=7 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=8 Destination Host Unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]From 192.168.2.4 icmp_seq=9 Destination Host Unreachable[/SIZE][/FONT]

---

### Post by Peter09 on 2010-05-20
Can you provide the output of the command

```
route
```

---

### Post by Peter09 on 2010-05-20
Did you do that ping with your wired connection in as well?

---

### Post by Blobface on 2010-05-20
[[IMG]http://img444.imageshack.us/img444/6401/screen5yj.jpg[/IMG]]("http://img444.imageshack.us/i/screen5yj.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by Blobface on 2010-05-20
no i did the ping without the wired connection

---

### Post by Peter09 on 2010-05-20
Can you provide the output of the route command issued in Ubuntu

---

### Post by tad1073 on 2010-05-20
why is your dns server the same as your default gateway?

that could be the problem.

go into your router and under preferred dns type in: 8.8.8.8 and 8.8.4.4 for your secondary dns

those are google dns server.

---

### Post by Blobface on 2010-05-20
wireless i got this
 
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ route[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[EMAIL="hab@hab-desktop"][COLOR=windowtext][FONT=Times New Roman][SIZE=3][EMAIL="hab@hab-desktop:~$"]hab@hab-desktop[/SIZE][/FONT][/COLOR][/EMAIL][FONT=Times New Roman][SIZE=3]:~$[/EMAIL][/SIZE][/FONT]
 
wired I got this
 
[FONT=Times New Roman][SIZE=3]ab@hab-desktop:~$ route[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]192.168.2.0     *               255.255.255.0   U     1      0        0 eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]link-local      *               255.255.0.0     U     1000   0        0 eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0[/SIZE][/FONT]
[FONT=Liberation Serif][EMAIL="hab@hab-desktop:~$"]hab@hab-desktop:~$[/EMAIL][/FONT]
[FONT=Liberation Serif][/FONT] 
[FONT=Liberation Serif]tad 1073 - i will try that now[/FONT]

---

### Post by Blobface on 2010-05-20
I went in to my router in the dns bit abd it had 'Automatic from ISP' checked and had 0.0.0.0. for both dns addresses. I unchecked it and typed 8.8.8.8. and 8.8.4.4. like you said and now i will try it in ubuntu. Is what i did correct?

---

### Post by tad1073 on 2010-05-20
> **Blobface said:**
> I went in to my router in the dns bit abd it had 'Automatic from ISP' checked and had 0.0.0.0. for both dns addresses. I unchecked it and typed 8.8.8.8. and 8.8.4.4. like you said and now i will try it in ubuntu. Is what i did correct?

yes

---

### Post by Blobface on 2010-05-20
I went back into ubuntu but it still didnt work

---

### Post by tad1073 on 2010-05-20
@Blobface; the only reason your dns should be a local address is if you have a dns server on your network

---

### Post by tad1073 on 2010-05-20
do you know how to get into your modem?

---

### Post by Blobface on 2010-05-20
I have no idea what that means
 
I have a Belkin 54g modem/router which i have 2 compuers running from it

---

### Post by Peter09 on 2010-05-20
This post just copied from another answer by 'anewguy'
> 
Here is what I would do first to check things out:

- right-click on network manager and go to edit connections again
- click on the wireless tab
- you should see "your ESSID" since that is the ESSID showing in your lists
- click on "Your ESSID"
- click "Edit"
- click on the Wireless tab
- mode should be infrastructure 
- MTU should be automatic
- click on the Wireless Security tab
- "Security" should be "WPA & WPA2 Personal"
- your password needs to match the password you set at the router.  
- click on the IPv4 tab
- "Method" should be "Automatic (DHCP)"
- click on the IPv6 tab
- "Method" should be "Ignore"


---

### Post by Blobface on 2010-05-20
yes i do. theres a router setup utility section where i can make changes

---

### Post by Peter09 on 2010-05-20
You can have a dns from your router (mine has). The router just relays from an external dns source, so this is not the problem, and windows works with this setup anyway.

---

### Post by Blobface on 2010-05-20
should I change something on it?

---

### Post by Peter09 on 2010-05-20
Not on your router - if it is working in windows then it should work in Ubuntu.

---

### Post by Blobface on 2010-05-20
Peter09 - I do not have any wireless conections as my wireless card is not detected in ubuntu. All my settings are the same for the wired connection but the internet wont work.
 
Anyway, I think I will give up for today. I would like to thank everyone who has tried to help.

---

### Post by tad1073 on 2010-05-20
your isp should provide your dns for you, unless, you use open dns, google etc. my setup is a modem into a router, where the router has dns that is supplied by my modem. If you have a dns server, your isp, open dns , google etc. is the primary provider and the dns server just caches dns for quicker lookup etc. Unless you are an isp.

---

### Post by halversondm on 2010-05-20
I think it is a 10.04 issue with SiS900 hardware.  I don't believe it is a broken hardware issue as I have 9.10 installed and WinXp installed on the same machine.  9.10 and WinXp work fine.  I'm on 9.10 now.  It's just that for 10.04 the SiS900 does not work.  I've tried many of the suggestions in this thread to no avail.

I've also chucked NetworkManager for Wicd, also to no avail.

I've also found this:
[https://answers.launchpad.net/ubuntu/+question/108900](https://answers.launchpad.net/ubuntu/+question/108900)

and many bugs in launchpad to the same effect.  It could be a bug with this kernel as well.  If I could connect I might be able to update it!

---

### Post by lanetherif on 2010-05-21
> **halversondm said:**
> I think it is a 10.04 issue with SiS900 hardware.  I don't believe it is a broken hardware issue as I have 9.10 installed and WinXp installed on the same machine.  9.10 and WinXp work fine.  I'm on 9.10 now.  It's just that for 10.04 the SiS900 does not work.  I've tried many of the suggestions in this thread to no avail.

I've also chucked NetworkManager for Wicd, also to no avail.

I've also found this:
[https://answers.launchpad.net/ubuntu/+question/108900](https://answers.launchpad.net/ubuntu/+question/108900)

and many bugs in launchpad to the same effect.  It could be a bug with this kernel as well.  If I could connect I might be able to update it!

Here, I have the same problem. I used to have a system gradually upgraded from 9.10 to 10.04. The connection was fine till two days ago. After a restart I saw that the connection was gone. I reinstalled 10.04 (I was planning even if I had a connection) and there is still no connection. Moreover, I am not able to connect in 10.04 live CD whereas things are fine with 9.10.
Another point that may be relevant, 9.10 also says that there is a kernel problem
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536)

Any ideas?

---

### Post by lanetherif on 2010-05-22
Ok, at the moment I have connection. My ethernet card is a Realtek RTL8111/8168. I disabled the wireless connection from router settings in 9.10 live CD and restarted to 10.04. Connection is fine although the there is a void on top right where the connection icon should be...

---


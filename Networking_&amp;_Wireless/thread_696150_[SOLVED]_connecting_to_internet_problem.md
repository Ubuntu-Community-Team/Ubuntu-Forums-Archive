---
title: "[SOLVED] connecting to internet problem"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by theduke2011 on 2008-02-13
Hi, I have a dual boot computer with XP and Ubuntu 7.10. I use a hardwired ethernet card to connect to the internet. It works perfectly fine in windows but not Ubuntu. Everything that I saw using the command lines looked good except (i can't remember exactly what i typed, something like    get name_if have   or something like that) and it gave me permission denied stuff. I use DHCP, not static. When I try and ping, it takes forever with a final error message basically saying I'm not connected. Do please help, thank you.

---

### Post by Iowan on 2008-02-13
Under System>Administration>Network Tools - click on the eth0 and verify that it gets an IP address (**ifconfig** from a terminal provides the same information.)
[This]("http://ubuntuforums.org/showthread.php?t=695227") post is similar - unfortunately hasn't been solved.

---

### Post by gimfred on 2008-02-13
'ifconfig' is a command that will tell you what your settings are and do some changes to the network. My system looks like the following:
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:BD:22:A1
          inet addr:192.168.1.4  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:febd:22a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:211015251 (201.2 MB)  TX bytes:6999537 (6.6 MB)
          Interrupt:23 Base address:0xf800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:307421 (300.2 KB)  TX bytes:307421 (300.2 KB)
```
'eth0' is my ethernet card and 'lo' is the internal networking system of the linux kernel. (The '0' is a numeral zero not a capital 'O' the terminal has a small dot in the centre to distinguish between the two. Linux starts (mostly) counting from 0 not 1 therefore we can read 'eth0' as ethernet device #1.) (Also, there is probably a better description of 'lo' but it isn't something I've looked at much.)

I happen to know I have a wireless card which linux (or Ubuntu if you prefer) calls 'ath0'
(Atheros chipset device #1 -- all wireless devices are designated by their chipset as there is a lot of differences and incompatibilities hardwired into the cards unlike ethernet which tend to have fairly reliable device drivers.)

So I enter ifconfig ath0 up:
```
ifconfig ath0 up
SIOCSIFFLAGS: Permission denied

```I assume this is the command that gives you a permission denied response? The computer is saying "That is on a need-to-know basis and you don't need to know."
The problem here is linux tries to separate for security reasons into the need to know basis. To prove to the computer you need to have the root (as in the main determiner of whether a tree *computer* lives or dies) access. In Ubuntu this is achieved with the super user do XXXXX command, that is 'sudo ifconfig ath0 up';```
sudo ifconfig ath0 up
[sudo] password for gimfred:

```Your computer would obviously give you your username i.e. '[sudo] password for theduke2011:' Type in your username password as applies. 

Now, that doesn't help you very much except to maybe give you an idea of what is going.

if you type 'lspci' into the terminal, what comes up? We can filter some of the data by asking only for information that concerns ethernet using the 'grep' command after 'lspci'. We need to connect the two commands via a "pipe" '|' ( My "pipe" is the shifted backslash  '\' key i.e. 'shift + \' = '|', it isn't lower-case L nor J nor upper-case i nor numeral 1. It looks like two vertical dashes similar to the colon, ':')

Thus the command is:
```
~$ lspci | grep ethernet
~$
~$ lspci | grep Ethernet
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
05:05.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```
As you can see the first time I searched for ethernet it didn't find anything so it filtered out everything. So before you run grep on a term run the first command without any filter to be sure you are getting the information you want! If you want to know more specialised commands for grep, you can type 'man grep' into your command line. man <the command you want to know about> will often give you some info about a command.I.e. 'man lspci'. The man pages can get a little cryptic or technical at times. 

Well at this point we know that I have an Rhine-II chipset ethernet card and an Atheros AR5212/ar5213 chipset wireless card. Now for people to start helping you we need to know your ethernet setup. So please post the data that 'ifconfig' and 'lspci | grep Ethernet' displays.

So if this post covers stuff you (theduke2011) already knew, it was more to help those who don't have a clue to get started finding out about their own setup.

---

### Post by theduke2011 on 2008-02-16
this info. came from a text file created sat. feb. 14 on what's happening...


this is the ifconfig

eth0      Link encap:Ethernet  HWaddr 00:40:CA:55:E6:D7  
          inet6 addr: fe80::240:caff:fe55:e6d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000

eth0:avah Link encap:Ethernet  HWaddr 00:40:CA:55:E6:D7  
          inet addr:169.254.10.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3253 (3.1 KB)  TX bytes:3253 (3.1 KB)

The eth0:avah from what it looks like, is the correct one, but when i go to configure it in network tools, it says the device 

does not exist. In the network tools box, the IP information area is filled on the eth0:avah, and the eth0 IP info is not 

available as it says. I think it is odd that the HWaddr is the same for both of them, I am unsure if this is normal.

update: sat. feb. 16
jakab@jakab-desktop:~$ ifconfig eth0:avah up
SIOCSIFFLAGS: Permission denied
jakab@jakab-desktop:~$ sudo ifconfig eth0:avah up
[sudo] password for jakab:
SIOCSIFFLAGS: Cannot assign requested address
jakab@jakab-desktop:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
jakab@jakab-desktop:~$ sudo ifconfig eth0 up
jakab@jakab-desktop:~$ 

still no connection, and if it helps any, the light on the modem that shows it is connected to the computer doesn't light up, 

however the power light, and download light are both lit up

this is the lspci info

jakab@jakab-desktop:~$ lspci | grep Ethernet
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. 

RTL-8139/8139C/8139C+ (rev 10)
jakab@jakab-desktop:~$

The internet still doesn't work, and yes, some I already knew, but this was still very helpful, thank you

(i copied and pasted this from the text so some of it may be a lil out of line)

edit: sorry for the smilies, they are not meant to be there, the smiley code happened to work out with the HWaddr

---

### Post by theduke2011 on 2008-02-17
I just now noticed the  Interrupt: 16 Base address:0x8000 , could this be the problem?

---

### Post by theduke2011 on 2008-02-18
If this is the problem, is there a fix to it?

---

### Post by theduke2011 on 2008-02-23
hello.....?

---

### Post by Iowan on 2008-02-24
Check [Post#6]("http://ubuntuforums.org/showthread.php?t=705023")

---

### Post by theduke2011 on 2008-05-26
Hey, it's been a while, but I decided to wait for the 8.04 Ubuntu to come out, I installed, and now the internet works fine :) Thanks for your help though

---


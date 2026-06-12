---
title: "New install does not connect to interenet (HELP)"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by mrparadigm on 2009-04-27
I[SIZE=2] am new to linux but very familiar with computers and have installed 9.04 i386 on a [/SIZE][SIZE=1][SIZE=2]Dell Dimension 3000 Desktop. Everything has loaded fine accept that it will not connect to the Internet. The desktop would be connected by Ethernet to a Motorola dsl router from ATT (non wirless). The router works because this is was written using that same connection on a laptop also using 9.04. What information do you need from me to help remedy this problem?[/SIZE]

[SIZE=2] 
:)Any help would be greatly appreciated as I have just converted my parents to Ubuntu because of all the problems they had with Windows![/SIZE]
[/SIZE]

---

### Post by JoshuaRL on 2009-04-27
I'm going to give you three commands to run from the terminal.  If you could post them here wrapped in [noparse]```
 tags 
```[/noparse] then we could see what we've got.
```
lspci
ifconfig eth0
ping -s -I -w5 www.google.com

```

The first lists the pieces connected to your computer.  The second lists your active ethernet connection.  And the third does a ping query to Google to see if you can see the internet and the internet can see you.

---

### Post by mrparadigm on 2009-04-27
[URL="file:///media/disk/Unsaved%2520Document%25201"][lspci]
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02) [/lspci]

[/URL]

---

### Post by mrparadigm on 2009-04-27
[eth0]      Link encap:Ethernet  HWaddr 00:11:11:2d:ed:06  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/eth0]

---

### Post by mrparadigm on 2009-04-27
ping -s -I -w5 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by JoshuaRL on 2009-04-27
Alright, you seem to have an Intel ethernet card on that machine, and it doesn't have connection.  Did you do those commands while connected to your modem?  I'm sorry, I forgot to tell you to do that part.

If so, could you elaborate on the type of internet service you have?

---

### Post by mrparadigm on 2009-04-27
I just connected the ethernet to the computer and gave it a few minutes to possibly recognize it. Then I input the commands. The service is ATT dsl service.

---


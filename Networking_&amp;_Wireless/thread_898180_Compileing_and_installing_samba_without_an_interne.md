---
title: "Compileing and installing samba without an internet connection - help needed"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by enixon on 2008-08-23
Greetings all. I'm trying to access the internet through a windows network. Because my dsl provider required non wine compatible software to be installed in order to use the dsl modem directly I cannot use the good old apt-get install command to install samba. This leaves me with no other choice but to compile samba from source my self. I don't know much about compiling software on Linux other than simple python programs I've compiled for the sake of learning so please bare with me. I've downloaded samba 3.2.2 unzipped and placed the files in /etc/samba/. There was already a samba folder in this location but it only contained 3 file smb.conf, gdcommands & dhcp.conf all of which i saved just in case. 

I've directed a terminal to the following path, /etc/samba/source/ then tried to configure using ./configure as some compile tutorials have suggested. This returns an error saying "no such file or directory" obviously theres no configure file like the one that was in the original samba file nor can I find one in the new samba directory. I've also tried the make command with the following error:*** No target specified and no make file found. Stop.

I'm reach a brick wall without the knowledge to clime over. Any help from ANY of you can provide would be greatly appreciated.

Sincerely Enixon

---

### Post by dmizer on 2008-08-23
Just because you don't have internet connection, doesn't mean you can't use the package system to install software.  You can directly download the package from the repositories on your windows computer, carry it over to your ubuntu computer, and install it without the need to compile.

You can also configure your Windows computer for internet connection sharing so that you can get online with Ubuntu.  Here's a good howto: [http://www.homenethelp.com/connection-sharing.asp](http://www.homenethelp.com/connection-sharing.asp)

Is your modem separate from the computer or a part of it?

Also, there are very very few cases where software is required in order to connect to your DSL.  Odds are, you don't even need the software for Windows. Most ISPs provide connection software as a "convenience" because many people find it troublesome to configure their computers without the software.  For some reason, these providers want to make it seem like there is no other way to connect to their service.

The only case I can think of is when using a USB or internal dsl software modem which requires drivers in order to function.  Even many of these will work in Ubuntu though.

---

### Post by enixon on 2008-08-23
Thanks for the quick reply dmizer. My modem is separate from my computer and its not a usb connection. All I'm trying to do is share a internet connection between one windows xp and one ubuntu computer. Does this even require samba or can it be done without any additional software? I read through the tutorial on the link you included with no results. The tutorial tells me to set the network ip and gateway manually with 192 168 0 1, 255 255 255 0, yet my internet will only work on my windows box when the net work is set to auto obtain and the internet connection has these numbers set so I'm baffeld when it comes to that sites advice. How would I go about setting up my dsl connection to my ubuntu box, with pppoeconf?


thanks

---

### Post by cariboo on 2008-08-23
You don't need samba to share an internet connection. Does you modem have a built in router, if not routers are pretty inexpensive and it would solve a lot of problems for you. If the modem does have a built in router have you tried accessing the mangement page to check what ip range it is serving addresses to.

Jim

---

### Post by enixon on 2008-08-23
I'm sorry for not being detailed. Yes I have a router. Both computers connect to the router and the router connects to the modem and no I haven't tried accessing the management page. I don't know what that is.

thanks

---

### Post by dmizer on 2008-08-23
You shouldn't need to worry about the management page.

Go to system > administration > network

Click on the button labeled "unlock" and type in your password.

Click to highlight the line labeled "wired connection" and click "properties"

Put a checkmark in the box labeled "Enable this connection". Switch the "configuration" from roaming to DHCP and click okay.

Wait for Ubuntu to connect and click "close".

You should be able to browse now. If not, please post the output of:
```
ifconfig
```
and
```
lspci
```

---

### Post by enixon on 2008-08-24
No luck with your directions. Here are the out puts you requested.

lord@lords-keep:~$ ipconfig
bash: ipconfig: command not found
lord@lords-keep:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:B3:31:8E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55824 (54.5 KB)  TX bytes:55824 (54.5 KB)

lord@lords-keep:~$ lspci
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
04:07.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
lord@lords-keep:~$ 

thanks for all your effort.

---

### Post by dmizer on 2008-08-24
What IP address does the windows computer have?

Please post the output of this command:
```
sudo ifdown eth0&& sudo dhclient eth0
```

If that is unsuccessful, please post the contents of: /etc/network/interfaces

Also, please try rebooting your router.

---

### Post by enixon on 2008-08-24
Well I hopped on today to check if there were any more updates to this forum only to glance over to my ubuntu boxes screen and see the orange updates available box next to the network icon. It appears all that was required after your last entry was a fresh restart of both boxes, so it appears the problem is fixed. Thank you both for all your help. You saved my a lot of wasted time and personal anguish.

---

### Post by enixon on 2008-08-25
It appears I've spoken to soon. My ubuntu box has free access to the internet but my windows box only has intermittent access. As soon as I reconfigure the network on windows, the windows box accesses the internet slowly for about a a minute before it drops out. If I unplug the ubuntu box from the router then hit repair on the connection, the windows box will then work perfectly so obviously its one or the other but not both that will work at one time. I have the network set to auto assign ip while the internet connection is set to 192.168.0.1 and the subnet mask is 255.255.255.0.

thanks!

---

### Post by dmizer on 2008-08-25
> **enixon said:**
> I have the network set to auto assign ip while the internet connection is set to 192.168.0.1 and the subnet mask is 255.255.255.0.

thanks!

When you can browse and everything works correctly in Windows, what's the IP address in Windows?

When you can browse and everything works correctly in Ubuntu, what's Ubuntu's IP address? You can check with this command:
```
sudo ifconfig
```

Sounds like you have a router settings issue where your router is trying to hand the same IP address to both windows and Ubuntu.

---


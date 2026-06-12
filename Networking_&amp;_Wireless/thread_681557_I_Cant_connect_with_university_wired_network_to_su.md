---
title: "I Cant connect with university wired network to surf internet..Pl help me"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by blues on 2008-01-29
Somebody pl help me. I have been trying for last 2 weeks:mad:  but failed to connect with university network and so internet. Now I am here.

1. My machine is Compaq Presario V3174TU Notebook
2. Windows Xp professional and Ubuntu 7.10 Gutsy installed (installed 2 weeks ago)
3. Using Univeristy wired network, speed 10.0 Mbps, I need to log in university net through Ruijie supplicant. I attached configuration picture of this supplicant in [COLOR="Red"]'Supplicant.zip'[/COLOR] folder. By this network i can browse all chinese web site and very few international web site.
4. To get full access to international web site from china  i bought one package from other company. Probably it is called VPN(Virtual private Network).I installed their software [&#25945;&#32946;&#32593;&#30452;&#36890;&#36710;(&#25945;&#32946;&#32593;)V0.92] and need to log in through their software to browse international web site. I attached configuration picture of VPN in [COLOR="red"]'Vpn.zip'[/COLOR] 
5. All of these are working very nice in Windows Xp. My notebook is connected by one cable to the room wall socket. Both side's jacks are called probably RJ45.
7. From Command prompt (Xp) after running [COLOR="red"]'ipconfig' [/COLOR]I got this: 
```

C:\>ipconfig
Windows IP Configuration

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 219.245.180.237
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 219.245.180.1

Ethernet adapter Wireless Network Connection:
        Media State . . . . . . . . . . . : Media disconnected

PPP adapter &#25945;&#32946;&#32593;&#30452;&#36890;&#36710;(&#25945;&#32946;&#32593;)V0.92:
        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 58.207.172.69
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 58.207.172.69

```

6. After installing Ubuntu i searched university net and was suggested to run 'Supplicant for Linux v1.1.1' . I downloaded but failed to run due to proper libpcap. So i installed successfully (It took 2 weeks to read several web sites and several threads)
     a.  bison++_1.21.11-3_i386.deb 
     b.  flex-2.5.4
     c.  build_essential-11.3.3ubuntu1-i386.deb
     d.  libpcap-0.9.8 

but still i cant run 'Supplicant for Linux v1.1.1' ..i didnt find any english web sites except chinese to explain this. As i understand chinese very little i couldnt make it run. But what i understood it needs another software called xrgsu-libpcap.tar.gz that i couldnt find. So i am in hell lot of s....t now. 

7. Now its the time to ask help from u guys. Perhaps the following info will help u:
```

xerox@xeroxpc:~$ su
Password: 

root@xeroxpc:/home/xerox# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:0D:33:31  
          inet addr:172.16.7.126  Bcast:172.16.7.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe0d:3331/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:585293 (571.5 KB)  TX bytes:505524 (493.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:18:DE:2E:0A:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa000 Memory:d4000000-d4000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6683920 (6.3 MB)  TX bytes:6683920 (6.3 MB)

root@xeroxpc:/home/xerox# lspci | grep -i eth
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

root@xeroxpc:/home/xerox# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

8. I also did this as trial basis: 
```

root@xeroxpc:/home/xerox# sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 4764
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d3:0d:33:31
Sending on   LPF/eth0/00:16:d3:0d:33:31
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 202.117.1.7 port 67

root@xeroxpc:/home/xerox# sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d3:0d:33:31
Sending on   LPF/eth0/00:16:d3:0d:33:31
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.90.7.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.90.7.2
bound to 172.16.7.126 -- renewal in 6647 seconds.

```
9. I think 202.117.0.21 is my primary DNS server and 202.117.0.20 is secondary server as it is found in Ruijie supplicant -server param dialog box. [The pic of dialog box  is in [COLOR="red"]Supplicant.zip [/COLOR]folder]. But these DNS server address are not same as 7 [Above. After running ipconfig in Xp]
```

root@xeroxpc:/home/xerox# ping 202.117.0.21
PING 202.117.0.21 (202.117.0.21) 56(84) bytes of data.
From 219.245.180.1 icmp_seq=1 Packet filtered
From 219.245.180.1 icmp_seq=2 Packet filtered
From 219.245.180.1 icmp_seq=3 Packet filtered
From 219.245.180.1 icmp_seq=4 Packet filtered
From 219.245.180.1 icmp_seq=5 Packet filtered
From 219.245.180.1 icmp_seq=6 Packet filtered

[1]+  Stopped                 ping 202.117.0.21

root@xeroxpc:/home/xerox# ping 202.117.0.20
PING 202.117.0.20 (202.117.0.20) 56(84) bytes of data.
From 219.245.180.1 icmp_seq=1 Packet filtered
From 219.245.180.1 icmp_seq=2 Packet filtered
From 219.245.180.1 icmp_seq=3 Packet filtered
From 219.245.180.1 icmp_seq=4 Packet filtered
From 219.245.180.1 icmp_seq=5 Packet filtered
From 219.245.180.1 icmp_seq=6 Packet filtered
From 219.245.180.1 icmp_seq=7 Packet filtered

[2]+  Stopped                 ping 202.117.0.20

```

10. I have attached all pictures of Network settings, Network Tools in the 'scr shot.zip' folder. So you will have an idea of my settings. I tried to connect with university network by using every option of 'Connect to server'. But no result. 

11. Attached:
      a.  Supplicant.zip
      b.  Vpn.zip
      c.   scr shot.zip
12. Somebody pl tell me what to do.

---

### Post by blues on 2008-01-29
I posted here my problem detailed hoping somebody will come and help me. I have been waiting from yesterday but still no help. I am nowhere.:(

---

### Post by blues on 2008-01-30
Today whole day i waited for some info. Now it seems that Ubuntu just brought me some frustration. logging off.:(

---

### Post by shafi on 2008-01-30
HI blues,
sorry that i am asking you this question , because i was in hurry i couldn't go through your attachements, so please exactly answer me,
Do you want to connect to your University internet through VPN?
if yes, do you have the account?

---

### Post by blues on 2008-01-30
Thanks Shafi
I want to connect with my univeristy network thorugh wired network. If i can be connected then i can browse. But to get access to all international web site I need to connect with another VPN.

So in windows actually i need log in 2 times one after another. First univeristy network and then login to VPN network. Without the 1 st one i cant be connected with 2nd one. 

I have account in both University wired network and  VPN. 

I m going to sleep. Wish some fruitful solution. Thanx again

---

### Post by blues on 2008-02-02
I asked for help and so i explained everything very details but still i dint get any help any solution. Ubuntu really brought only frustration to me.:(

---

### Post by shafi on 2008-02-04
Dear [COLOR="Red"]blues,[/COLOR]
check these two links may be help you:

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Robert C on 2008-02-07
Sorry, as you know, I am also hoping for an answer because I can not connect to the university lan without Ruijie Supplicant also.

I have to say that the VPN page was next to useless. In order to get the client that is needed to the network, one must first connect to the network to get it... Catch 22. On top of that, Ruijie was not listed in the clients for down load. If you figure this out please post how you did it. So far I am still using pirated Vista.

---

### Post by blues on 2008-02-07
Dear Shafi 
Thanx to u. I read but didnt get any help from those pages. Probably i couldnt clear u my problem. Anyway VPN will come next after connecting with university LAN. I have been asking help how to connect with this LAN first. Some website suggest to install 'xrgsu-libpcap.tar.gz' but i couldnt find this software. I think Robert C is also facing the same problem. 

Hope somebody will appear with solutions... :(

---

### Post by farahbod on 2008-03-24
Your Xp ip configuration:
219.245.180.237
But your ubuntu:
172.16.7.126

:confused:
If you use static ip address, you should set this for both xp and ubuntu.
If you dynamically assigned ip, then normaly it should be assigned from the same range!

Let start a step-by-step configuration check to resolve this.

---

### Post by DregonX on 2008-05-14
Okay, I have a solution for this problem.

1. Download Ruijie Supplicant for Linux 1.1 from here: [http://forum.ubuntu.org.cn/download.php?id=16889]("http://forum.ubuntu.org.cn/download.php?id=16889").  It contains two files.  Sudo root, and put the "myxrgsu" file in the /bin/ folder, and the "libpcap.so.0.6.2" file in the /lib/ folder.  Make sure you modify the permissions for myxrgsu so that it can be executed as a program.

2. Download libstdc++5 from: [http://debian.linux.org.tw/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15_i386.deb]("http://debian.linux.org.tw/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15_i386.deb").  You probably won't be able to install this deb by double-clicking it because recent versions of Ubuntu come with a newer version, so open the packages with archive manager, and manually extract the two files found in the package to /usr/share/lib/  Remember that you'll need root permissions for this step as well.

3. Now, as a regular user, go to system - administration - network, and enable wired connection.  In the properties window, set the connection to: static IP address.  Then set your IP as anything in 192.168.1.* (for example: 192.168.1.234); set subnet mask as 255.255.255.0 and gateway as 192.168.1.1.  

4.  Now, open a terminal and type: sudo myxrgsu -d

5. Input your sudo password, then you'll be prompted for your account username and password.  Type them in, and you'll be connected.  Keep the terminal window open, or your connection will close.  

6. Enjoy.

This solution has been tested on Gutsy and Hardy, and has worked on both.  I hope it works for you.

---


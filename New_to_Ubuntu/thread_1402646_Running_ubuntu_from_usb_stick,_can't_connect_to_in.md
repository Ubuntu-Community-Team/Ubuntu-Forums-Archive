---
title: "Running ubuntu from usb stick, can't connect to internet"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by wdhpr on 2010-02-09
Hello new to the forum

I have been using Mepis on a dual boot computer for over a year. I want to give ubuntu a try so I made a bootable usb stick from ubuntu's live cd. Everything works as advertised even saved files and changes.

[COLOR=Red]THE PROBLEM[/COLOR]

[COLOR=Black]I can't connect to the internet:mad:

I am connected via a 2wire modem to a linksys router thats connected to my computer through a ethernet cable. the router is for connecting my son's computer. 
Anyway I have no problems connecting from windows or Mepis.
[COLOR=RoyalBlue]Whats strange is [COLOR=Black]I can even connect when booting directly off the live CD. When I try connect when booting from my usb stick [COLOR=Red]I get a can not connect error:mad:
[COLOR=Black]I am using the auto eth0 function and everything appears fine. I compared my settings from when booted from the live CD and they are Identical.
I used network tools and I can ping my IP address but when trying to ping a web address I get the can not connect error. I am beginning to think ubuntu has my USB stick confused with a CD but not sure how to correct it. HELP ):P

PS I thinking of switch from Mepis to Ubuntu but have had hardware issue's with Ubuntu in the past and want Test drive 9.10 first.

Thanks and Cheers
Wdhpr
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by HarrisonNapper on 2010-02-09
Run the following commands and post the output(s) here:


```
ifconfig; lspci; ping <internal IP of your router>; ping google.com
```

Normally if you can successfully ping the router or another computer on the network, the connection with the router was successful. Can you access the internet on another computer at the same time as when you are having the issue from the LiveUSB?

---

### Post by wdhpr on 2010-02-09
> Normally if you can successfully ping the router or another computer on  the network, the connection with the router was successful. Can you  access the internet on another computer at the same time as when you are  having the issue from the LiveUSB?Yes I can. As a matter of fact my son was playing games on the internet at the same time I'm running Ubuntu from my usb stick. It really seems to be something happening as a result of me booting ubuntu from my usb. As I mentioned, when I boot Ubuntu from the live CD the internet works perfectly.

I will run those line commands and give the results. Thanks for helping :)

Cheers
Wdhpr

[COLOR=Blue]Here are the Results[/COLOR]:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:6f:b2:70  
          inet addr:10.10.10.100  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe6f:b270/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104139 (104.1 KB)  TX bytes:6945 (6.9 KB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9170 (9.1 KB)  TX bytes:9170 (9.1 KB)

ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
01:08.0 Communication controller: Conexant Systems, Inc. Device 2f40
ubuntu@ubuntu:~$ ping
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
ubuntu@ubuntu:~$ ping 10.10.10.100
PING 10.10.10.100 (10.10.10.100) 56(84) bytes of data.
64 bytes from 10.10.10.100: icmp_seq=1 ttl=64 time=0.058 ms
64 bytes from 10.10.10.100: icmp_seq=2 ttl=64 time=0.046 ms
64 bytes from 10.10.10.100: icmp_seq=3 ttl=64 time=0.046 ms
64 bytes from 10.10.10.100: icmp_seq=4 ttl=64 time=0.051 ms
64 bytes from 10.10.10.100: icmp_seq=5 ttl=64 time=0.047 ms
64 bytes from 10.10.10.100: icmp_seq=6 ttl=64 time=0.049 ms
64 bytes from 10.10.10.100: icmp_seq=7 ttl=64 time=0.049 ms
64 bytes from 10.10.10.100: icmp_seq=8 ttl=64 time=0.046 ms
64 bytes from 10.10.10.100: icmp_seq=9 ttl=64 time=0.049 ms
64 bytes from 10.10.10.100: icmp_seq=10 ttl=64 time=0.044 ms

---

### Post by HarrisonNapper on 2010-02-10
bumping. The os sees your NIC and is connected to the router, which means that the router may not be allowing the computer through. Do you have MAC address filtering enabled? Most routers offer a UI that you can access by typing the gateway IP (of router) in to a browser. Make sure the router recognizes your computer and is placing no restrictions on it.

Also, try network-manager and see if it works any better
```
sudo apt-get install network-manager
```

Cheers.

---

### Post by wdhpr on 2010-02-10
Hello and thanks for the help :)

I managed to correct the problem. I reinstalled ubuntu from windows using the Pendrivelinux usb-creator. Others experiencing this problem suggested this procedure. Why it worked and not the install via the Ubuntu live CD I have no clue, but I used the same ISO file. 
Again thanks

Cheers
Wdhpr

---


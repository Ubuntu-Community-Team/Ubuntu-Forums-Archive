---
title: "No internet connection"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by p.utsav on 2009-09-10
...So I got attacked by viruses on my xp. I finally installed Ubuntu 9.04 on my Dell Inspiron 1501. However, now I am not being able to connect to the internet. The radio bars show a lil red cross on them. However, networking is enabled, wireless is enabled. Yesterday night the wireless adapter was turned on, now its not and I dont know how to turn it on either. I checked the firefox file menu and I have checked off the "work offline" option. Need help.

Thanks a lot for any responses in advance.

---

### Post by Hospadar on 2009-09-10
First, are you sure you didn't accidentally hit the wifi switch on the laptop itself?

Second, what kind of wifi card do you have, if you could open a terminal, run the following commands and post the output it would be helpful

ifconfig
iwconfig
sudo lshw -C network
lspci

Just so you know, ifconfig gives network info, iwconfig gives wireless info, lshw gives hardware info, lspci gives pci bus info.

---

### Post by ukripper on 2009-09-10
you need to turn your laptop wifi switch back on as other poster suggested.

---

### Post by AlexanderDGreat on 2009-09-10
Here's how to restart your NetworkManager without rebooting your pc, might come handy...

sudo /etc/init.d/NetworkManager restart

---

### Post by p.utsav on 2009-09-10
There you go...

administrator@ubuntu:~$ lspci



00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)

08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
administrator@ubuntu:~$ ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:19:b9:57:1e:de

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 
          
	  RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:21



lo        Link encap:Local Loopback

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:36 errors:0 dropped:0 overruns:0 frame:0

          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:2688 (2.6 KB)  TX bytes:2688 (2.6 KB)



pan0      Link encap:Ethernet  HWaddr 0a:92:ef:a7:e0:11

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:19:7d:8c:9e:63

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-19-7D-8C-9E-63-00-00-00-00-00-00-00-00-00-00

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




administrator@ubuntu:~$ iwconfig


lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:""

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated

          Tx-Power=20 dBm

          Retry min limit:7   RTS thr:off   Fragment thr=2352 B

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.




administrator@ubuntu:~$ lshw -c network


WARNING: you should run this program as super-user.

  *-network
       description: Network controller

       product: BCM4311 802.11b/g WLAN

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:05:00.0

       version: 01

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: driver=b43-pci-bridge latency=0 module=ssb

  *-network

       description: Ethernet interface

       product: BCM4401-B0 100Base-TX

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:08:00.0

       logical name: eth0

       version: 02

       serial: 00:19:b9:57:1e:de

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

  *-network:0 DISABLED

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:19:7d:8c:9e:63

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

  *-network:1 DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: pan0

       serial: 0a:92:ef:a7:e0:11

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by p.utsav on 2009-09-10
@AlexanderDGreat:

Where do I type in this??
(Sorry, I am a first timer at anything other than windows)

---

### Post by p.utsav on 2009-09-10
Ok, I turned on the wireless adapter from windows but still I cant access the net

---

### Post by AlexanderDGreat on 2009-09-10
You type this in the Terminal.

Go to Applications > Accessories > Terminal.

You will use this a lot, it's also called CLI (command line interface). Don't get intimidated.

user@computername:~$

user = your username
@
computername: = your hostname/cpuname

~ = means you're in your home directory.

$ = means you're using CLI as user NOT root, root is #.

note: when you're just a user you always add "sudo" before every command that's critical, it just means, super user do...

/etc/ = where most of your config files are located

/etc/init.d/ = where most of running background services are located (d is for daemon), i dunno meaning of init

NetworkManger = this is the gnome-network-manager program

restart = restart...

*** Hey man, not to discourage you, but if you wanna make your wifi work, you have to read, read, and read some more... There are a lot of frustrated wifi users in Ubuntu, I'm just warning you so you'll be prepared and know what you're dealing with. Do you have the time? Good luck. =)

---

### Post by p.utsav on 2009-09-10
Thanks for the description. Yes I do have time and willingness to get thru Ubuntu. I see a lot of forums for internet connections on Ubuntu. BTW, I had to install the driver which I did from System>Admin>Hardware Drivers. Now its showing me diff. networks available, however, its not accepting the password to my wifi network.

---

### Post by AlexanderDGreat on 2009-09-10
In my case, I've tried using different wifi's some will connect in 3 seconds, others in 20 seconds, others won't connect at all.

Also, I do a little trick, I connect intermittently, when that blue thing is circling around in NetworkManager (connecting), I let it be for 10 seconds, then I click my network name again twice, then it connects!

Sometimes, I disable it, enable it, click to my network name, wait 12 secs, click again 2-3x, then I'm online.

However others, I tried different things, but won't plain connect, later I found out it's the router's fault.

I'm not an expert on this, so forgive my lack of technical advices.

---

### Post by p.utsav on 2009-09-10
Ok, when I left click the radio signal, it shows the list of networks available. I select my network and the blue thing starts circling. After a lil while, I get a window titled "wireless network authentication required"

Wireless Security: WPA & WPA2 Personal
Password: <a long alphanumeric string> (which is not my network password)

Am I suppose to enter my network password there? I did that and its not helping either.

---

### Post by AlexanderDGreat on 2009-09-10
Here's what I do:

1: delete everything in NetworkManager > Edit Connections > Wireless >

2: Go to your router settings, make sure to broadcast your SSID.

3: Have NetworkManager detect it, click on your network if necessary

4: NetworkManger will ask for your password, enter it. (I suggest always use WPA)

If you can connect by this time, NetworkManager will automatically save this connection in Edit Connections > Wireless >

If not, repeat 1-4.

Note: even if NetworkManager won't accept your password try it again and again.

Also, do some testing, reset your router to its factory defaults, then try connecting without a password or a complicated SSID, just to make sure you can connect in its plain basic service, that way, you will know for sure if you can connect evern before using complicated settings.

---


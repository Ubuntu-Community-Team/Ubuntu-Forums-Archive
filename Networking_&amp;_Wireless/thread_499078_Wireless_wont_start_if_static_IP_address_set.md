---
title: "Wireless wont start if static IP address set"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by netreg on 2007-07-12
Hi,

I have been struggling with this now for months, but if i set a static ip address for my wireless interface, when i startup the wireless icon on the nm-applet doesn't appear and I cant use wireless.   As soon as i remove the static ip address from the interfaces file, it works...

I have seen someone raised a bug report 110187, but i was wondering if anyone has found a workaround to this, other than using dhcp.

thanks in advance.

---

### Post by Azoix on 2007-07-12
[B][COLOR="Blue"]I would be interested in this answer too , i have similar problems myself , a flat refusal of this laptop to connect to the wireless , odd unexplained drop-outs on occasion , and other weirdness.
Setting the connection to DHCP , letting it configure and pick-up an IP , then changing back to static , fixes the issue, but shouldn't be required...........sometimes i think the fella's at MS have something to contribute after all , you dont get these issues wirelessly in windows...(excuse the language).

edit : I am also interested as to why the interface list shows me my connection , wlan0 set static but also has wmaster0 ( ?? ) set DHCP.
I can connect and disconnect at will , the mentioned sporadic dropouts are due mainly to L.O.S interferance , and/or shonky equipment...but the switching between DHCP and static assignment of IP's bit has me confused.I know it's rebooting the interface , but WHY the interface is in need of said reboot is what i'm at a loss to explain.[/COLOR][/B]

---

### Post by Majorix on 2007-07-12
I have the same problem too.. Its annoying.

---

### Post by kevdog on 2007-07-12
Can you post your interfaces file with and without the static IP address???  After setting your static IP address did you disable roaming??

---

### Post by netreg on 2007-07-12
My Interfaces file looks like this at the moment..  If i totally remove the ehth1 lines then wi-fi kicks into life on startup..   it grabs a dhcp address and everything is ok..

When i log in, it will ask me to enter password for default keyring...  but with eth1 set as a static ip, i dont get that..

When i set the static IP, i dont remove the tick for roaming because in the nm-applet it wants a wep key, but i am using wpa.  


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.12.18
netmask 255.255.255.0
gateway 192.168.12.1

auto eth1
iface eth1 inet static
address 192.168.12.19
netmask 255.255.255.0
gateway 192.168.12.1




output from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:43:7A:67:90  
          inet addr:192.168.12.18  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe7a:6790/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1741364 (1.6 MiB)  TX bytes:469915 (458.9 KiB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:55:D5:39  
          inet addr:192.168.12.19  Bcast:192.168.12.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5364 (5.2 KiB)  TX bytes:5364 (5.2 KiB)


please let me know if i have provided enough, or if you need more

thanks in advance

---

### Post by kevdog on 2007-07-12
You have to tell me more --
You have two network cards on the computer??
eth0=wired connnection
eth1=wireless

Please post:
lshw -C network

Unless you want to go through a difficult configuration, you can not run both a wired and wireless connection at the same time.  I noticed you are trying to assign each card a different IP address.  Is this what you want to do??

---

### Post by netreg on 2007-07-12
> **kevdog said:**
> You have to tell me more --
You have two network cards on the computer??
eth0=wired connnection
eth1=wireless

Please post:
lshw -C network

Unless you want to go through a difficult configuration, you can not run both a wired and wireless connection at the same time.  I noticed you are trying to assign each card a different IP address.  Is this what you want to do??


Hi here are the answers and the output you requested.

Yes, i have a Dell Inspiron 9300 which was primarily running 'cough cough' windows XP Home.  
eth0 is the wired nic and eth1 is the wireless nic.

It could be that i'm not getting out of windows mode, as I just simply assign each nic its own IP address so when im at my desk, i plug in the ethernet cable...  when i move to another room, i unplug the cable and allow the wireless nic to take over...   that i presume is what you can do with linux...

It's not that i need them to run at the same time, but i want to be able to switch from one to the other with relative ease.

again, please let me know if you need more info...

thanks again.


I issued this command with the wireless not working, if you want me to run it again when the wireless is working then please let me know.   

:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:7a:67:90
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.68.12.18 latency=64 multicast=yes
       resources: iomemory:dfcfe000-dfcfffff irq:19
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:55:d5:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.12.19 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:dfcfd000-dfcfdfff irq:18

---

### Post by netreg on 2007-07-12
Ok, thought i would run it with wireless working to save time just in case. I removed the eth1 block from the interfaces file, and restarted ubuntu..  

:~# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:7a:67:90
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.12.18 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfcfe000-dfcfffff irq:19
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:55:d5:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.12.65 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:dfcfd000-dfcfdfff irq:18

---

### Post by kevdog on 2007-07-12
Ok I got it, explain to me what you want to do again, Im not quite clear?  You want the wireless to start automatically on startup with a static IP??

---

### Post by netreg on 2007-07-12
Yes, i simply want to be able to use a static IP address when using my wireless connection...   


As i said in one of my earlier posts i use WPA encryption and from what i can make out, using the nm-applet that only handles WEP encryption...

:D the downside of this is my laptop goes back to Dell tomorrow for a few days holiday whilst they replace the lcd...

thanks again

---

### Post by kevdog on 2007-07-12
Couple of things:

To run with a static IP and WPA I would highly recommend this thread:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Second
I think your wired connection and wireless connection are competing trying to set a static IP address.  I think first you should comment out the eth0 lines, and focus strictly on the eth1 configuration because that is your wireless connection.

When controlling or configuring the settings manually in the interfaces file, the nm-applet may or may not work.  nm does not formally use this file, so if things are set for certain internet adapters it simply defaults to the set settings.  Clicking or unclicking the roaming button and system->admin->networking controls the nm-applet.  With roaming the settings in the interfaces file are ignored, with unclicking roaming the settings in the file are defaulted to.  See for using a static IP, you definitely want roaming unclicked.

To use one interface, you need to make sure that the other interface is brought down.  the auto line in the interfaces file attempts to bring up both interfaces.  If you dont want the wired interface brought up automatically just comment out the auto line or bring the interface down manually via
sudo ifconfig eth0 down.

Where I would start -- First comment out all the settings for eth0, deal strictly with eth1 -- 
Make sure that you can set a static IP with eth1 without WPA settings.  After this works add the additional WPA settings.  Read the post referenced above on how to do this.  Make sure network roaming is disabled.

---

### Post by Azoix on 2007-07-13
[B][COLOR="Blue"]I do like the tut. above , very clear and concise.Well Done kevdog.
One point i will put forward , It is also possible to run 2 NIC's ,setting one interface as static and one as dhcp.
At least it is on my laptop, i run static IP when on ethernet , and the wireless is set to DHCP.Ubuntu also allows me to set a static IP for the wireless , but i run into connection issues in this case.
The machine will quite happily run static on both wireless and ethernet, if the wireless is connected, and i plug in the e-cable , it receives a second IP and runs with both.
It WILL not connect as easily with both on DHCP, but it will do so with some fiddling in the network interface GUI.
I can drop this laptop in the replicator , turn it on and be up with 2 IP's at anytime.
However , this is utilising an onboard and EXTERNAL interface , one being a USB dongle and this may allow this to happen here , but may not apply to your configuration.[/COLOR][/B]

---


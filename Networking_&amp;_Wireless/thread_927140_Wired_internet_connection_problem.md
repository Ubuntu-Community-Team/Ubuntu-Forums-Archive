---
title: "Wired internet connection problem"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by plymouthjp on 2008-09-22
Hi,
I hope someone can help which i feel should be a relatively easy problem.
I have just installed a copy of ubuntu 8.04 (amd64 version) onto my pc which is now being dual booted with vista. I am having trouble with ubuntu connecting to the internet. My connection to the router is fine as the internet works when the system is running vista or if i swap the connection onto an older separate computer running ubuntu. (Please note this older computer did not require any network connection set up when installed).

I have gone through the network settings and firefox settings and have set them up to a similar configuration as my old ubuntu computer, which I presume are defaulted settings for a standard direct internet connection.   

Thanks in advance.

---

### Post by Iowan on 2008-09-22
What do your connections look like? (Results of **ifconfig** and contents of **/etc/network/interfaces**)

---

### Post by plymouthjp on 2008-09-22
Thanks for the reply, this is the result of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:18:f3:d8:de:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:d8:e9:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91900 (89.7 KB)  TX bytes:91900 (89.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0b:a7:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-0B-A7-75-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




Sorry for my naivety, but what and where do i get the contents of my network and interfaces (I am a newbie to ubuntu). But i hope this helps.

---

### Post by Iowan on 2008-09-22
> **plymouthjp said:**
> Sorry for my naivety, but what and where do i get the contents of my network and interfaces (I am a newbie to ubuntu). But i hope this helps.
From a (gnome) terminal, type **less /etc/network/interfaces**, then use the Edit>Copy to copy it, then Edit>Paste to insert it here (or another document for transfer). **cat /etc/network/interfaces** also works.

It would appear that no IP addresses are being assigned.The ** /etc/network/interfaces** file will show how they *should* receive addresses.

BTW, two Ethernet cards? Are you cabled to the right one?

---

### Post by plymouthjp on 2008-09-23
When typing in either line i get -
auto lo
iface lo inet loopback

Although I have 2 ethernet ports, neither work when trying to connect to the internet. (But Vista seems to pick work on either port).

---

### Post by plymouthjp on 2008-09-23
Some more info that may be of assistance.

When i try to ping my router in the terminal window it says "Network is unreachable".

When i look at devices in Network Tools i am not able to configure either of my Ethernet interfaces as well as no interface information being available at the bottom. (Although sometimes when i boot up ubuntu i have a 3rd interface card (ethernet interface - eth0:avahi) which has an assigned IP address starting with 169.x.x.x.

Do i need to install a driver for my interface card? I have an Asus p5n32-sli motherboard. Or is it to do with vista mapping memory as i have read elsewhere or am i looking at it a little to deeply?

---

### Post by plymouthjp on 2008-09-25
Hi, Still having trouble to connect to the internet on my dual boot system. (I hope someone can help)
What I do know -
The internet is working fine when i boot vista.
When i view the active connection information there are no addresses set up other than the hardware address, which is correct.(I am not always able to view the connection information as it is greyed out)

---

### Post by xebian on 2008-09-25
> **plymouthjp said:**
> When typing in either line i get -
auto lo
iface lo inet loopback

Although I have 2 ethernet ports, neither work when trying to connect to the internet. (But Vista seems to pick work on either port).

Here is what you should do, in that file /etc/network/interfaces, duplicate the 2 lines above but change 'lo' to 'eth0' or 'eth1'.  Save the file, and then execute sudo /etc/init.d/networking restart.  To check do ifconfig, and then make sure you have ip addresses on eth0 or eth1.

---

### Post by plymouthjp on 2008-09-26
Thanks for the reply, but when i try to make the changes to that file it is not letting me carry out the operation (due to permission restrictions), even if i try and copy the info and try to replace the file with the new one.

If I set up my network for dhcp, i have the following lines in the interfaces file.

auto lo
iface lo inet loopback  


iface eth0 inet dhcp
address 192.168.2.5
netmask 255.255.255.0
gateway 198.168.2.1

auto eth0

---

### Post by plymouthjp on 2008-10-01
I have tried all the posted suggestions but still with no luck.

I don't know if someone is able to tell me what the file /etc/network/interfaces is suppose to read, as i am now not sure what it originally read due to various suggested changes i have seen on this and other forums. I have tried so many different network permutations but i am still getting nowhere.

In network mananger my wired network reads(nVidia Corp MCP55 ethernet) which seems to suggest that it is recognised by Ubuntu(although this does not come up everytime i boot up Ubuntu).

I do know my equipment is okay, as everytime i boot Vista my internet connection always works.

So I do help someone can help, as i don't want this to let me give up on Ubuntu. Surely this cant be this difficult

---


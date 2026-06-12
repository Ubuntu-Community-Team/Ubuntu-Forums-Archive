---
title: "Vpn"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by PhDP on 2008-06-14
I'm trying for quite some time to make my VPN connection work with Ubuntu, but it simply doesn't work. First I had troubles with the installation (a patch is needed), but now the problem is just... weird. 

I enter the command; 

```
vpnclient connect <PROFILE> user <USERNAME> pwd <PASSWORD>
```

And I get; 

```
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686
Config file directory: /etc/opt/cisco-vpnclient

WARNING:
Using the "pwd" option may allow other users
on this computer to see your password.

Initializing the VPN connection.
Contacting the gateway at 132.203.244.151
Contacting the gateway at 132.203.244.152 (balancing)
Authenticating user.
Negotiating security policies.
Securing communication channel.

Bienvenue sur le r&#65533;seau de l&#65533;Universit&#65533; Laval!
Do you wish to continue? (y/n): y

Your VPN connection is secure.

VPN tunnel information.
Client address: 132.203.240.58
Server address: 132.203.244.152
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is inactive
Local LAN Access is disabled

```
...

Two things... #1. it is normal that I have to enter this long command every single time ?

#2, most importantly, it seems to work, but doesn't. Normally, with this connection I should be able to open firefox and have access to most scientific journals (with sciencedirect, JTSOR, Blackwell, et cetera...).

But I have no access, and I need this for my job. I've installed this VPN connection dozens of time on Windows XP in less than 5 minutes, but in a week I've been unable to make it work on Ubuntu, what's wrong ?

---

### Post by PhDP on 2008-06-16
I would really like to have an answer on this, I can't work without my VPN connection, and it's not a problem with FireFox, it's easy to know; my IP should change when I'm connected to the VPN.

---

### Post by tamoneya on 2008-06-16
what I did for the cisco vpn was I grabbed the pcf file from a windows machine and dumped it in /etc/CiscoSystemsVPNClient/Profiles.  This can be found in something like c:/programfiles/cisco systems/vpn/profiles.

Assuming that the configuration file is called myVPN.pcf you call the following command:```
vpnclient connect myVPN
```Then what I would do is I would add this line as into sessions (system->preferences->sessions) and hit add.  For name put "CIsco VPN" for command "vpnclient connect myVPN" and for discription: "connects to myVPN with cisco vpnclient"

---

### Post by PhDP on 2008-06-16
I'm not sure to understand your point, I know how to use the command to connect to the VPN, I know how profiles work, but I receive a message saying I'm connected (see my first message), but clearly, I'm not (my IP should change and it doesn't, and I can't get my scientific articles).

---

### Post by tamoneya on 2008-06-16
first of all I was dealing primarily with the 1st question you posed about making it simplier.  However I also wanted to make sure that you were using exactly identical settings as you do with a window XP install.  That way we can determine if it is a problem with the vpnclient itself or the way you entered the configuration.

---

### Post by PhDP on 2008-06-16
> **tamoneya said:**
> first of all I was dealing primarily with the 1st question you posed about making it simplier.  However I also wanted to make sure that you were using exactly identical settings as you do with a window XP install.  That way we can determine if it is a problem with the vpnclient itself or the way you entered the configuration.

ah yes sorry, I completely forgot about my first question.

I'm quite certain the configuration is O.K., I followed the procedure and the installation seems to work perfectly. Also, I get; 

Bienvenue sur le r&#65533;seau de l&#65533;Universit&#65533; Laval!
Traduction; Welcome to the network

As if I was connected...

---

### Post by tamoneya on 2008-06-16
can i get the output of ```
ifconfig
```Please post the output of when you are "connected" and when you arent.

---

### Post by PhDP on 2008-06-16
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:58:38:aa  
          inet addr:74.210.236.52  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:114 txqueuelen:1000 
          RX bytes:3642915 (3.4 MB)  TX bytes:293261 (286.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94200 (91.9 KB)  TX bytes:94200 (91.9 KB)

```

After;

```
cipsec0   Link encap:Ethernet  HWaddr 00:0b:fc:f8:01:8f  
          inet addr:132.203.240.82  Mask:255.255.255.0
          inet6 addr: fe80::20b:fcff:fef8:18f/64 Scope:Link
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1448 (1.4 KB)  TX bytes:54 (54.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1d:09:58:38:aa  
          inet addr:74.210.236.52  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:198 txqueuelen:1000 
          RX bytes:4451781 (4.2 MB)  TX bytes:419863 (410.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107372 (104.8 KB)  TX bytes:107372 (104.8 KB)

```

---

### Post by tamoneya on 2008-06-16
it appears that it has changed you IP address to 132.203.240.82.  Are you sure that it isnt working.  Test it by going to [http://whatismyip.com/](http://whatismyip.com/)

It may be that firefox is just using the wrong network adapter.

---

### Post by Dougie187 on 2008-06-16
Im not sure if this would help more or not, but there is actually a plugin for network-manager that uses vpnc, and its really easy to use. 

Just open a terminal and do a
```
sudo apt-get install network-manager-vpnc
```
then if you click on the network thing in your status bar, you can configure a vpn connection from that. and then to connect just click on it again and select the one you want to connect to.

---

### Post by PhDP on 2008-06-16
> **tamoneya said:**
> it appears that it has changed you IP address to 132.203.240.82.  Are you sure that it isnt working.  Test it by going to [http://whatismyip.com/](http://whatismyip.com/)

It may be that firefox is just using the wrong network adapter.

I went on [http://www.monip.org/](http://www.monip.org/) and; 

Before; 74-210-236-52.ri.cgocable.ca

After; 74-210-236-52.ri.cgocable.ca

Also, I see that it doesn't work; I can't go where I'm supposed to be able to go. On my WinXP computer, I see the new IP when I'm connected, but not with my Ubuntu laptop, it's quite frustrating.

---

### Post by tamoneya on 2008-06-16
what happens if you shutdown eth0.  I recommend this because you appear to be connected but firefox isnt figuring out that you want to use the cisco interface.  Try this in terminal:```
sudo ifconfig eth0 down
```Then restart firefox and give it a test.

---

### Post by PhDP on 2008-06-17
> **tamoneya said:**
> what happens if you shutdown eth0.  I recommend this because you appear to be connected but firefox isnt figuring out that you want to use the cisco interface.  Try this in terminal:```
sudo ifconfig eth0 down
```Then restart firefox and give it a test.

My computer froze, apparently I can't shut eth0 down then cisco is active.

---

### Post by tamoneya on 2008-06-17
here is what happens when I connect to my vpn:```
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Initiating TCP to 209.235.13.20, port 10000
Contacting the gateway at 209.235.13.20
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: 10.100.2.70
Server address: 209.235.13.20
Encryption: 168-bit 3-DES
Authentication: HMAC-SHA
IP Compression: None
NAT passthrough is active on port TCP 10000
Local LAN Access is disabled

```
and here is ifconfig:
```
tamoneya@tamoneyat61:~/Desktop/vpnclient$ ifconfig
cipsec0   Link encap:Ethernet  HWaddr 00:0b:fc:f8:01:8f  
          inet addr:10.100.2.70  Mask:255.0.0.0
          inet6 addr: fe80::20b:fcff:fef8:18f/64 Scope:Link
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:1777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1833 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74773 (73.0 KB)  TX bytes:131170 (128.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:6b:3a:ca:4a  
          inet addr:10.100.34.137  Bcast:10.100.34.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fe3a:ca4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2609330 (2.4 MB)  TX bytes:1280328 (1.2 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1443640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1443640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14717857887 (13.7 GB)  TX bytes:14717857887 (13.7 GB)

```
The thing that I noticed is that the vpn client posts one line: "Local LAN access disabled".  That says to me that it is switching from eth0 to cipsec0.  Not sure why yours isnt doing that.

---

### Post by PhDP on 2008-06-17
But what can I do ?

I absolutely need this for work, and I bought by laptop for work, so I can't let this as it is.

---

### Post by tamoneya on 2008-06-17
does this university have any support for linux.  Their tech support may have run into this problem before.  I would love to see this through to the end with you but that is about all I know about the cisco VPN client since that is how much I have used it and you seem to want to get this problem resolved quickly.

---

### Post by PhDP on 2008-06-17
> **tamoneya said:**
> does this university have any support for linux.  Their tech support may have run into this problem before.

I won't get anything from them, beside, this system is used by many universities, I can't believe nobody here can solve this problem.

---

### Post by Ejas12 on 2008-06-17
Well, I got an easy solution, use Log Me in Hamachi, is a free application that makes a vpn with few easy steps.
I know it isnt flashy but it works fine for me.:)

---

### Post by tamoneya on 2008-06-17
> **PhDP said:**
> I won't get anything from them, beside, this system is used by many universities, I can't believe nobody here can solve this problem.

I realize it is used at many universities.  My university uses it and I was able to get it congfigured correctly for my universities network.  However there are many different ways to setup a vpn and the settings on your vpn may conflict with some parts of the linux vpnclient.  If they support linux it wouldnt hurt to ask would it?

---

### Post by antm88 on 2008-06-17
I second the post about using the network-manager-vpnc plugin, I was able to configure mine based on a cisco config file so you may be able to also. Once you have it set up you can just right-click on your network-manager tray icon and choose 'connect to vpn'. It comes with a setup gui so its pretty easy to do.

---

### Post by PhDP on 2008-06-17
> **Ejas12 said:**
> Well, I got an easy solution, use Log Me in Hamachi, is a free application that makes a vpn with few easy steps.
I know it isnt flashy but it works fine for me.:)

I'll try that.

> **antm88 said:**
> I second the post about using the network-manager-vpnc plugin, I was able to configure mine based on a cisco config file so you may be able to also. Once you have it set up you can just right-click on your network-manager tray icon and choose 'connect to vpn'. It comes with a setup gui so its pretty easy to do.

Actually, it's installed but I don't see it when I right-click on the tray icon for my network, I only see; 'Enable Networking', 'Connection Information' (grey), 'Edit Wireless Network' and 'About'.

---

### Post by PhDP on 2008-06-18
...So what can I do except going back to WinXP ?

---

### Post by rickatnight11 on 2008-07-01
> **PhDP said:**
> Actually, it's installed but I don't see it when I right-click on the tray icon for my network, I only see; 'Enable Networking', 'Connection Information' (grey), 'Edit Wireless Network' and 'About'.
You don't actually have to right-click.  I have the network-manager-pptp package installed (which uses the pptp-linux package) and I just left-click on the network icon (like I was trying to find a wireless network) and there is a "VPN Connections" submenu.  I can create or select VPN connections there.  It should be similar for your package.

---


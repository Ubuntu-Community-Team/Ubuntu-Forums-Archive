---
title: "WPA2 Cannot connect"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by WI_Mike on 2007-07-27
Hello fellow Ubuntu-ers,

I have recently switched to Ubuntu 7.04 from Windows and must admit I am a super-n00b. Here is my problem, so I hope to find help.  

I have a wireless router configured for WPA2 with a password. Under windows I can see this router and just double click it then enter my password. All is fine. Yay internet!

Now, in Ubuntu, when I click the network connection thing in the upper right of the screen, it lists my wireless router. Then if I click on the name, the network connection manager just displays a swirly blue thing. Like it's attempting to connect to my wireless router. After about 5-8 minutes, I just give up because it has not connected. Whatever I do, I can't seem to get it to connect or ask me for a password. Boo! No internet.

If I select "manual connection" and then select my router, it only has WEP as security. It does not have WPA2.  

So, my question is how do I enable WPA2 through this network connection manager?  Please help this super-n00b out!  :KS

---

### Post by fredj on 2007-07-27
Open a terminal and type sudo lshw -class network. Post the output from that here.
Some linux wireless drivers don't do WPA or at least the network manager doesn't recognise
them as being capable of WPA. You may have to use windows XP drivers through the ndiswrapper
program, but first we need to know your wireless chipset and the driver that is being loaded for it.

---

### Post by NilsE on 2007-07-27
You need to make sure wpasupplicant is installed.  Since it only presents WEP to you I assume it isn't so go into synaptic and install it.

You may also want to look into pam-keyring so you don't have to enter the key every time.

---

### Post by daschmidt on 2007-08-03
I'm having the same problem and the wpasupplicant is correctly intalled! In "connect to other wireless connection" the wpa and wpa2 options desn't appears...

 ...

 description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ba:2f:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A ip=10.90.67.16 latency=0 multicast=yes
       resources: iomemory:b0200000-b0203fff ioport:a000-a0ff irq:18
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:ca:0e:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

...

thanks for any help!

---

### Post by kevdog on 2007-08-03
Couple of things to clarify this thread.

Is your wireless networking without encryption or with the use of WEP.  This is very important since I dont want to go chasing our tail.

Next if you do have an internet connection due the following
sudo aptitude install wpasupplicant

Great, now it sounds like your card and driver probably supports WPA protocol, however own way to check would be the following (so we can gather some parameters).

Change your router to WPA2 along with the appropriate ciphers

Although your wireless computer will not be able to connect perform the flollowing and post the results:

iwlist scan

---

### Post by daschmidt on 2007-08-07
The wpasupplicant is correctly installed. (checked and reinstalled twice).
the wpa - wpa2 don't appears in wireless security options when I try to connect to a wireless network manualy.

the results from a " iwlist scan " :

---

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

wlan0     No scan results

---
thanks for any help, and sorry about the noobness. ^^

---

### Post by kevdog on 2007-08-07
I just noticed when you posted:

*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:c0:a8:ca:0e:70
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

that no driver was assigned to this device.  Are you working with a USB or PCI device??  Did you attempt to install any drivers for the card?? And if so how??

---

### Post by daschmidt on 2007-08-08
No, I didn't. But it seens to work fine with WEP and non-authenticated networks.

If you know some kind of specific driver installation, please I wold like to try. ^^.

Tanks again!

---

### Post by kevdog on 2007-08-08
Lets go back to the beginning --
Can you tell me about your card, did you install any drivers??

I know you posted some of this information before, but to have it all in one place can you post:
lspci -nn
lshw -C network

Im trying to find the driver currently associated with your card and/or the chipset of the device.

---

### Post by WI_Mike on 2007-08-08
Hello,

I am still unable to connect to my WPA2 router. Here is the output of lshw -class network.

```
sudo lshw -class network
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@00:09.0
       logical name: ra0
       version: 01
       serial: xxxxx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febfe000-febfffff irq:19
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: xxxxxx
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:d400-d4ff iomemory:febfac00-febfacff irq:18
mcf@icarus:~$ 

```

Based on this, I believe my WIFI card is an rt2500.  I have also checked and the rt2500 module is loaded. 

I see there are several other people with this issue. I don't know what to say with them, but I have an RT2500 WIFI card and I am trying to access my WPA2 router. Network-manager and wpasupplicant are installed but I can not select WPA2 from network-manager.

Any ideas?? Help is appreciated since I can't access the internet and need to type everything through Windows.  So if someone can tell me how to activate WPA2 for the RT2500 card, that is what I am looking for.

---

### Post by kevdog on 2007-08-09
Here is what I would do

Although there are drivers for your ra based chipset contained by default, they are very old, and in many cases give people a lot of problems (Search the forums if you dont believe me)

I would update your rt2500 driver to the newest cvs version found at serial monkey:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

In order to assist you with the installation, here is a thread for installation of its sister driver (rt73):
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Please read the instructions about 3 times before beginning, and be mindful that you want the rt2500 cvs version rather than rt73.  Also, just use a little common sense --- when they mention blacklisting the rt2500 driver -- dont -- blacklist the rt73 driver.  If you read it with this idea in mind, you should be up and running in no time.

Post back if you need help

---

### Post by WI_Mike on 2007-08-09
Hello, 

I have followed the instructions for compiling the rt71 but I used the rt2500-cvs-daily.tar.gz file like you mentioned. The module compiled and I ran "make install" and it stuck the new module in the kernel directory.  I followed the rest of the instructions and did not blacklist the rt2500.  However, now when I use that network-manager I can see my wireless access point. But, when I connect to it, the network-manager just circles the blue thing for over 5 minutes (if I let it run that long).  So it's not connecting.  

Now, if I select "Connect to Other Wireless Network" the only options for wireless security are

WEP 128-bit Passphrase
WEP 64/128bit HEX
WEP 64/128bit ASCII

This is not new, I am still at the same point: unable to select WPA2.  Again, my wireless router uses WPA2 with AES not WEP.  Pleae please please, I'm looking for help in connecting via WPA2 not WEP.  

Does anyone know how I can connect with WPA2 and not WEP??

:confused: ](*,) [-o<

---

### Post by kevdog on 2007-08-09
If you are using the rt drivers -- (at least I think the post mentioned this) it really conflicts with network manager.  

Here is how I would do it

If you take a look at the post, try first to connect to an unencrypted network (if you can), manually through making changes in the /etc/network/interfaces file.  

If this is successful, try a manual connection to a wpa1 network through modifications in the /etc/network/interfaces file

If this is successful, try wpa2.

Since its a graphic tool that I can see you after, in the end when everything is configured. you need to use the rutilt GUI rather than the network manager to help you navigate the wireless networks.  This works for ra based chipsets

If you need help, this is what I need from you next post
lshw -C network
iwlist scan
/etc/network/interfaces <--- This is a file not a command

---

### Post by WI_Mike on 2007-08-09
I do not have access to an unencrypted (WPA/WEP/or otherwise) network. All I want to know is how to connect to my WPA2 router. I really can't believe Ubuntu has to make it so hard to do this...?  Nevertheless...

I have recompiled the driver just for giggles. But, I'm not laughing. :( Now, the post about the RT71 driver does not detail how to make changes for WPA2. I searched all the 52 pages and there were scant references to WPA2 and those posts did not detail the changes necessary to make in /etc/network/interfaces which would enable the driver to see WPA2 routers. All of the documentation and other posts which I have searched on the forum do not detail how to connect with WPA2 or simply mention how to use WEP (which is not an option). 

I posted my lshw -C network previously, but here it is again:

```

root@icarus:~#  lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@00:09.0
       logical name: ra0
       version: 01
       serial: xxxxx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febfe000-febfffff irq:19
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: xxxxx
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:d400-d4ff iomemory:febfac00-febfacff irq:18
root@icarus:~# 

```

Here is the output of iwlist scan:
```

root@icarus:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:13:46:0A:34:10
                    Mode:Managed
                    ESSID:"default"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-74 dBm  Noise level:-192 dBm
          Cell 02 - Address: 00:18:39:8F:76:C8
                    Mode:Managed
                    ESSID:"godzilla"
                    Encryption key:on
                    Channel:9
                    Quality:51/100  Signal level:-50 dBm  Noise level:-192 dBm
          Cell 03 - Address: 00:13:46:03:E0:FE
                    Mode:Managed
                    ESSID:"default"
                    Encryption key:off
                    Channel:6
                    Quality:0/100  Signal level:-81 dBm  Noise level:-192 dBm

root@icarus:~# 

```

And, here is my /etc/network/interfaces file:  

```

root@icarus:~# cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

###my edits

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=AES
    pre-up iwpriv ra0 set WPAPSK="xxxxx"
    pre-up iwpriv ra0 set SSID="godzilla"
    pre-up iwpriv ra0 set NetworkType=Infra
root@icarus:~# 


```

My router is the one called godzilla and it uses WPA2 with AES. I have xxx'ed out my router password and the serial #s on ra0 and eth0.  

Anyone have ideas?

---

### Post by kevdog on 2007-08-09
Just a quick question -- does this connection work with WEP or no encryption.  I would be good to have some feedback right now.  If I start making changes to the interfaces file and something doesnt work, I dont want to find out later it was because the card couldnt connect to a basic unencrypted network first.

---

### Post by Austin_KW on 2007-08-09
I dont think that the rt2500 legacy driver supports wpa2 authentication. You can use the AES encryption with WPA  (if you have downloaded the source look at rt2500-cvs-yyyymmddhh/Module/iwpriv_usage.txt)
I am not sure what WPA2 with PSK would gain you anyway so why not configure your router to WPAPSK (if it supports WPA2 then it certainly supports WPA)

---

### Post by kevdog on 2007-08-09
I posted a question in the rx2500 support forum to confirm if/which legacy drivers support wpa2.  Hopefully I will get a definitive answer soon, however it looks like preliminarily that the rx2500 driver does not support wpa2.

---

### Post by WI_Mike on 2007-08-09
I can get the rt2500 to connect with an unsecured, WEP-secured, and WPA-secured wireless AP. The problem is connecting with a WPA2 router.  

Also, if the solution is simply to change my router to WPA then my next question is how can I connect to WPA2 routers when I am at businesses or coffeeshops which only allow WPA2?  That is, these routers I am NOT able to simply change to WPA or WEP.

If the legacy drivers (are these the same as the serial monkey CVS ones? Or, by legacy do you mean the drivers that come out-of-the-box with Ubuntu?) do not support WPA2 then again, how can I connect to WPA2 routers when I am at airports, businesses, or places with routers I cannot change?

---

### Post by kevdog on 2007-08-09
Hopefully Ill have an answer soon, but where the heck do you live??  I dont know any airports that use WPA2 exclusively, in fact the only thing I know they use is WEP. 

If the answer is that the ra chipset doesnt support WPA2 currently, you will have to go get another networking card.

More later....

---

### Post by Austin_KW on 2007-08-09
I think it is that the wpa suppliciant in the serialmonkey rt2500 legacy driver does not support WPA2. It is unlikely that public access points wil support wpa2, private office networks may but I would then imagine that the would then also use additional enterprise class authentication.

You would probably need a driver that uses the wpa suppliant such as the beta rt2x00 driver, but I don't know if anyone has it working on ubuntu, but you could check the rt2x00 forums on serialmonkey.com.

---

### Post by Austin_KW on 2007-08-09
Another thought ,
You might blacklist the rt2500 driver and use the windows driver (rt2500.inf, rt2500.sys, rt2500.cab?) and use the ndiswrapper. I have not tried it but I guess it should work.

---

### Post by gijsbrecht on 2007-08-13
> **Austin_KW said:**
> I think it is that the wpa suppliciant in the serialmonkey rt2500 legacy driver does not support WPA2. It is unlikely that public access points wil support wpa2, private office networks may but I would then imagine that the would then also use additional enterprise class authentication.

You would probably need a driver that uses the wpa suppliant such as the beta rt2x00 driver, but I don't know if anyone has it working on ubuntu, but you could check the rt2x00 forums on serialmonkey.com.

The rt2500 driver does not support wpasupplicant. To be able to use wpasupplicant (and enable wpa2) you do need the experimental rt2x00 driver, which does not seem to compile with the ubuntu kernel. You could  give it a shot with a vanilla kernel (some ubuntu users seem to have been succesful using this approach), but using a custom kernel is a lot of trouble.
You could of course try ndiswrapper as Austin_KW suggested (I haven't tried that yet), but if that doesn't work I would seriously consider buying another wireless card that is better supported unless you enjoy spending lots of time maintaining your system.

---

### Post by kevdog on 2007-08-13
gijsbrecht

Actually I thought the problem with the rt2500 drivers were that they didnt support WPA2 -- I thought WPA (1) was actually supported.  Any source where you are getting you information??

---

### Post by wirelessmonkey on 2007-08-13
Ok, so why not just use WPA1?  WPA1 and 2 are virtually the same, with wpa2 including CCMP and full standards based PMK.   You can still use AES or TKIP with WPA1 and expect nearly the same level of security, particularly when using preshared keys.

---


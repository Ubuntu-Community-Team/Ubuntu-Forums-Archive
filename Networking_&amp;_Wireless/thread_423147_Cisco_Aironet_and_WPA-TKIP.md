---
title: "Cisco Aironet and WPA-TKIP"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by fornews on 2007-04-25
If the answer is already available that would be great but I haven't been able to find one that has worked.

T30 with Cisco Aironet that works fine under XP to my Linksys with WPA-TKIP configured.
I've recently installed Edgy and this is my first experience with Ubuntu

I can see and connect to my neighbors unprotected AP so I know there is some level
of functionality in the existing driver.  But I can not connect to my AP that has WPA TKIP configured.

I've tried Network Manager and I've also tried wpa_supplicant but that will still connect to my neighbor.

Contents of /etc/wpa_supplicant/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=1
update_config=1
fast_reauth=1
network={
       ssid="MySSID"
       psk="CorrectKey"
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
}

And I restart WPA with these commands

sudo wpa_cli terminate
sudo wpa_supplicant -Bw -i eth1 -D airo -c /etc/wpa_supplicant/wpa_supplicant.conf
sudo killall dhclient; sudo dhclient

However it still connects to my neighbor.

Some guidance is much appreciated. I've tried a number of things I've found on this site
and other places but nothing seems to work.

TIA
Jon

---

### Post by sdide on 2007-04-25
try running wpa_supplicant with the following config

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

 network={
        ssid="<your essid here>"
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="<your_key_here>"
}

and run it without the B option . eg-

~# wpa_supplicant -ieth1 -Dairo -c/etc/wpa_supplicant/wpa_supplicant.conf

and post output here

---

### Post by fornews on 2007-04-26
Much appreciated and I think you've brought out the crux of my problem with wpa_supplicant...

Unsupported driver 'airo'

Apparently the -Bw option/flag was supressing this very important error message.

Any suggestiuons what to do next ?

Jon

---

### Post by sdide on 2007-04-26
Not sure which wireless adapter is in a T30.

you can see it with 

~# lshw -C network

I would try with the Linux wireless extensions, wext., that is

~# wpa_supplicant -ieth1 -Dwext -c/etc/wpa_supplicant/wpa_supplicant.conf

---

### Post by fornews on 2007-04-26
The adapter is the internal Cisco Aironet... I think model 350 but not positive of that.


With -Dwext I received a number of errors beginning with
ioctl[SIOCSIWAUTH]: Operation not suppoted
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWAUTH] Operation not suppoted
WEXT auth param 4 value 0x1 - ioctl[SIOCSIWAUTH] Operation not suppoted

then a bunch of

 ioctl[SIOCGIWSCAN]: Resource temporarily unavailable

And then I had to reboot to connect to my neighbors AP again.

Jon

---

### Post by sdide on 2007-04-26
What did 

~# lshw -C network

give?

---

### Post by fornews on 2007-04-26
BTW this card works fine with the same AP under XP if that makes any difference.

lshw -C network
  *-network:0             
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:4b:07:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=airo ip=192.168.1.104 multicast=yes wireless=IEEE 802.11-DS
       resources: ioport:8000-80ff iomemory:d0200000-d0203fff iomemory:d0400000-d07fffff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:e0:99:5d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0204000-d0204fff ioport:8400-843f irq:11
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: ipsec0
       serial: 2a:3e:f8:25:9e:42
       capabilities: ethernet physical
       configuration: broadcast=yes

---

### Post by fornews on 2007-04-27
sdide....  

Any additional thoughts short of buying and installing a PCMCIA adapter ??

Jon

---

### Post by sdide on 2007-04-29
I'm out blank here. It seems you were doing all the right things, but still it did not work, the card might be unsupported, 
I've looked around and found these: 

[http://ubuntuforums.org/showthread.php?t=201145](http://ubuntuforums.org/showthread.php?t=201145)
[http://luni.org/pipermail/luni/2006-June/021599.html](http://luni.org/pipermail/luni/2006-June/021599.html)
[http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)

the last URL seems interesting.

last resort before you spend credits on a new card is to try googling it..

If I had to look futher into it, I would suggest communications on messenger or irc. :)

---

### Post by fornews on 2007-04-30
> **sdide said:**
> I'm out blank here. It seems you were doing all the right things, but still it did not work, the card might be unsupported, 
I've looked around and found these: 

[http://ubuntuforums.org/showthread.php?t=201145](http://ubuntuforums.org/showthread.php?t=201145)
[http://luni.org/pipermail/luni/2006-June/021599.html](http://luni.org/pipermail/luni/2006-June/021599.html)
[http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)

the last URL seems interesting.

last resort before you spend credits on a new card is to try googling it..

If I had to look futher into it, I would suggest communications on messenger or irc. :)

Thanks again..

From reading those links and other stuff I've researched myself the Cisco Aironet 350 is a real problem.
The driver from sourceforge is for 2.4 kernel and I'm at 2.6.17 so I figure that  wont work.
The most interesting link is the last one and from there it seems like a firmware update is all that
is needed if 2.6 kernel but the problem is it appears the firmware and tool used to load it
require an ID/PW from Cisco....argh.

Something tell me the only option is going to be a new PCMCIA that'll work.
Assuming so any good suggestions keeping the price at a minimum

Jon

---

### Post by spawnywhippet on 2008-04-23
> **fornews said:**
> Thanks again..

From reading those links and other stuff I've researched myself the Cisco Aironet 350 is a real problem.
The driver from sourceforge is for 2.4 kernel and I'm at 2.6.17 so I figure that  wont work.
The most interesting link is the last one and from there it seems like a firmware update is all that
is needed if 2.6 kernel but the problem is it appears the firmware and tool used to load it
require an ID/PW from Cisco....argh.

Something tell me the only option is going to be a new PCMCIA that'll work.
Assuming so any good suggestions keeping the price at a minimum

Jon

I have the identical problem. Did you find a resolution?
I'm running both a Thinkpad T30 with Intel High Rate 802.11b and a Thinkpad T41 with Cisco Aironet 802.11b and cannot get either one to connect to WPA. They'll both connect to WEP or unsecured though.

---

### Post by kevdog on 2008-04-23
This is a very old thread, but I'll throw my hat in the ring?  Can you post your wpa_supplicant.conf file and the command line used to invoke wpa_supplicant?

Hmm maybe I found the problem in the documentation:

Supported wireless cards/drivers

    * Linux drivers that support Linux Wireless Extensions v19 or newer with WPA/WPA2 extensions
    * Host AP driver for Prism2/2.5/3 (WPA and WPA2)
    * Linuxant DriverLoader with Windows NDIS driver supporting WPA/WPA2
    * Agere Systems Inc. Linux Driver (Hermes-I/Hermes-II chipset) (WPA, but not WPA2)
    * madwifi (Atheros ar521x)
    * ATMEL AT76C5XXx
    * Linux ndiswrapper
    * Broadcom wl.o driver
    * Intel ipw2100
    * Intel ipw2200
    * Wired Ethernet drivers
    * BSD net80211 layer (e.g., Atheros driver) (FreeBSD 6-CURRENT and NetBSD current)
    * Windows NDIS drivers (Windows; at least XP and 2000, others not tested)

---

### Post by spawnywhippet on 2008-04-23
Thanks for your response, I'm currently booted via LiveCD into Gutsy 7.10 on the Thinkpad T41, so no wpa-supplicant available. I blew away the installation of Ubuntu and tried CentOS to see if it was a distro-related problem anyway. 
My wireless chipset is Prism 2.5, but I think the main problem is that I do not know how to install an updated wireless driver on Ubuntu. I found an updated hostap driver, but despite 5 days of intermittent searching, have not found a single thread or help file describing how to install it in a way that I can understand. Every single help file I've come across assumes that the user is knowledgeable about Linux and doesn't explain the basics for a novice Linux user to follow. Eg, "compile the ndiswrapper and restart networking" - what does that mean and how do I do it??

As a 15 year experienced Windows guy with an (worthless) MCSE, it's frustating to spend so long on such a simple problem without even the hint of getting close to a fix. In both cases, my laptops connect to WPA networks in XP with no problems. I'd greatly appreciate any assistance or pointers on where to get the basic knowledge to start running with Linux in general.

---


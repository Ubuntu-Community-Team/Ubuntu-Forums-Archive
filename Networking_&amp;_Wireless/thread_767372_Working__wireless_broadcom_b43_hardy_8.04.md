---
title: "Working  wireless broadcom b43 hardy 8.04"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by ali_1 on 2008-04-25
yess finally got my broadcom wireless working on ubuntu 8.04 hardy. heres a guide below tried to make it easy for u to understand :S

this is how i did it :- (mainly used the linuxwireless.org for guidance)

1) first install fwcutter, just open synaptic package manager and search for fwcutter, you need to install from your ubuntu 8.04 cd!

2) then download :-
 [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

ok now open up a terminal and type the following

3) export FIRMWARE_INSTALL_DIR="/lib/firmware"

   --------------press ENTER------------------

    tar xjf broadcom-wl-4.80.53.0.tar.bz2

   --------------press ENTER------------------

        cd broadcom-wl-4.80.53.0/kmod

  --------------press ENTER------------------

sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o

--------------press ENTER------------------

and this should install the driver and it should work.

to check goto system -> administration -> hardware drivers

and it should be ticked and say "in use"!

anyway this works for me.

---

### Post by calibre97 on 2008-04-25
FYI, this may NOT work. Didn't for me. I've got an HP dv5035nr and I couldn't get the wireless to work for my life and I tried everything, including your steps. No joy. I wound up going with a D-Link 652 wireless card. Worked plug and play, no config. 

Just offering my outcome as a possibility in case anyone's interested and in the same boat (most normal tricks/hacks don't work for some reason).

---

### Post by mommono on 2008-04-25
Hi, I have the HP pavillion DV 6653eo with the broadcomm bcm4328 rev.3, and it is working perfect *with* WPA , following instructions in step 2d at "https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c9037d4dac23680f0939e488c2291413ce831ef3"

Just FYI

Best 
M :-)

---

### Post by cybil on 2008-04-25
Worked great for me...HP nx6125 Laptop.  Thanks!

---

### Post by NeoenY152 on 2008-04-25
ali_1

You are the man! ... It freaking works!!!

HP dv8100

---

### Post by grumpa4 on 2008-04-25
Worked for me on my HP dv6305  Thanks.  What a
great job

gertrude

---

### Post by andied on 2008-04-25
Perhaps I had beginners luck, but I did a search for Broadcom (name and description) in Synaptic Manager and B43-cutter came up, which I installed. I then went to System>Administration > Hardware drivers and enabled the Broadcom B43 driver and it downloaded the firmware and my wireless works great.

---

### Post by kevdog on 2008-04-25
The b43 drivers are only compatible with the following chipsets:

supported

    * bcm4303 (802.11b-only chips)
    * bcm4306
    * bcm4309 (only the 2.4GHz part)
    * bcm4311 rev 1 / bcm4312
    * bcm4311 rev 2 / bcm4312 (needs patches for 2.6.24)
    * bcm4318 

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * There is no support for any Draft 802.11n features.
    * BCM 4328/4329

---

### Post by david_lynch on 2008-04-25
I had the same experience as andied - I just let the system do the work. I went into synaptic and searched for wireless and found the broadcom fw-cutter, which then prompted me to download the firmware, and the wireless networks immediately appeared in the network manager applet, and I connected to my linksys WAP without any trouble.

---

### Post by Melcar on 2008-04-25
My 4318 works perfectly.  Only had to enable the restricted driver.  Still need to test its speed and range a bit more.

---

### Post by jecompton on 2008-04-25
Not working for me. I've got 4318 on a HP/Compaq Presario V5000. (an AMD turion 64)

The system > hardware drivers shows the box ticked and enabled, but I get no connectivity. lshw -C network shows the card disabled, and the light on the wireless button is off.

I had major problems on 7.10 as well. Only ndiswrapper worked, but even that was difficult--had to find just the right driver which of course I've lost since then...

---

### Post by Melcar on 2008-04-25
Range is very poor, as I suspected.  I had the same problems with the Gutsy module before and had to resort to ndiswrapper, which unfortunately, does not seem to want to work in Hardy

---

### Post by npallett on 2008-04-26
> **Melcar said:**
> Range is very poor, as I suspected.  I had the same problems with the Gutsy module before and had to resort to ndiswrapper, which unfortunately, does not seem to want to work in Hardy

You can get ndiswrapper working in Hardy, but there are some things you need to do, as described at the end of my earlier post:

[http://ubuntuforums.org/showthread.php?t=761325](http://ubuntuforums.org/showthread.php?t=761325)

---

### Post by ali_1 on 2008-04-26
no problem.

glad it works.:)

---

### Post by dtgolder on 2008-04-26
> **jecompton said:**
> Not working for me. I've got 4318 on a HP/Compaq Presario V5000. (an AMD turion 64)

The system > hardware drivers shows the box ticked and enabled, but I get no connectivity. lshw -C network shows the card disabled, and the light on the wireless button is off.

I had major problems on 7.10 as well. Only ndiswrapper worked, but even that was difficult--had to find just the right driver which of course I've lost since then...
This thread worked for me and got my Broadcom/NDISWrapper working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Look for the Hardy fix (almost at the end)

---

### Post by Aeph on 2008-04-26
Thanks. I was furious when I couldn't get my wireless config to work with Hardy the same way it did with Gutsy. This worked perfectly with my bcm4306.

---

### Post by jecompton on 2008-04-26
Thanks for the info on the ndiswrapper.

I almost have it working WITHOUT ndis, though. It's very strange. I have it where the light is on on the wireless on the laptop, and Network Manager now displays several of the WAPs in the area, including mine, but it refuses to accept my key.

Every minute or so, a Network Manager popup comes up asking for the key, but it fails to allow connectivity. I can even do dhclient on the wireless interface, but it gets no response.

I know the key, key type, and security mode are all correct, so I don't know what's wrong...

---

### Post by jecompton on 2008-04-26
.

---

### Post by ericmitz on 2008-04-26
I got this working, and everything seems fine on the surface, but my connection keeps cutting out and it's driving me insane!

I can browse the web fine, etc. But things that stay conencted like Pidgin keep disconnecting! 

anyone have any ideas?

---

### Post by f37u5g0d on 2008-04-26
This did not work for me (BCM 4306).

---

### Post by LoSt180 on 2008-04-26
Driver installed automatically, auto downloaded. Connected to my hidden WPA2 network.

Problem is my connection speed is only 1Mb/s. The Feisty bcm43 driver only allowed 24Mb/s. What's with the Broadcom drivers sucking? I know it's not the router signal, it has a high gain antenna and signal is at 80%. 

I have a Broadcom 4318. I guess I'll try to hash it out with ndiswrapper again, but it's such a pain.

---

### Post by andied on 2008-04-26
LoSt180, my connection speed also shows 1MB's, but when I run speed tests I get excellent speed - around 5000 kb/s, which is close to the top speed of my ISP provider.

---

### Post by LoSt180 on 2008-04-26
> **andied said:**
> LoSt180, my connection speed also shows 1MB's, but when I run speed tests I get excellent speed - around 5000 kb/s, which is close to the top speed of my ISP provider.

okay, I got around 2300 kb/s on a broadband test. When I transfered a 400MB iso from my file server it transfered at around 650-700 KB/s. I'm crappy at conversions, so what's that in Mb/s?

Edit: iwconfig shows speed at 24Mb/s

---

### Post by andied on 2008-04-26
650-700 KB/s - I think you are doing fine.

[http://edoceo.com/utilitas/bandwidth-calculator?from_bw=650+KB&cmd=Calculate](http://edoceo.com/utilitas/bandwidth-calculator?from_bw=650+KB&cmd=Calculate)

---

### Post by 7Seas on 2008-04-26
Works great for me.  Many thanks for simplified and easy to use info.  It's a breeze and everything works. Great!

---

### Post by jecompton on 2008-04-27
> **dtgolder said:**
> This thread worked for me and got my Broadcom/NDISWrapper working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Look for the Hardy fix (almost at the end)

Yes! It works now.

There was some undocumented pain along the way, though, so I'll mention it in case it helps someone. First of all, I had to use the 2a step (the sp34152.exe) on the document, not the 2c--just as others w/ a 4318 have said.

I did have to follow the tip for the hardy heron bug near the bottom of that page as well.

The twist was that I still had the problem w/ it asking for the encryption key over and over again. I kept checking the list and could see several of the neighborhood APs listed, but mine wouldn't connect. Finally, I checked again after 5 minutes or so and I saw my AP listed twice. The one I was trying to associate w/ had lowercase letters while the other was in all caps. Once I clicked on that one through network manager, I entered the key and it worked.

I should repeat that this was not the case with any of the other methods, and I had to follow the instructions on the link in this post very carefully.

---

### Post by RED_M on 2008-04-27
Hi. I was able to get through almost all of the tutorial, up to the point...

```
sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o
```

I got the message:

```
sudo: b43-fwcutter: command not found
```

This is for my bcm4318.

Any suggestions?

EDIT: Never mind. I was able to work around it by:

Accessing System > Administration > Hardware Drivers

Checking the "Enabled" box for "Broadcom B43 wireless driver," and letting that do the last step instead.

Might be something to include as an alternate option.

Wireless works! Been trying to get this working since Feisty last summer, so I'm really excited to finally keep Ubuntu (sorta..dual-booted with Windows) for the long-term! Thank you!

---

### Post by akall on 2008-04-28
Hi!
I have a Compaq 6715s, with BCM4312 wireless network controller. I've just installed a brand new Ubuntu Hardy distro.
My laptop has got a blue led and a connected button thanks to which you can enable/disable BCM4312.
After the installation the led was on, but I was not able to connect to my network.
Right now, after several trials, the led is always off with no possibility to set it on.
I tried with b43-fwcutter and with ndiswrapper, following this post.
No success.

I post here some commands, hoping someone will help me. Thanks in advance
> lshw -C network
*-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

> lspci -nn | grep 4312
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Moreover, I am not able to find any reference into System --> Administration --> Hardware Drivers


Need anything else to help me?:)

Thanx again,
Akall

---

### Post by tehMalone on 2008-04-28
Hmm, all guides I try seem not to work. Anyone know what to do, if Ubuntu do not know that there is a wireless card.
I'm on HP pavilion dv6510eo

---

### Post by jarodrig on 2008-04-28
I have the exactly same problem, Any ideas? I'm stuck with this, the solution is using an old pcmcia wireless (Atheros :P)

> **akall said:**
> Hi!
I have a Compaq 6715s, with BCM4312 wireless network controller. I've just installed a brand new Ubuntu Hardy distro.
My laptop has got a blue led and a connected button thanks to which you can enable/disable BCM4312.
After the installation the led was on, but I was not able to connect to my network.
Right now, after several trials, the led is always off with no possibility to set it on.
I tried with b43-fwcutter and with ndiswrapper, following this post.
No success.

I post here some commands, hoping someone will help me. Thanks in advance
> lshw -C network
*-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

> lspci -nn | grep 4312
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Moreover, I am not able to find any reference into System --> Administration --> Hardware Drivers


Need anything else to help me?:)

Thanx again,
Akall

---

### Post by notoriousdbp on 2008-04-28
I did have the b43 driver working immediately downloading b43-fwcutter using a wired connection to my router but I found the driver so unstable to use and while I could get ndiswrapper to load I couldn't get it to connect at all using that driver.  Currently I've rolled back to 7.10 as my Hardy experience has not been a good one. Very disappointed

---

### Post by petersk on 2008-05-17
It's actually "System: Hardware Drivers manager" in Kubuntu with KDE4.  Also, I get nothing but the invidia driver when I look at that.
when I do a lshw -C network for the bcm43 part I get:
*-network UNCLAIMED
description: Network Controller
product: BCM43XG
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 32 bits
clock: 33 MHz
configuration: latency=0

Kurt

---

### Post by Ayuthia on 2008-05-17
> **petersk said:**
> It's actually "System: Hardware Drivers manager" in Kubuntu with KDE4.  Also, I get nothing but the invidia driver when I look at that.
when I do a lshw -C network for the bcm43 part I get:
*-network UNCLAIMED
description: Network Controller
product: BCM43XG
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 32 bits
clock: 33 MHz
configuration: latency=0

Kurt
Can you post your lspci -nn?  I have not seen that product name before.

As for Kubuntu, if you have a working internet connection you can download the b43-fwcutter by using Adept.  It will do the same thing.  Or if you want to use Konsole:
```
sudo apt-get install b43-fwcutter
```

---

### Post by yebo29 on 2008-05-17
Nope!! didn't work for me. I am at the end of my wits... using hp dv2815nr

---

### Post by Ayuthia on 2008-05-17
> **yebo29 said:**
> Nope!! didn't work for me. I am at the end of my wits... using hp dv2815nr

If you go to the Terminal and type lspci -nn.  It will list your PCI cards and one of them will be your wireless card.  If it is a BCM4310 USB Controller [14e4:4315] (rev 01), you will need to use NDISwrapper.

You might want to start with this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by sylvesterp4 on 2008-08-05
Works Great on HP nx6110.:KS

Thank You

---

### Post by Ognid on 2008-08-06
I tried this as well, and found two fwcutter's in my list, one already installed.  Since it wasn't working I tried the other. Still no luck.

---

### Post by zeffuri on 2008-08-12
[FONT="Arial"][SIZE="3"]Hello all, after two straight days of trying to get my wireless network to connect, I've decided to stop searching and take the bull by the horns. Here's the deal:

I have the BCM 4311 chipset in my Gateway lappy and I've been trying to connect to my WEP home wireless network.  And since I am still new (three days in) to learning to love Linux I did a lot of copy and paste for terminal stuff.

I started [here]("http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/") built the fwcutter and literally copied every step.

It didn't work.  So I went [here]("http://forum.notebookreview.com/showthread.php?p=3675644") and tried this command... 
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
still with no luck.

And with all my newbian copy and paste craziness I don't know what step to go back to. I have both the B43 and B43legacy in my /lib/firmware folder  AND I can see my network and others around me, but can't connect to any of them (all WEP)

1. Will multiple firmware cause a problem?
2. What would you do?
3. Which program should I use to actually monitor and connect to my wireless network? (in XP there's a wireless network connection icon AND the Broadcom icon in my system tray, but only one allows me to truly use my wireless... is Ubuntu 8.04 like that?)

Thanks[/SIZE][/FONT]

---

### Post by Ayuthia on 2008-08-12
> **zeffuri said:**
> [FONT="Arial"][SIZE="3"]Hello all, after two straight days of trying to get my wireless network to connect, I've decided to stop searching and take the bull by the horns. Here's the deal:

I have the BCM 4311 chipset in my Gateway lappy and I've been trying to connect to my WEP home wireless network.  And since I am still new (three days in) to learning to love Linux I did a lot of copy and paste for terminal stuff.

I started [here]("http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/") built the fwcutter and literally copied every step.

It didn't work.  So I went [here]("http://forum.notebookreview.com/showthread.php?p=3675644") and tried this command... 
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
still with no luck.

And with all my newbian copy and paste craziness I don't know what step to go back to. I have both the B43 and B43legacy in my /lib/firmware folder  AND I can see my network and others around me, but can't connect to any of them (all WEP)

1. Will multiple firmware cause a problem?
2. What would you do?
3. Which program should I use to actually monitor and connect to my wireless network? (in XP there's a wireless network connection icon AND the Broadcom icon in my system tray, but only one allows me to truly use my wireless... is Ubuntu 8.04 like that?)

Thanks[/SIZE][/FONT]

Having multiple firmware will not cause a problem.  I have the b43/b43legacy and bcm43xx firmware installed and it has not caused any problems.  As for the program to use, I am not too good in providing an option.  I tend to use the Terminal to view things.

Can you post the results of the following from the Terminal:
```
lshw -C network
uname -a
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```
The first command will help confirm the revision of your card and what driver it is trying to use.  The second will help us figure out what kernel you are using along with if it is 32 or 64-bit.  The third command will help us see what drivers are being loaded for your wireless.

---

### Post by zeffuri on 2008-08-12
[FONT="Arial"][SIZE="3"]_lshw -C network_ ......

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
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ca:80:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

_uname -a_   ........

Linux LiNK 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

_lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl_......

b43                   159152  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb    


I thank you for your help, and your patience with my slowness ;]

[/SIZE][/FONT]

---

### Post by Ayuthia on 2008-08-12
> **zeffuri said:**
> [FONT="Arial"][SIZE="3"]_lshw -C network_ ......

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
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ca:80:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

_uname -a_   ........

Linux LiNK 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

_lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl_......

b43                   159152  0 
rfkill                 10128  3 rfkill_input,b43
mac80211              192532  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb    


I thank you for your help, and your patience with my slowness ;]

[/SIZE][/FONT]

Ok.  You are using the b43 driver and it all looks fine.  Do you have a 10 digit hex WEP key?  If so, try the following:
```
sudo iwconfig wlan0 essid <router> key <key>
sudo dhclient wlan0
```
For example, if the name of your router is ubuntu and the key is e42a5c8d4a:
```
sudo iwconfig wlan0 essid ubuntu key e42a5c8d4a
sudo dhclient wlan0
```

---

### Post by zeffuri on 2008-08-12
[FONT="Arial"][SIZE="3"]_zeffuri@LiNK:~$ sudo dhclient wlan0_

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:ca:80:45
Sending on   LPF/wlan0/00:14:a5:ca:80:45
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


So it did something, but what does that mean?
When I click on the network icon on the upper right of the gnome panel I can see my network "Austin Home" and when I click on my network, a box opens asking for a "passphrase" so I entered the network key.

nothing happened. so I switched it from 128 encryption to the 64/128 and entered my network key again.

It seems to be working now.  THANK YOU THANK YOU THANK YOU!
[/SIZE][/FONT]

---

### Post by Ayuthia on 2008-08-12
> **zeffuri said:**
> [FONT="Arial"][SIZE="3"]_zeffuri@LiNK:~$ sudo dhclient wlan0_

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:ca:80:45
Sending on   LPF/wlan0/00:14:a5:ca:80:45
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


So it did something, but what does that mean?
When I click on the network icon on the upper right of the gnome panel I can see my network "Austin Home" and when I click on my network, a box opens asking for a "passphrase" so I entered the network key.

nothing happened. so I switched it from 128 encryption to the 64/128 and entered my network key again.

It seems to be working now.  THANK YOU THANK YOU THANK YOU!
[/SIZE][/FONT]

Unfortunately, it did not do anything that should have made it work.  It just did what you just did.  The difference is that the dhclient command timed out on my command and using the network icon worked.  I think that the only thing that made it work was the switch to 64/128.

---

### Post by jesterthejedi on 2008-08-13
Having trouble connecting to an unsecure network.

  *-network
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:44:1c:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.42.116 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:6f:68:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Linux loverboy 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

b43                   144420  0 
ssb                    34308  1 b43
mac80211              165652  1 b43
input_polldev           5896  1 b43
rfkill                  8592  3 b43,rfkill_input
led_class               6020  2 b43,acer_acpi

sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 15455
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:7e:6f:68:20
Sending on   LPF/wlan0/00:19:7e:6f:68:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Ayuthia on 2008-08-13
> **jesterthejedi said:**
> Having trouble connecting to an unsecure network.

  *-network
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:44:1c:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.42.116 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:6f:68:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Linux loverboy 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

b43                   144420  0 
ssb                    34308  1 b43
mac80211              165652  1 b43
input_polldev           5896  1 b43
rfkill                  8592  3 b43,rfkill_input
led_class               6020  2 b43,acer_acpi

sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 15455
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:7e:6f:68:20
Sending on   LPF/wlan0/00:19:7e:6f:68:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I am not for sure if you did the iwconfig portion before the dhclient:
```
sudo iwconfig wlan0 essid name_of_router
sudo dhclient wlan0
```
Just replace name_of_router with the name of the router that you are trying to conect.

---

### Post by jesterthejedi on 2008-08-13
$ sudo iwconfig wlan0 essid echobase
$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 24805
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:7e:6f:68:20
Sending on   LPF/wlan0/00:19:7e:6f:68:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Newbie1978 on 2008-08-15
I will definitely give a try, hope it works :lolflag:

---

### Post by snakep on 2008-10-11
This worked for me after much difficulty with ndiswrapper.  However, when I reboot it doesn't seem to be working.  When I run "lshw -C network", I find that it is trying to use ndiswrapper with the bcmwl5 driver.  I then run

```
sudo rmmod ndiswrapper 
sudo modprobe b43

```

After this, the wireless card is working.  I then have to connect it to the network, either with the Network Manager or with iwconfig.  

The question is, how do I make these steps automatic?  I added "blacklist ndiswrapper" to /etc/modprobe.d/blacklist, but it doesn't make any difference.  Basically, I just need to load the b43 module but not ndiswrapper.

Thanks,

Jeremiah

---

### Post by Ayuthia on 2008-10-11
> **snakep said:**
> This worked for me after much difficulty with ndiswrapper.  However, when I reboot it doesn't seem to be working.  When I run "lshw -C network", I find that it is trying to use ndiswrapper with the bcmwl5 driver.  I then run

```
sudo rmmod ndiswrapper 
sudo modprobe b43

```

After this, the wireless card is working.  I then have to connect it to the network, either with the Network Manager or with iwconfig.  

The question is, how do I make these steps automatic?  I added "blacklist ndiswrapper" to /etc/modprobe.d/blacklist, but it doesn't make any difference.  Basically, I just need to load the b43 module but not ndiswrapper.

Thanks,

Jeremiah

You will also need to make sure that you have removed ndiswrapper and added b43 in /etc/modules.  The blacklist will tell the system that it should not use the ndiswrapper module and the /etc/modules tells the system what to load.

---

### Post by TheSmokingGNU on 2008-10-11
hey, you tried to help me out the other day, and thank you for that. but do you know anyone that is good with Atheros cards?

---

### Post by Ayuthia on 2008-10-11
> **TheSmokingGNU said:**
> hey, you tried to help me out the other day, and thank you for that. but do you know anyone that is good with Atheros cards?

Sorry, but I am not for sure.  I think that bmartin has created a guide for some of the Atheros cards.  He might be able to help.

---

### Post by TheSmokingGNU on 2008-10-11
tyvm, I will try that then.

---

### Post by snakep on 2008-10-11
> **Ayuthia said:**
> You will also need to make sure that you have removed ndiswrapper and added b43 in /etc/modules.  The blacklist will tell the system that it should not use the ndiswrapper module and the /etc/modules tells the system what to load.

Thanks!  That did the trick.

Jeremiah

---

### Post by Obituaryfreak on 2009-04-17
I have an HP TX 2070ee tablet,preloaded with windows vista,
its wweless worked out of the box,then I moved into Interpid
and the wireless was ok with out asking me even for any driver or firmware stuff.
It worked for 3 month flawlessly until 7 days ago,when I turn it on it couldnt detect the wireless ,,i tried ndiswrapper but t was of no ise
then I decided to upgrde to Jaunty after the first reboot I got my wireless working so I could find that wireless is Broadcom and its version etected on my machine is BCM4312 rev01. I as so happy and I turned off the computer and the day after again there was no wireless.
lwhs -c network doesnt show my wireless and lcpci -nn doesn't show card either  .
I tried your solution as well again nothing.
](*,)
Only the No fluff how to for Hardy  could work for me once but even if I took prosecutions by making the setting permanent again after the reboot it waz gone.

---

### Post by Ayuthia on 2009-04-17
Can you try the following in the Terminal:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
This will allow us to check and see if the Ubuntu supplied module works for you still or not.  If it is not able to find the wl module, please go into System->Administration->Hardware Drivers and see if the Broadcom STA module is enabled.

Your card is a 4312 rev 01 card so it might have the 14e4:4315 chipset (you can verify this by typing lspci -nn in the Terminal).  If it is, then your options are ndiswrapper or wl.  The b43 module does not support this chipset yet.

---


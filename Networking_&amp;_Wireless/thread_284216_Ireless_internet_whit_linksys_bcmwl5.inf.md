---
title: "Ireless internet whit linksys bcmwl5.inf"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by Erik. on 2006-10-25
Hi,
I am complte new into linux.
My dad has a wireless network at home.
I have a wirless pci card of linksys WMP54G pci v2
We use The G type.
Now do i have 2operation systems:
1)Windows
2)Ubuntu 6.06
I am running kernel:2.6.15-27-k7
I have installed ndiswrapper from automatrix.
I have installed driver:bcmwl5
Nidswrapper works but my internet not.

1) ndiswrapper -l 
       Installed ndis drivers:
bcmwl5          driver present, hardware present



2)My interface file:
      # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0


iface eth0 inet static
address 172.27.183.213
netmask 255.255.255.0
gateway 172.27.183.103

iface eth1 inet dhcp

auto eth1

Whit iwconfig:
    lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I have etho and eth1
eth0 is for my fireless internet and eth1 is for my cable...

From my internet:   
ESSID:Pisv184ldk
Channel 11
Security code WEP
Key 3
Acces key: 13 48 19 C6 11
IP 172.27.183.213
subnet 255.255.255.0
Gateway 172.27.183.103
DNS server 10.0.0.138

When i do ifdown eth0 i got this:
ifdown: interface eth0 not configured

i have configured manualy!

When i do ifup eth0 :
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up eth0.

I realy do not know what to do!
I have read many topics and done many things but nothing will help:(

I hope someone can help me to make my wireless iternet so i can put my pc upstairs...

Gr Erik.

---

### Post by wieman01 on 2006-10-25
Ok, please open "interfaces":
> sudo gedit /etc/network/interfaces
Then **_replace_** the contents with this:
> auto eth0
iface eth0 inet static
address 172.27.183.213
netmask 255.255.255.0
gateway 172.27.183.103

auto wlan0
iface wlan0 inet dhcp
The restart the computer (that's best) and scan for your network:
> iwlist wlan0 scan
Please post the output.

---

### Post by Erik. on 2006-10-25
Hi,
```

wlan0     Interface doesn't support scanning.

```

---

### Post by Erik. on 2006-10-25
Hi,
I have found a funny thing:
I have a screen saver thats a sonar...
It displays ejp.lan and the milisecons under it.
Is that my wireless internet?? or is it fake?

---

### Post by wieman01 on 2006-10-25
Don't know anything concerning your screen-saver.

Nonetheless let's start all over again. Please follow these first instructions & post the results whenever possible:

1. Open "interfaces":
> sudo gedit /etc/network/interfaces
2. Paste this:
> auto eth0
iface eth0 inet static
address 172.27.183.213
netmask 255.255.255.0
gateway 172.27.183.103

auto ra0
iface ra0 inet dhcp
3. Do another scan:
> iwlist ra0 scan
"ra0" is the native Linux driver for your card. If this does not work we embark on "ndiswrapper"...

---

### Post by wieman01 on 2006-10-25
Rather than "ndiswrapper" we will try to install the native Linux driver first, if it has not been installed yet.

Basically we will follow this howto: [http://ubuntuforums.org/showthread.php?p=1409752#post1409752]("http://ubuntuforums.org/showthread.php?p=1409752#post1409752")

I will help you there, don't worry.

---

### Post by Erik. on 2006-10-26
Hi,
do i need to use that driver or my own driver???
I will do everything whit that howto.
i will post my results here


EDIT:Do i need to use rao or eth0??
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="*******"

I use WEP not that other...
Or do i only need to to everything and then you help me do not understand for 100%

---

### Post by wieman01 on 2006-10-26
1. Have you installed the Linux driver yet?
2. Please show me your interfaces file. The device we are now going to use is "ra0".
3. Please turn off WEP for the time being. It's easier this way.

---

### Post by Erik. on 2006-10-26
Hi,
 I will do that things and i hope it will work.
Every problem that i have will posted here so other people whit the same problem can get a solution...

---

### Post by Erik. on 2006-10-26
Hi,
I have done everything and i do not have any error!!!
What can i do now?

---

### Post by wieman01 on 2006-10-26
Please show me your interfaces file:
> sudo gedit /etc/network/interfaces
[COLOR="Red"]DHCP enabled & WEP disabled (= router)?[/COLOR]

---

### Post by Erik. on 2006-10-26
Hi,
I have set no wireless security so you do not need a key..
I have this interface:
```


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

auto ra0

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid  Pisv184ldk
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK= key
pre-up ifconfig ra0 up

```

---

### Post by wieman01 on 2006-10-26
Please replace the contents of "interfaces" and paste this (you don't need anything else right now):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid [COLOR="Red"]Pisv184ldk[/COLOR]
The restart the network:
> sudo ifdown ra0
sudo ifup ra0
Then scan:
> iwlist ra0 scan
Post the results please.

---

### Post by Erik. on 2006-10-26
Hi,
When i do:
sudo ifdown ra0 i get : ifdown: interface ra0 not configured

When i do:
sudo ifup ra0: Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ra0.

EDIT:
Whit that driver installed i have a new option at the upper right of my schreen at network...
It only can not connect to my router

---

### Post by wieman01 on 2006-10-26
What does your interfaces file look like now? Have you copied my stuff? If yes, then the driver has not installed correctly. Have you followed the steps in the tutorial I have given you?

---

### Post by Erik. on 2006-10-26
This is my interface now:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid Pisv184ldk

And yes i did every step into that HOW TO and i have no errors.

---

### Post by wieman01 on 2006-10-26
Have you done all this?
> wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod 
And what does this file say?
> sudo gedit /etc/modprobe.d/rt2500

---

### Post by Erik. on 2006-10-26
I have realy done it
here is the file:
alias ra0 rt2500

---

### Post by wieman01 on 2006-10-26
Ok, I really believe you. :-)

Please try to scan:
> iwlist ra0 scan

---

### Post by Erik. on 2006-10-26
ra0       Interface doesn't support scanning.

---

### Post by wieman01 on 2006-10-26
That means that the driver is not working properly. Have you done a restart since you installed it? 

And what does this command say?
> lshw

---

### Post by Erik. on 2006-10-26
it says:
```

-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-network DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 6
             bus info: pci@05:06.0
             logical name: eth0
             version: 03
             serial: 00:0f:66:1d:6e:b4
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-27-k7 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:d8000000-d8001fff irq:58
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          logical name: eth1
          version: a3
          serial: 00:13:d4:17:53:43
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=full ip=172.27.183.220 link=yes multicast=yes port=MII speed=100MB/s
          resources: iomemory:d8100000-d8100fff ioport:b000-b007 irq:217

```

---

### Post by wieman01 on 2006-10-26
Ok, is there a button that you can press to enable your wireless device? Or unplug it & plug it in again...

Need to hop off line now... Continue tomorrow.

---

### Post by Erik. on 2006-10-26
I don't have any buttons on my divice
I have at th upperright of my screen an new option fir wireless internet but i can not conect whit it..

See you tommorow

---

### Post by wieman01 on 2006-10-26
You could also try to use Gnome's Networking Applet... Disable & enable the device "wlan0" and see if it starts working. Sometimes the devices are turned off by default.

Continue tomorrow then.

---

### Post by Erik. on 2006-10-26
Where can i find it and when it is installed where to find?

---

### Post by wieman01 on 2006-10-26
> **Erik. said:**
> Where can i find it and when it is installed where to find?
You find it somewhere in the Gnome menu... Not sure though as I am using KDE, not Gnome. But it says something like "Networking" or similar...

---

### Post by Erik. on 2006-10-27
Hi,
In the menu Internet i have found: Knetwork manager or something like that.
Now when i start it i can try to connect to my wireless internet but i have tried it 7 times but i can not connect to it.
Signal is -1

---

### Post by wieman01 on 2006-10-27
Hi Erik, 

Are you using KDE or Gnome? If you have found KNetworkManager, then you need to uninstall it. It will interfer with our setup...

To achieve that please do this from command line:
> sudo apt-get remove network-manager knetworkmanager network-manager-gnome wifi-radar
That done, _restart the computer_.

Then restart your network & do one more scan (post the output as usual):
> sudo /etc/init.d/networking restart
> iwlist ra0 scan

---

### Post by Erik. on 2006-10-27
Hi,
This is the output of sudo /etc/init.d/networking restart:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:d4:17:53:43
Sending on   LPF/eth1/00:13:d4:17:53:43
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.0.0.138 port 67
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ra0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:d4:17:53:43
Sending on   LPF/eth1/00:13:d4:17:53:43
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 10.0.0.138
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.138
bound to 10.0.0.152 -- renewal in 3571 seconds.


This is the output of iwlist ra0 scan:
ra0       Interface doesn't support scanning.

---

### Post by nbound on 2006-10-27
Ive created a HOWTO for this card here: [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809) :D

---

### Post by wieman01 on 2006-10-27
> **nbound said:**
> Ive created a HOWTO for this card here: [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809) :D
Great! But then you're not using the native Linux driver. May I know why? I have ditched as well & went for "ndiswrapper" because the Linux driver has fairly poor WPA1/WPA2 support... Could not get it working. What's your reason?

---

### Post by wieman01 on 2006-10-27
Erik:

The guide is definitely what you ought to try if we don't get the native driver to work.

---

### Post by Erik. on 2006-10-27
Hi,
When i have done this HOW TO my option of wireless connection disapeared
i don't think it help for me,

Wieman could you help me?

---

### Post by wieman01 on 2006-10-27
Hi Erik, 

Do you have an **AIM** account? My alias is "wieman001"...

---

### Post by nbound on 2006-10-27
> **wieman01 said:**
> Could not get it working. What's your reason?

This card doesnt work with the native driver fullstop.

Its the only one that doesnt in the bcm43xx series apparently... else i'd be using the native driver too

---

### Post by wieman01 on 2006-10-27
> **nbound said:**
> This card doesnt work with the native driver fullstop.

Its the only one that doesnt in the bcm43xx series apparently... else i'd be using the native driver too
Oh man... Thanks for telling us. :-) Honestly I had a very similar problem so I am glad you sent us a note.

I'll guide Erik through your guide then, mate.

---

### Post by nbound on 2006-10-27
> **wieman01 said:**
> Oh man... Thanks for telling us. :-) Honestly I had a very similar problem so I am glad you sent us a note.

I'll guide Erik through your guide then, mate.

No worries... :D 

I had similar problems with Dapper took me about a week to find out why it wouldnt go. ](*,)

---

### Post by wieman01 on 2006-10-27
> **nbound said:**
> No worries... :D 

I had similar problems with Dapper took me about a week to find out why it wouldnt go. ](*,)
Haha! D@#$ it! Same here... Got a WUSB54G and it was such a PITA. Took me about a week as well. Felt completely "Lights are on, nobody home."

---

### Post by Erik. on 2006-10-27
Hi,
I will make an AIM account...

---

### Post by wieman01 on 2006-10-27
Hi Erik, 

I think that your problem is that your card is turned off. Please check:
> lspci
Does it list your card and say "Disabled" or similar somewhere? Also try:
> lshw
I am sure that's the problem. Please also boot Windows & try to enable the connection there, then restart & boot Ubuntu. Try another scan...

---

### Post by Erik. on 2006-10-28
Hi,
i have take a look but my wireless card has already enabled in windows,

Can linux enable the wirless device?
How can i look if it is enabled or disabled?

---

### Post by wieman01 on 2006-10-28
EriK:

I have found some suspicious lines while you were posting "lshw":
>  **[COLOR="Red"]*-network DISABLED[/COLOR]**
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 6
             bus info: pci@05:06.0
             logical name: eth0
             version: 03
             serial: 00:0f:66:1d:6e:b4
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-27-k7 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:d8000000-d8001fff irq:58
This says that your device has been recognized but is DISABLED. Any idea why? Is any light (LED) on the device lit?

---

### Post by Erik. on 2006-10-29
Hi,
I don't know why it is disabled but how can i enable it?

The problem is that in windows my wireless card was enabled not disabled...
How can i set it on into linux??

---

### Post by wieman01 on 2006-10-29
Erik:

Are you online?

---

### Post by wieman01 on 2006-10-29
Erik:

Can you please post the contents for the dmesg log-file:
> sudo gedit /var/log/dmesg
I think there is a known issue with your card.

---

### Post by wieman01 on 2006-10-29
Now, Erik, I think I may know what the problem is. The driver for your card has an issue. So what we are now going to do it remove the existing driver & load a new one which can be found here:

[http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz]("http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz")

Now follow these steps:

1. Unload the current driver:
> sudo ndiswrapper -e bcmwl5
2. Unzip new driver archive:
> sudo mkdir /lib/windows
cd /lib/windows/
sudo tar -xvf [COLOR="Red"]/path/to/your_zip_file/[/COLOR]SP23107A.tar.gz
[Please replace [COLOR="Red"]/path/to/your_zip_file/[/COLOR] with the corresponding folder in which you find the zip archive you have just downloaded.]

3. Load new driver:
> sudo ndiswrapper -i /lib/windows/SP23107A/bcmwl5.inf
4. Another modprobe:
> sudo modprobe ndiswrapper
Check if the LED is lit now. If not restart the computer & do another scan:
> iwlist wlan0 scan
What's the output?

---

### Post by Erik. on 2006-10-30
Hi,
i will try it i hope it will work..

---

### Post by wieman01 on 2006-10-30
Erik:

Try my staff and if it does not work, get in touch with another user who has just got his Broadcom working. His thread can be found here: [http://www.ubuntuforums.org/showthread.php?t=288514]("http://www.ubuntuforums.org/showthread.php?t=288514")

---

### Post by wieman01 on 2006-10-31
One last note: Your problem definitely relates to the driver you're using. I have seen it in a couple of other threads... driver disabled, LED not lit, etc. All could be resolved by using the right driver (AND driver version).

So don't give up, buddy.

---

### Post by Erik. on 2006-10-31
Hi,
i will try it as fast as i can...
I have set my pc upstairs so i don't have any cable here...
I am now at windows using my wireless internet.

Thank you very much for all your help!!

---

### Post by wieman01 on 2006-10-31
My pleasure. With a bit of patience we'll get is solved soon, I am pretty sure.

_**EDIT:**_
If you still have problems, we can have another chat session via AIM.

---

### Post by wieman01 on 2006-11-01
Erik:

Just came across this one & apparently this relates to your card (BCM4306):

[https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983/comments/2]("https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983/comments/2")

Basically upgrade to "ndiswrapper" version 1.8:
> sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper

---

### Post by TheRitz on 2007-10-28
This method worked great for me. I installed a Broadcom 4306 wifi card in my Dell D600 using this procedure and got it going in a flash where as some other tips on Ubuntuforums.org did not work for me at all. Thanks!

---


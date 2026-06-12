---
title: "wifi devices"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by marshall.robert on 2007-02-12
hi, ive been trying for ages now to get my wifi working with my current usb dongle, i cant be arsed any more, anyone know of any pcmcia/usb wifi adapters that work out the box, or with hardly effort involved?

much appreciated

-rob

---

### Post by ukripper on 2007-02-12
Here are some links :


[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)



[http://ralink.rapla.net/](http://ralink.rapla.net/)


worked for me out of the box on Edgy

Airlink 
 awll3026 
 zd1211b 
 ? 
 Yes 
 Yes
 Works out of the box on Edgy using network-manager

---

### Post by marshall.robert on 2007-02-12
im assuming that any ralink chipset will work with xubuntu?

-rob

---

### Post by ukripper on 2007-02-12
> **marshall.robert said:**
> im assuming that any ralink chipset will work with xubuntu?

-rob



Depends on the chipset, it could work out of the box straight away or you might need to use ndiswrapper to wrap the chipset drivers which won't be that tough as I said all depending on the chipset. What chipset you have?

---

### Post by marshall.robert on 2007-02-12
thanks very much for the quick replies.

right now i have the belkin f5d7050, i think its version 4 and im not sure what chipset it has exactly,  but i have used ndiswrapper and got the drivers that where on the cd ok, ndiswrapper tells me that the driver and the hardware are found, but when i look into the network settings of xubuntu is only shows my built in dialup modem.....

-rob xx

---

### Post by gradedcheese on 2007-02-12
Please run "ifconfig" and "iwconfig" in the Terminal and post the output here.  Also post the contents of the file /etc/network/interfaces

---

### Post by marshall.robert on 2007-02-12
ok, i will in a few mins, im doing a fresh install of xubuntu so i can start from scratch with this, i will edit this post with the details when it has finished installing...

here it is:

ifconfig:
lo   link encap:local loopback
     inet addr:127.0.0.1   mask:255.0.0.0
     UP LOOPBACK RUNNING MTU:16436   Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0 (0.0b)   TX bytes:0 (0.0b)

iwconfig:
lo no wireless extensions

it gives me the same with and without ndiswrapper

and the interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan inet dhcp

-rob

---

### Post by ukripper on 2007-02-13
Try following meanwhile,

According to your config, wlan0 is not configured and you need to go in network manager to configure it, 
Put you ESSID(which is your wireless name you used in windows xp) and 

put WEP key enable, auto DHCP and enable network card. 

Then install wlassistant or use wifiradar, I personally use wlassistant although it is kde  app, you can use it by issuing **sudo wlassistant **from terminal window once installed and all available networks will show up in there once configured through network manager, all you will need to configure wlassiatnt with same ESSID and WEP you used in network manager and don't forget to check on check box ASCII

Refresh your network using following:

$ sudo ifdown wlan0
$ sudo ifup wlan0

go to wlassistant and connect again.

if it doesn't work
paste your iwconfig here and paste what is in the follwoing file /etc/network/interfaces using sudo gedit /etc/networks/interfaces,

---

### Post by marshall.robert on 2007-02-13
there are alot of dependancies for it....

here goes.....

when its done ill post :)

thanks very much for yout support :)

------------------------------------------------------------------------------

i have a vicous cycle here.. 2 of the dependancies for this wlassistant depend on each other, they are kdelibs-bin and kdelibs4

kdelibs-bin depends on kdelibs4 and kdelibs4 depends on kdelibs-bin

how do i get around this?

-rob

---

### Post by ukripper on 2007-02-13
> **marshall.robert said:**
> there are alot of dependancies for it....

here goes.....

when its done ill post :)

thanks very much for yout support :)

------------------------------------------------------------------------------

i have a vicous cycle here.. 2 of the dependancies for this wlassistant depend on each other, they are kdelibs-bin and kdelibs4

kdelibs-bin depends on kdelibs4 and kdelibs4 depends on kdelibs-bin

how do i get around this?

-rob


Make sure you are connected to internet via your ethernet cable and eth0 is enabled and working properly.

update using $ sudo apt-get update
$ sudo apt-get upgrade

try **$ sudo aptitude install wlassistant** which should install all the needed depedencies required by you. looks like you have broken dependencies not linking to your installed packages.

if that doesn't work then try using synaptic manager or manually download wlassistant and install deb package.


Also, I assume that you have managed to configure network manager if not then first you need to do that, as wlassistant will only show available networks only if you have your network card enabled and configured.

---

### Post by marshall.robert on 2007-02-13
my laptop doesnt have a working ethernet cable, the manufacturer didnt enable it, and it wasnt recognised under xp when it was on, nor does linux see it...

i try the **sudo aptitude install <path to wlassistant package>** and **sudo atitude wlassistant** and they both say:

Reading package lists... Done
Building dependancy tree
Reading state information... Done
Building tag database... Done
Couldnt find any package whose name or description "<folder where package is held>"
No packages will be installed, upgraded, or removed,
0 packages upgraded, 0 newly installed, 0 to remove and 0 upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

i cant get anything throught the package manager, and i downloaded the package and was doing it manually when i got the vicous cycle

if by network manager you mean 'network settings' then network manager doesnt have anything in it but my builting dialup modem....

---

### Post by ukripper on 2007-02-13
Can you post output of iwconfig and lspci here?

Also, paste contents of /etc/network/interfaces

---

### Post by marshall.robert on 2007-02-13
iwconfig:
lo        no wireless extensions.

sit0      no wireless extensions.

lspci:
00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev 0a)
00:09.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1211
00:0f.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev 20)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] (rev 09)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)


*its a usb device so i thought this would be good*
lsusb:
Bus 001 Device 033: ID 050d:705c Belkin Components 
Bus 001 Device 001: ID 0000:0000 

interfaces: 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BTVOYAGER2100-76
wireless-key s:<my network key>

---

### Post by ukripper on 2007-02-13
> **marshall.robert said:**
> iwconfig:
lo        no wireless extensions.

sit0      no wireless extensions.

lspci:
00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev 0a)
00:09.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1211
00:0f.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev 20)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] (rev 09)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)


*its a usb device so i thought this would be good*
lsusb:
Bus 001 Device 033: ID 050d:705c Belkin Components 
Bus 001 Device 001: ID 0000:0000 

interfaces: 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BTVOYAGER2100-76
wireless-key s:<my network key>



I can't see wlan0 in your iwconfig? Looks like you need correct drivers to configure it using ndiswrapper.

Follow following guide to configure your drivers first and alias with wlan0:

If ver04:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29%20?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29%20?highlight=%28WifiDocs%2FDevice%29)


if ver03:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?a%20ction=show](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?a%20ction=show)

after above, make sure wlan0 is associated with drivers otherwise it won't work.

---

### Post by marshall.robert on 2007-02-13
i used the drivers on the cd with ndiswrapper, i would have thought they worked... maybe not...

you recon i could use a usb adsl modem with linux to do this sudo apt-get update stuff?


-rob

---

### Post by ukripper on 2007-02-13
There is no Alias between your wlan0 to adapter's MAC address. 

I really could only suggest you to re-install drivers follwoing the above guide and looking at your post earlier I didn't udnerstand what you mean by not having ethernet cable enabled by manufacturer? Do you mean to say there is no PCI ethernet network card present in your laptop?

---

### Post by marshall.robert on 2007-02-13
well, its a bit wierd, cos the port itsself exists in the side of the laptop, but it is covered with a rather annoyingly difficult to pull off cover (have to use a knife and brute force), and when you plug it in the indicator on the router doesnt blink, so it cant be active, and it wasnt seen in xp when i had it, i recon the manufacturer has been a bit lazy and not activated it for this model (compaq presario 1690)

so, in basic, yes there is a card, but it dont work, never did.

and what do you think about a usb adsl modem, recon it will work?

-rob

---

### Post by ukripper on 2007-02-13
> **marshall.robert said:**
> well, its a bit wierd, cos the port itsself exists in the side of the laptop, but it is covered with a rather annoyingly difficult to pull off cover (have to use a knife and brute force), and when you plug it in the indicator on the router doesnt blink, so it cant be active, and it wasnt seen in xp when i had it, i recon the manufacturer has been a bit lazy and not activated it for this model (compaq presario 1690)

so, in basic, yes there is a card, but it dont work, never did.

and what do you think about a usb adsl modem, recon it will work?

-rob

I can't suggest you adsl modem as I have not tested using modem as yet. If you had ethernet card things would be lot simpler. I can only suggest you to go for a decent pcmcia card from the list i posted earlier such as:  Linksys  WMP54G (Ver.4) or Linksys 
 WMP55AG  Atheros . look into the list I posted. Without internet it would be bit tricky to configure wireless especially in your case which has not ethernet conn.

---

### Post by marshall.robert on 2007-02-13
yeah, it is a bit tricky, im gonna try the adsl modem (when i find it) and if things still dont work then ill probably post.

many many thanks for you support

-rob xx

---


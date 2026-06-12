---
title: "Edgy &amp; WUSB54g V4"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-12-23
Hi,

Seems "Edgy" has built in support under "Raus0".

I CAN get this unit to connect under the Ubuntu Edgy native driver. RT2570...Raus0...with no WEP or WPA:) .

I CAN'T get this unit to show a wlan0 by using Ndiswrapper/Linksys RT2500.inf/Blacklist...etc (I've read ALL the Dapper threads on WUSB54G, WPA, Configuration, etc. & Ubuntu member Wieman01's threads)  I give up in Edgy!!!!](*,) 

*************************************************************************************************************

My question...:-k 

In "EDGY" can someone help me with the steps how to enable WPA, or WEP & the sudo gedit /etc/network/interfaces configuration steps....under the native driver rt2570(Raus0) since I can get on the internet with this, but unencrypted. 

Dlink wireless router with.......
a) One dedicated channel (for example...6)
b) Hidden SSID enabled
c) DHCP enabled 
d) WEP options include 64 or 128bit/open or shared key/4 passphrase lines appear. (I'd like at least 128bit or ultimately....WPA PSK TKIP. Just not sure what to add under "Raus0
 in sudo gedit /etc/network/interfaces:confused: )    

Thanks

---

### Post by wieman01 on 2006-12-23
Not sure if the native driver supports WPA, but please try this:
> auto [COLOR="Blue"]rausb0[/COLOR]
iface [COLOR="Blue"]rausb0[/COLOR] inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto [COLOR="Red"]WPA[/COLOR]
wpa-pairwise [COLOR="Red"]TKIP[/COLOR]
wpa-group [COLOR="Red"]TKIP[/COLOR]
wpa-key-mgmt [COLOR="Red"]WPA-PSK[/COLOR]
wpa-psk <your_hex_key> 
Please generate the PSK as explained in [[COLOR="Blue"]this howto[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=318539"). This configuration is as follows:

1. No broadcast of ESSID.
2. WPA with TKIP.
3. Interface "rausb0".

---

### Post by DapperMe17 on 2006-12-26
Thanks Wieman,

I will try it.


By the way, I have read and tried, in detail, the steps you offered another member, the one that guided through the steps of Version 4, and it turned out he/she had Version 2.  I followed that thread to a tee, and have had the very same outcome (no connection), except for I do not have a "sit1" listed and I don't have V2. OPc course, I am sitting with no "wlan" listed, but do have V4.

---

### Post by Floppyjoe on 2006-12-26
I have this device installed on one of my computers and I believe i blacklisted the native driver and used ndiswrapper. The device still shows up as rausb something or other and i used the wext driver to activate WPA encryption using wpa_supplicant.

---

### Post by wieman01 on 2006-12-26
Funny, but another guy has the same problem. Look at this:

[http://ubuntuforums.org/showthread.php?t=316917&page=3]("http://ubuntuforums.org/showthread.php?t=316917&page=3")

---

### Post by DapperMe17 on 2006-12-26
Hi Wieman,

I could not connect WPA, using your istructions, with the native driver:( 


However, I followed your min-step list below....I've posted my results under each.

Unfortunately, I'm still not connecting:( 
(Ethernet disconnected/no firestarter/no networkmanager/etc)
[I]
Can you help me get 'ole V4 running?


Mini-howto:
[I]
[B]*1. Install "ndiswrapper":*

Quote:
sudo apt-get install ndiswrapper-utils[/I]
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 dhcdbd
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.1
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/47.4kB of archives.
After unpacking 250kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 89947 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.1.
Unpacking ndiswrapper-utils-1.1 (from .../ndiswrapper-utils-1.1_1.1-5_i386.deb) ...
Selecting previously deselected package ndiswrapper-utils.
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.1-5_all.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
Setting up ndiswrapper-utils-1.1 (1.1-5) ...

Setting up ndiswrapper-utils (1.1-5) ...

[[B]I]2. Open "blacklist" file:

Quote:
sudo gedit /etc/modprobe.d/blacklist
[/I][/B]


[B][I]3. Add this line & save:

Quote:
blacklist rt2570[/I][/B]

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist rt2570

**4. Get the latest(!) Windows driver for your card.**

***V4 from Linksys website

[B]5. Copy the driver files (*.sys, *.inf, etc.) to your home folder:[/I]

[I]Quote:
/home/your_user/WUSB54GV4[/B]

****Ok

[B]6. Install Windows driver:

Quote:
sudo ndiswrapper -i /home/your_user/WUSB54GV4/rt2500usb.inf

7. Check if driver has installed correctly:

Quote:
ndiswrapper -l[/I][/B]

rt2500usb       driver present, hardware present

[[B]I]8. Load new driver module (may not be necessary):

Quote:
sudo depmod -a
sudo modprobe ndiswrapper

9. Loading module at startup:

Quote:
sudo ndiswrapper -m[/I][/B]

modprobe config already contains alias directive

[[B]I]10. Restart computer & scan for networks:

Quote:
iwlist scan[/I][/B]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

[[B]I]Quote:
sudo gedit /etc/network/interfaces[/I]
[/B]
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid *******


[B]*sudo gedit /etc/modprobe.d/ndiswrapper*
[/B]

alias wlan0 ndiswrapper



I thought you said this thing was a breeze to set up;)

---

### Post by wieman01 on 2006-12-26
Perhaps I was mistaken when I said that setting it up was a piece of cake... ;-)

The scanning does not return any results. Are you sure you have installed the correct driver? Does is really say V4 on the back of the device? Is the LED lit?

---

### Post by Floppyjoe on 2006-12-26
You also need to add the word ndiswrapper to /etc/modules.
```
sudo gedit /etc/modules
```
add ndiswrapper to end of file, then save and exit.
reboot and see if the ndiswrapper module loads then at startup.

The following does not enter ndiswrapper into the above file for me:
> Quote:
sudo ndiswrapper -m

i tried it wth the same result as shown here and when I checked the above file there was no reference to ndiswrapper, however I may have forgotten to use sudo.

modprobe config already contains alias directive

---

### Post by wieman01 on 2006-12-26
> sudo ndiswrapper -m
This is the same as editing "/etc/modules"... As reference can be found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by DapperMe17 on 2006-12-31
Hey guys. Thanks for the input...just back to the forum. Here's what I have...


** sudo gedit /etc/modules**


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper



...and...


** sudo ndiswrapper -m**


modprobe config already contains alias directive





Wieman....Yes, the device is V4, as indicated under the sliding cover on the unit. The unit works with the native rausb0 driver, and the lights are on.

I have tried both the V4 driver from the CD, as well as the driver from Linksys.

I'm using Edgy, v6.10....could this be the problem?

---

### Post by DapperMe17 on 2006-12-31
UPDATE!!!!!!!!!!!!!!!


Just got the unit working under Ndiswrapper!!!:D 

Seems as if Edgy requires Ndiswrapper-utils 1.8....NOT....Ndiswrapper-utils.

After using Synaptic to uninstall all Ndiswrapper, then install Ndiswrapper-util 1.8 and loading the rt2500 driver, a simple network scan identified my wireless network connection as active:D 

I will continue with WPA encryption & let you know the results.

Wieman...I eat my words about it being a difficult problem:eek:

---

### Post by wieman01 on 2006-12-31
Good luck with WPA. That - at least - should be way simpler. To begin with, follow the howto in my signature.

---

### Post by DapperMe17 on 2007-01-01
WPA1 successfull:D..... w/hidden ESSID 


As far as the **sudo gedit /etc/network/interfaces**...


I simply followed your WPA link for WPA1(SSID broadcast)
But, because I chose to "hide the ESSID", all I did was to change one line...


Use [COLOR="Red"]wpa-ap-scan 2[/COLOR], instead of [COLOR="Blue"]wpa-ap-scan 1[/COLOR] 


I then enabled my wireless connection in System/Administration/Networking & typed in my network name(which is actually the same as the hidden ESSID).

Wahlaaaaah...WPA1 encryption working flawlessly:p


Thank you Weiman01 for your time & consideration...I'm thinking of adding a streamlined how-to for WPA1, to your fine instructions.

---

### Post by acegolfer on 2007-01-02
I got WUSB54G V4 working in Edgy within WPA(TKIP) environment

1. add "blacklist rt2570" to /etc/modprobe.d/blacklist
2. install ndiswrapper utils 1.8 (not 1.1) from synaptic
3. copy and save 3 rt2500usb.* Windows XP drives to your preferred folder.
4. "sudo ndiswrapper -i rt2500usb.inf"
5. "sudo ndiswrapper -l" to see whether the driver and hardware are working
6. sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

7. Next choose either 1) network-manager or 2) configuring /etc/network/interfaces
7.1.a. From add/remove program, install network-manager
7.1.b. reboot and when network manager starts automatically, it will ask your password key for WPA. Then you should get the internet.

7.2.a Edit /etc/network/interfaces and add (or modify)
auto wlan0
iface wlan0 inet dhcp
       pre-up wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -Bw
7.2.b. create /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="XXXX"
       psk="XXXXXXXX"
       key_mgmt=WPA-PSK
       proto=WPA
       pairwise=TKIP
#psk=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
}

There are pros and cons between 7.1 and 7.2

7.1 network-manager
pro: easy and can reconnect after unplugging the USB. (I share this WUSB54G with another XP)
con: takes long to boot; in the middle of init stage, it stops for 30 seconds in the middle of the bar

7.2 configure manually
pro: boots fast
con: if unplug USB, can't reconnect. Needs to reboot. (Please correct me if I'm wrong)

---

### Post by wieman01 on 2007-01-02
Glad it worked for you. I would use WPA2 instead of WPA1 as it is more secure.

---

### Post by hasuob on 2007-02-17
I could use some help with this. I had my adapter working just fine (Wireless USB Linksys WUSB54GC) on my desktop running Dapper. I upgraded last night and now I am no longer able to connect to my network. I can't even see a network exists. When i do ndiswrapper-1.8 -l it returns:
```
rt73 driver installed, hardware present
```
which is what I saw when using the WUSB54G and Dapper tutorial in this forum.

Will I have to uninstall ndiswrapper and redo it from the start of that tutorial or is there something that I should try first. I could use some advice on how to uninstall this stuff too because when I try doing the command
```
sudo ndiswrapper -e rt73
```
to re-install it, it gives no errors, but next time i -l, rt73 is still listed.
Any help is appreciated since I'm pretty inept when it comes to Linux

---

### Post by bilbothebaggins on 2007-02-22
> **acegolfer said:**
> I got WUSB54G V4 working in Edgy within WPA(TKIP) environment

1. add "blacklist rt2570" to /etc/modprobe.d/blacklist
2. install ndiswrapper utils 1.8 (not 1.1) from synaptic
3. copy and save 3 rt2500usb.* Windows XP drives to your preferred folder.
4. "sudo ndiswrapper -i rt2500usb.inf"
5. "sudo ndiswrapper -l" to see whether the driver and hardware are working
6. sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m


I wanted to share that I finally got my Linksys WUSB54Gv4 to run with Edgy along the lines described here ... I did blacklist, use ndis utils 1.8 etc.

My interfaces file looks like this:
#
# Network interfaces
#
# To restart and apply changes:
# > sudo /etc/init.d/networking restart
# > sudo ifdown -a
# > sudo ifup -a

# Loopback device:
auto lo
iface lo inet loopback

# First wired device:
#auto eth0
#iface eth0 inet dhcp

#
# Configuration with ndiswrapper:
# wlan0 device
#-Generated by wpa_passphrase <ESSID> <PASSPHRASE> ...
#
auto wlan0
iface wlan0 inet dhcp
#pre-up ifconfig wlan0 down
#pre-up ifconfig wlan0 up
#pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid <my essid>
pre-up iwconfig wlan0 mode Managed
wpa-driver wext
wpa-conf managed
wpa-ssid <my essid>
wpa-ap-scan 1 *(I'm not sure if it makes a difference using 1 or 2 ...)*
wpa-prot WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <my passphrase-hex>
#pre-up ifconfig wlan0 up


And now I'm crossing my fingers that it'll also work after I've rebooted this box :)

cheers,
Martin

---

### Post by wieman01 on 2007-02-23
> wpa-ap-scan 1
"1" stands for ESSID broadcast enabled, "2" for hidden ESSID.

---

### Post by astrobit on 2007-06-03
[B]uhhh...
i've followed all the steps in this thread

and now i can see the interface active in the system... i see the WUSBG leds blinking...

but i cant stablish a connection...[/B]
--------------------------------------------------------------------------------------
leo@nava:~$ ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2570)
leo@nava:~$ 
--------------------------------------------------------------------------------------
leo@nava:~$ sudo gedit /etc/network/interfaces
||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth0 inet static
address 192.168.2.84
netmask 255.255.255.0
gateway 192.168.2.1


iface wlan0 inet static
wireless-essid astrobit
address 192.168.2.85
netmask 255.255.255.0
gateway 192.168.2.1


auto eth0

auto wlan0
--------------------------------------------------------------------------------------
[B]
and in the network connections i see wlan as
wlan0:avahi

i use static IPs in my router...

i cant make it work... any ideas?[/B]

---

### Post by brucetan on 2008-02-24
> **astrobit said:**
> [B]uhhh...
i've followed all the steps in this thread

and now i can see the interface active in the system... i see the WUSBG leds blinking...

but i cant stablish a connection...[/B]
--------------------------------------------------------------------------------------
leo@nava:~$ ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2570)
leo@nava:~$ 
--------------------------------------------------------------------------------------
leo@nava:~$ sudo gedit /etc/network/interfaces
||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth0 inet static
address 192.168.2.84
netmask 255.255.255.0
gateway 192.168.2.1


iface wlan0 inet static
wireless-essid astrobit
address 192.168.2.85
netmask 255.255.255.0
gateway 192.168.2.1


auto eth0

auto wlan0
--------------------------------------------------------------------------------------
[B]
and in the network connections i see wlan as
wlan0:avahi

i use static IPs in my router...

i cant make it work... any ideas?[/B]


Hello,

From your interfaces file, it does not have any WEP/WPA, etc.  Are you sure not using any wireless encryption at your wireless router?  

Also, please try to do the following teminal command:

> iwlist scan 

You should use if your wireless adapter see any access point found.  If not and your wireless router is on, then your wireless is either not working or its driver is not configured and you check with the following command:

> lshw -C network

> ndiswrapper -l

> iwconfig

Hope these help!


Bruce

---


---
title: "Not sure what I've done.  No wired connection available."
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by sippinondew on 2008-05-04
I'm pretty much a newb and have no idea what I've done.

I've just installed Hardy and after having a few problems with my wireless connection, I've managed to get it working, but in the process I've killed my wired connection.

When I click on the network icon at top right, no wired connection is displayed at all.

I'm running a Dell Inspiron 1501 with the current distro of Ubuntu.

Any advice would be greatly appreciated.

Thanks.

---

### Post by kwacka on 2008-05-04
First try going to System --> Administration --> Network

Can you see wired connection & adjust properties.

If not come back here.

---

### Post by sippinondew on 2008-05-04
The wired connection is in the list.  I have it set to autoconfig.

However, when I plug in my ethernet cable, there is no option to connect in my networks drop down.

---

### Post by kwacka on 2008-05-04
Open terminal & type ```
ifconfig
```

this will show you network adapters, the wired connector is **probably** eth0, assuming that it is type:

Type ```
sudo ifdown eth0
```

followed by ```
sudo ifup eth0
```

As you've set it for DHCP you will should see it seeking (and hopefully finding) a connection.

A further ```
ifconfig
``` should show an IP address in the (something like) 192.168.x.x range for eth0

---

### Post by sippinondew on 2008-05-04
States:

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The address given is 192.168.1.103

---

### Post by kwacka on 2008-05-04
That you get an IP means that there is a connection.

Is it possible that eth0 is your wireless connection?

Is your router set for DHCP or static IP?

---

### Post by sippinondew on 2008-05-04
No idea.

Browser won't connect to IP address.

---

### Post by kwacka on 2008-05-04
What type of router are you using?

---

### Post by sippinondew on 2008-05-04
RCA DCM425C

Sadly, it's the one the cable company included with the internet package.

---

### Post by Ayuthia on 2008-05-04
Do you have a Broadcom wireless card?  If so and you removed b44, you have removed the module that runs your wired connection.  If what I am saying is correct, the fix that you applied is loading ssb back, but it should be loading b44 instead.  

To test it out, you can do:
```
sudo modprobe -r ssb
sudo modprobe b44
sudo ifconfig eth0 up
```
That should get it back.  You will need to do this until you repair the fix script.

Hope that helps.

---

### Post by sippinondew on 2008-05-04
after entering sudo modprobe -r ssb, terminal states:

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'mkdir'
WARNING: /etc/modprobe.d/blacklist line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'mkdir'
FATAL: Module ssb is in use.


after entering sudo modprobe b44, terminal states:

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'mkdir'
WARNING: /etc/modprobe.d/blacklist line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'mkdir'


sudo ifconfig eth0 up yeilds no response.

---

### Post by kwacka on 2008-05-04
I understand this is a cable modem, do you have a router connected to this?

If there have been any changes (e.g. removal/replacement of router, use or removal of spoof MAC) the IP registered by your cable provider will no longer be recognised and you will not be able to reconnect without contacting them to re-allocate MAC etc.

---

### Post by sippinondew on 2008-05-04
Sorry for the miscommunication.

It is simply a cable modem.  No router.

The connection in question is my bcm44xx card.  I have a direct connection to the modem via ethernet cable.  The wireless card (bcm43xx) is connecting through a neighbor's router.

---

### Post by kwacka on 2008-05-04
> **Ayuthia said:**
> Do you have a Broadcom wireless card?  If so and you removed b44, you have removed the module that runs your wired connection.  If what I am saying is correct, the fix that you applied is loading ssb back, but it should be loading b44 instead.  

To test it out, you can do:
```
sudo modprobe -r ssb
sudo modprobe b44
sudo ifconfig eth0 up
```
That should get it back.  You will need to do this until you repair the fix script.

Hope that helps.

O/P states that wireless connection is working - problem is with **_wired_** connection.

---

### Post by sippinondew on 2008-05-04
Maybe helpful, maybe not, but here are results of sudo lshw -C network:

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b6:b1:62
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:4c:67:99:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11g

---

### Post by kwacka on 2008-05-04
Try the thread at [http://ubuntuforums.org/showthread.php?t=340824&highlight=bcm4400](http://ubuntuforums.org/showthread.php?t=340824&highlight=bcm4400)

suggests that some cards are 'seen' at eth0 but 'recognised' at eth1, or 2, and a link to solution.

---

### Post by sippinondew on 2008-05-04
dmesg | grep eth yields:

[   22.859242] Driver 'sd' needs updating - please use bus_type methods
[   25.270247] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:b6:b1:62
[   47.165150] hda-intel: Invalid position buffer, using LPIB read method instead.
[  144.484503] ADDRCONF(NETDEV_UP): eth0: link is not ready
[124095.643812] b44: eth0: Link is up at 100 Mbps, full duplex.
[124095.643822] b44: eth0: Flow control is off for TX and off for RX.
[124095.646000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[124105.739550] eth0: no IPv6 routers present
[124926.389740] b44: eth0: Link is down.
[125041.051596] ADDRCONF(NETDEV_UP): eth0: link is not ready
[125058.238368] b44: eth0: Link is up at 100 Mbps, full duplex.
[125058.238379] b44: eth0: Flow control is off for TX and off for RX.
[125058.240617] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[125068.443087] eth0: no IPv6 routers present
[125110.773214] ADDRCONF(NETDEV_UP): eth0: link is not ready
[125113.805551] b44: eth0: Link is up at 100 Mbps, full duplex.
[125113.805563] b44: eth0: Flow control is off for TX and off for RX.
[125113.807813] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[125124.412848] eth0: no IPv6 routers present

ifconfig eth0 yields:

eth0      Link encap:Ethernet  HWaddr 00:1d:09:b6:b1:62  
          inet6 addr: fe80::21d:9ff:feb6:b162/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6320249 (6.0 MB)  TX bytes:38771 (37.8 KB)
          Interrupt:21 

but, ifconfig eth1 yeilds:

eth1: error fetching interface information: Device not found

---

### Post by Ayuthia on 2008-05-04
> **kwacka said:**
> O/P states that wireless connection is working - problem is with **_wired_** connection.
The b44 driver is the wired connection.  There are fixes that have been applied to ndiswrapper that turned off the b44 (wired).

---

### Post by Ayuthia on 2008-05-04
Can you post the results to the following:
```
lsmod|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
```

Also, you need to fix /etc/modprobe.d/blacklist.  Lines 41, 42, 45, and 46 need to be removed because sudo and mkdir are commands not recognized in the blacklist file.

Edit: Since we do see the messages from the blacklist, I am guessing that some modifications were made to it.  Can you tell us what was done there?

---

### Post by sippinondew on 2008-05-04
Results of lsmod | grep -i -e b43 -e b44 ssb -e ndiswrapper read:
grep: ssb: No such file or directory

Not sure what changes have been done to blacklist.

---

### Post by Ayuthia on 2008-05-04
> **sippinondew said:**
> Results of lsmod | grep -i -e b43 -e b44 ssb -e ndiswrapper read:
grep: ssb: No such file or directory

Not sure what changes have been done to blacklist.
You forgot the -e before the ssb.

Can you post your /etc/modprobe.d/blacklist?
```
cat /etc/modprobe.d/blacklist
```

---

### Post by sippinondew on 2008-05-04
Sorry.

The results of lsmod | grep -i -e b43 -e b44 -e ssb -e ndiswrapper read:

b43                   115104  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
b44                    28432  0 
mii                     6400  1 b44
ssb                    32260  2 b43,b44

The results of  cat /etc/modprobe.d/blacklist read:

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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx


sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
blacklist bcm43xx

---

### Post by Ayuthia on 2008-05-04
> 
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx


sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
blacklist bcm43xx 
Those lines are not needed in the file.  The last one (blacklist bcm43xx) is repeated and that is why I said it is not needed.  I don't think that it should be hurting anything, but it would be good to remove them so that you don't see the error messages.

You lsmod results do show that b43, b44, and ssb are being used.  Those are the modules that you need.

Let's try to remove the modules once again.  When you do this, you will be disconnecting your wireless and then it will come back.  You will need to reconnect your wireless to the internet after this.  This will only work for this session because once you reboot, the system will do what it did last time.  

```
sudo modprobe -r b43 b44 ssb
sudo modprobe b43 b44
```

You don't need the ssb in the last statement because b43 and b44 need ssb and will load it automatically.

---

### Post by sippinondew on 2008-05-04
How do I remove the undesired lines from the blacklist?

---

### Post by Ayuthia on 2008-05-05
```
gksu gedit /etc/modprobe.d/blacklist
```It should bring up an editor for you with the file opened.  Remove the lines I mentioned and save it.

However, before you do it, make a backup copy of it into your home directory:
```
sudo cp /etc/modprobe.d/blacklist $HOME/blacklist.bkup
```Just in case.... :)

---

### Post by sippinondew on 2008-05-05
The blacklist is corrected.

Still no wired connection available. :(

---

### Post by Ayuthia on 2008-05-05
Ok, can you do the following and post the results?

```
sudo modprobe -r b43 b44 ssb
sudo modprobe b43 b44
sudo ifconfig eth0 up
dmesg | grep eth
```

Hopefully something will show up in the dmesg.

---

### Post by Ayuthia on 2008-05-05
Does your /etc/network/interfaces look like this:
```
auto lo
iface lo inet loopback
```

---

### Post by sippinondew on 2008-05-05
Results read:

robert@Deathstar:~$ sudo modprobe -r b43 b44 ssb
robert@Deathstar:~$ sudo modprobe b43 b44
FATAL: Error inserting b43 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
robert@Deathstar:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
robert@Deathstar:~$ dmesg | grep eth
[   29.924475] Driver 'sd' needs updating - please use bus_type methods
[   32.335373] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:b6:b1:62
[   56.571871] hda-intel: Invalid position buffer, using LPIB read method instead.
[  151.338429] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by sippinondew on 2008-05-05
Interfaces read:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

---

### Post by Ayuthia on 2008-05-05
> **sippinondew said:**
> Results read:

robert@Deathstar:~$ sudo modprobe -r b43 b44 ssb
robert@Deathstar:~$ sudo modprobe b43 b44
FATAL: Error inserting b43 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Can you post the last few lines (maybe 10-20 lines) of dmesg?  We need to see what this error is telling us.  Is your wireless working?

---

### Post by sippinondew on 2008-05-05
[ 3994.009983] PCI: Setting latency timer of device 0000:05:00.0 to 64
[ 3994.069170] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[ 3994.083669] b43: Unknown parameter `b44'
[ 1595.905473] b43-phy0: Broadcom 4311 WLAN found
[ 1595.972960] phy0: Selected rate control algorithm 'simple'
[ 1596.024671] input: b43-phy0 as /devices/virtual/input/input10
[ 1597.702535] Registered led device: b43-phy0:tx
[ 1597.702966] Registered led device: b43-phy0:rx
[ 1597.703314] Registered led device: b43-phy0:radio
[ 1597.770620] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4013.296217] wlan0: Initial auth_alg=0
[ 4013.296232] wlan0: authenticate with AP 00:14:bf:76:33:11
[ 4013.308054] wlan0: RX authentication from 00:14:bf:76:33:11 (alg=0 transaction=2 status=0)
[ 4013.308065] wlan0: authenticated
[ 4013.308071] wlan0: associate with AP 00:14:bf:76:33:11
[ 4013.308105] wlan0: authentication frame received from 00:14:bf:76:33:11, but not in authenticate state - ignored
[ 4013.309528] wlan0: authentication frame received from 00:14:bf:76:33:11, but not in authenticate state - ignored
[ 4013.381135] wlan0: RX AssocResp from 00:14:bf:76:33:11 (capab=0x1 status=0 aid=2)
[ 4013.381148] wlan0: associated
[ 4013.381157] wlan0: CTS protection enabled (BSSID=00:14:bf:76:33:11)
[ 4013.381243] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 4013.381250] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 4013.381256] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 4013.381262] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 4013.383597] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4037.795846] wlan0: no IPv6 routers present

---

### Post by Ayuthia on 2008-05-05
What we need to do next is make sure that we have our modules loaded.  I found out that you can unload multiple modules but you can only load one module at a time.  So just to be safe:
```
sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe b43
sudo modprobe b44
```
This is not going to get us up and running, but it will get our modules loaded.

Now to /etc/network/interfaces.  You are going to have to make a correction to the file.  For now, modify the file to show:
```
auto lo
iface lo inet loopback
```
I think that you are not getting connected because you had the iface and auto lines flip-flopped for eth0.  I don't think those lines are needed because mine seems to run fine without it.  So go modify the file by:
```
gksu gedit /etc/network/interfaces
```
Once that is done, enter this:
```
sudo /etc/init.d/networking restart
```
Check to see if eth0 is up:
```
ifconfig
```
If you don't see eth0 enter:
```
ifconfig eth0 up
```

---

### Post by sippinondew on 2008-05-05
The changes made to interface fixed the problem!

Thanks and sorry for the persistent inconvenience.

---

### Post by Ayuthia on 2008-05-05
It was no inconvenience!  I am glad that we were able to find it!

---

### Post by Feenix3k on 2008-05-23
> **Ayuthia said:**
> Do you have a Broadcom wireless card?  If so and you removed b44, you have removed the module that runs your wired connection.  If what I am saying is correct, the fix that you applied is loading ssb back, but it should be loading b44 instead.  

To test it out, you can do:
```
sudo modprobe -r ssb
sudo modprobe b44
sudo ifconfig eth0 up
```
That should get it back.  You will need to do this until you repair the fix script.

Hope that helps.o add the following code:


I tryed the steps above, I had to add the following code above it:

sudo rmmod b44
sudo rmmod ssb

This gave me access to ssb and b44. When I was done doing your code I saw the driver b44 listed in the connection information, but I still did not have a network connection. For wired I need ssb and b44. But why the card is not getting a signal from the server I am not sure, unless it has something to do with this line, I have no idea what this line is or what it does, I have never seen it befor in ifconfig



eth0:avahi Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
inet addr:169.254.6.161 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:17

---

### Post by seantm on 2008-05-24
Hey everyone -still having trouble getting wireless going in Hardy or other distros? TRY THIS!  --> [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

I've browsed forums for days... And posted... Tried all kinds of command line alchemy just to get a common aeth0 intel network card running on my Lenovo/IBM thinkpad -nothing obscure --no luck Until now! This little utility did the trick -and quick -I 'didn't even have to compile it!

Below is the original post wherein I learned about it --big Kudos to Gais Kay!---

Quote:
Originally Posted by Gias Kay View Post
I am a new user to Ubuntu who have just installed 8.04 (Hardy Heron) two days ago. The installation and setup process were all smooth except for one yet major part - the wireless. Since I am using a notebook (HP Compaq nc6000), without wireless means losing the ability to get online for most of the time which would effectively render the notebook half-dead, so I was anxious to solve the problem.

I went onto several forums and saw various suggestions, ranging from asking me to download some third party driver for the wireless card which needed to be further "built up" from the source code on my end, to some crazy command line instructions I can't really tell what the freak that was though the answerer kept guaranteeing that should work. But these were all too intimidating for a Linux newbie like me and I couldn't really have the determination to try out those expert-looking "problem-neutralizing attempts" (didn't even have the confidence to say "yep that looks like a working solution for me").

Eventually, I stumbled upon my savior (on this exact forum) - Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

According to the explanation I found, the current version of the default network manager in Ubuntu is just incapable when it comes to encrypted wireless connections, and Wicd, coming with a full-fledged GUI, is a better network managing program that can work correctly with the wireless.

I saw the screenshots in the page and the claim seemed to be reliable enough, and there was no horribly long codes and so on, just like how we do things in Windows - install it, set it, problem solved - so I decided to give it a shot.

The installation is quite simple, just follow the instructions inside the "Download" page, then do some more post-setup inside the "FAQ" page; you may or may not have to reboot to make the new problem work, but for me a reboot was necessary. Once you see the Wicd icon on the tray, right click on it and you'll be able to get into the settings. Now just turn on your wireless, wait a few seconds then reload, you can choose from a list of detected networks and the rest is intuitive. Using Wicd, I can even connect to the encrypted WEP network of my home wireless without the password, so I guess it's really the time for me to switch to WPA2.

Unfortunately this handy software seems to be not known by many users who also have problems in trying to get their encrypted wireless connections to work inside the default network manager, so I am writing this from a newbie perspective as an attempt to offer some experience talk for others who are new to Ubuntu as well and have been frustrated over the wireless issue. I also sincerely hope that Wicd can get some deserved attentions from Ubuntu developers and include it into the software repository if not making it the new network managing default
__________________
Ad astra per aspera!
Registered Linux user #471548
Dual Bootn' Ubuntu Hardy 8.4 & Windoze Vista Hm Basic
ThinkPad T61, 15+", core2duo T7100@1,7GH, 2GB RAM/80HD
Last edited by seantm; 3 Days Ago at 01:50 AM.

---


---
title: "Netgear WG511 with WICD in Gusty - no wireless networks found"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by arg on 2008-01-11
hi,

I have gusty and WICD installed and working for wired lan.. wireless worked with network manager but couldnt get WPA working and after reading heaps and heaps came around to WICD... but after installing it all that is displayed is "no wireless networks found" I cant get my netgear WG511 to even light up. I have removed network manager as i installed via the synaptic package manager... 
Can someone please help a noob out. 
Thanks heaps.

---

### Post by wieman01 on 2008-01-11
First off, please post:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
> sudo iwconfig
> route

---

### Post by arg on 2008-01-11
thanks for a quick reply

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results



**lshw -C network**
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:aa:c2:55
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5705-v3.11 ip=10.1.1.53 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=80 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!

**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
default         mik3y.net       0.0.0.0         UG    0      0        0 eth0

---

### Post by wieman01 on 2008-01-11
Your wireless device is probably switched off:
> *-network DISABLED
Is there a hardware switch somewhere?

---

### Post by arg on 2008-01-11
no such luck... it was working with a wep connection untill i installed WICD and still works when plugged into a windows xp machine

---

### Post by wieman01 on 2008-01-11
> **arg said:**
> no such luck... it was working with a wep connection untill i installed WICD and still works when plugged into a windows xp machine
What happens when you unplug the device and plug it in again while Ubuntu is running? Do so only if it is a USB device...

---

### Post by arg on 2008-01-11
not usb its a PC Card 
[http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG511.aspx]("http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG511.aspx")

---

### Post by cameran on 2008-01-11
hello,

i just installed wicd this morning and am having the exact same problem with gutsy.

thanks for any help.

cameran

---

### Post by wieman01 on 2008-01-11
> **arg said:**
> not usb its a PC Card 
[http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG511.aspx]("http://www.netgear.com/Products/Adapters/GWirelessAdapters/WG511.aspx")
Ok, please change the following file:
> sudo gedit /etc/network/interfaces
And make it look like this:
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
Then reboot the PC.

---

### Post by arg on 2008-01-11
gave that a try but still no luck... =(

---

### Post by cameran on 2008-01-12
fixed my problem.  i restored my gnome-network-manager. 

then i downloaded the drivers for my wusb54g v1 adapter, installed them with ndiswrapper, blacklisted entries in this thread:

[http://ubuntuforums.org/showpost.php?p=2533727&postcount=5]("http://ubuntuforums.org/showpost.php?p=2533727&postcount=5")

 then i downloaded wicd again but this time i did not touch my /etc/network/interfaces at all and just left it as is.  it was instantly able to see everything and seems to be working great!

hope this helps someone.

cameran

---

### Post by arg on 2008-01-13
well i managed to get it to find the wireless at last =D thanks to both of you!
however still wont connect... looks like its having trouble getting the ip address or something!! gawd! any ideas?
says connected if i manually enter the ip subnet etc but cant even ping the router!

---

### Post by wieman01 on 2008-01-13
> **arg said:**
> well i managed to get it to find the wireless at last =D thanks to both of you!
however still wont connect... looks like its having trouble getting the ip address or something!! gawd! any ideas?
says connected if i manually enter the ip subnet etc but cant even ping the router!
Network Manager cannot handle static IP addresses, that's all. You either use DHCP or install WICD. No other option.

---

### Post by arg on 2008-01-13
its wicd im using now... 
previous to this i could connect to a wep secured network using network manager but couldnt get onto a WPA network...
so the plane was to install WICD... only couldnt see any wireless networks wep/wpa alike...

either way i have managed to get WICD to see the networks but cant connect to them !! says it is connected but cant even ping 10.1.1.1? pretty much a whole new problem i imagine! 

im guessing network manager cant connect to WPA ?

---

### Post by wieman01 on 2008-01-13
> **arg said:**
> its wicd im using now... 
previous to this i could connect to a wep secured network using network manager but couldnt get onto a WPA network...
so the plane was to install WICD... only couldnt see any wireless networks wep/wpa alike...

either way i have managed to get WICD to see the networks but cant connect to them !! says it is connected but cant even ping 10.1.1.1? pretty much a whole new problem i imagine! 

im guessing network manager cant connect to WPA ?
This has no so much to do with the wireless client that you are using, but the driver for your wireless adapter. If NM does not give you the WPA option, then the card or the driver do not support it. You will have to replace the driver I am afraid...

---

### Post by arg on 2008-01-13
NM gives the option just doesnt work

i have used the card on windows xp with WPA

---

### Post by arg on 2008-01-15
hey
just wanted to say thanks to both of you for your help... how do you do the thanks thing?

i did get it all working including WPA following the instructions i found here:
[http://brainsnorkel.com/tech/getting-wireless-wpa-psk-working-on-a-dell-inspiron-with-netgear-wg511/]("http://brainsnorkel.com/tech/getting-wireless-wpa-psk-working-on-a-dell-inspiron-with-netgear-wg511/")

only changes i needed was i used the win2k drivers rather than XP and i had to select wtext  to finish up ;)

cant recommend the above link more! 

thanks all

---

### Post by wieman01 on 2008-01-15
Great. I would have never guessed that you would need the Win2K driver. Very strange.

You can thank people by pressing the little star icon next to the "Quote" button if that is what you mean. Not saying you should use it, but that's how one would go about thanking other users.

---


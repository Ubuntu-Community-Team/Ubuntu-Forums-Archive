---
title: "Wireless AP broke after upgrade to Feisty 7.04"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by ebike on 2007-05-28
Hi All,

My Prism54 based wifi card refuses to go into "Master" mode after the upgrade. It uded to work fine 
with edgy. Here is the output of iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.417 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Mythtv"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:00verysecret00
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

br0       no wireless extensions.

Here is my /etc/network/interfaces file:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# My network to the house
auto eth0
iface eth0 inet manual
address 0.0.0.0

# My wireless interface
auto wlan0
iface wlan0 inet manual
address 0.0.0.0
wireless-mode master
wireless-channel 2
wireless-essid Mythtv
wireless-key 00verysecret00 restricted

# My internet interface modem
auto eth1
iface eth1 inet dhcp

# My bridge at a fixed IP
auto br0
iface br0 inet static
address 192.168.0.3
netmask 255.255.255.0
broadcast 192.168.0.255
bridge_ports eth0 wlan0 

I seem to get errors when trying to set the mode .. ie.

>  iwconfig wlan0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
root@mythbackend:/var/lib/tmp/media/root# iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


Anyone have any ideas what has changed. I notice that there is a new interface called wmaster0,
what is that?

---

### Post by ebike on 2007-05-28
Bump!

---

### Post by ebike on 2007-05-29
Well you guys are too slow ... fixed it myself.

Seems I needed the latest formware from the prism54.org website and plonked it in the
/usr/lib/hotplug/firmware directory, re-loaded the driver and now everything works ...:p

---

### Post by ebike on 2007-05-30
Ok, spoke too soon. The iwconfig tools allows the mode to be set. But the AP is not seen by other machines.

I have no idea what to do next.

---

### Post by ebike on 2007-05-31
Seems the Prism54 drivers are borken for the latest kernels, I can't wait for them to get there act together, so am purchasing a MadWifi supported card, they have a very good active development cycle ....

---

### Post by stoian on 2007-05-31
does this seem familiar at all?

[http://ubuntuforums.org/showthread.php?t=459665](http://ubuntuforums.org/showthread.php?t=459665)

---


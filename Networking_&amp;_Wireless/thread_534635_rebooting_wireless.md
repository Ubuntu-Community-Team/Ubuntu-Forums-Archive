---
title: "rebooting wireless"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2007-08-25
Hi all,

Forgive me in advance if my terminology is completely wrong. I sometimes seem to lose my wireless connection and my wireless software (wicd) stops being able to see any APs. The way I normally remedy this is by rebooting my computer, and that works fine. What I was wondering, though, is if there is a way to reboot just my "device" (I guess this would be my wireless card or my antenna?) rather than rebooting my entire system. 

Thanks in advance of your replies.

---

### Post by bdoe on 2007-08-25
The following commands will reset your networking:
```
sudo ifdown -v wlan0
sudo ifup -v wlan0
```
replace wlan0 with the device name for the card you need rebooted.

What kind of wireless card are you using?

---

### Post by scholzilla on 2007-08-25
Thanks! I'm using a Realtec RTL8187 chipset, but I don't know if that's the same thing as my wireless card. The results of iwconfig give me wlan0? Is that the name of my card? I don't frankly understand the difference between a card and a chipset.

---

### Post by bdoe on 2007-08-26
Could you copy your iwconfig here?  The Realtec RTL8187 is most likely your wired ethernet controller, and should be configured as eth0.

---

### Post by scholzilla on 2007-08-26
Yeah, and thanks for your follow up. Here's what I get:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"You_No_Use"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:85:67:F2   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality=44/64  Signal level=50/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Incidentally, I've been getting dropped a lot whenever I run torrent programs (bittorrent, deluge). If you see anything here that explains that to you, please let me know.

Thanks!

---

### Post by scholzilla on 2007-08-26
sorry about the last message, I forgot to turn off the smileys.

---

### Post by bdoe on 2007-08-26
heh...  Not quite what I was looking for - my fault. :o

type the following and post the output:
```
sudo lshw -C network
```

---

### Post by scholzilla on 2007-08-26
Thanks again. Here it is:

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:c0200000-c0203fff ioport:a000-a0ff irq:16
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11g

---

### Post by bdoe on 2007-08-26
Okay.  That, and a Google search, told me what I needed to know.  I didn't know Realtek made wifi chips.  I'm intrigued that lshw didn't display any product information for your device, nor any drivers used, or bus information, or anything!  Is this a USB device?

---

### Post by scholzilla on 2007-08-26
no, it's the built in device.

---

### Post by bdoe on 2007-08-26
Weird.

Well, as far as your dropped connections go, I'm not sure if there's a cure for that right now.  I experience net dropouts myself, sometimes severe enough to interrupt my last.fm listening, and I'm using a Broadcom-based card.  The best I can suggest is make sure you've got good wi-fi coverage where you are.

Unfortunately, I know just enough about how Linux handles wireless networking to be dangerous - and that was through a lot of trial and error!  So I'm afraid I'm out of ideas otherwise.

---

### Post by scholzilla on 2007-08-27
oh well, thanks anyway for all your help.

---

### Post by KCPokes on 2007-08-27
I have the same issue as you do, using the same wireless card.  Oddly enough, as you stated, it does seem to be related to what I'm doing at the time, such as high traffic applications.  The other thing I've noticed, which I can't figure out the relation, is that the uptime of my connection seems to be related to which windows manager I use; Compiz drops me real quick, while Beryl works a bit better.  Why or how these are related, or if it is just coincidence, I have no idea.  

This is definitely one of those pesky issues that has been driving me batty for the past couple months.

---

### Post by scholzilla on 2007-08-27
interesting....yes, i've noticed the effect worsens with more traffic. My home wifi almost never drops.

---

### Post by Zorael on 2007-08-27
I experience something similar ([http://ubuntuforums.org/showthread.php?t=533331](http://ubuntuforums.org/showthread.php?t=533331)).

To be able to once more discover networks, I have to reload the driver module thingie for my wlan interface (Intel 3945ABG):

```
zorael@azrael:~$ sudo modprobe -r ipw3945 && sudo modprobe ipw3945
```

(perhaps just one 'sudo modprobe ipw3945' would do the trick, I'm not suicidal enough to kill my connection to try it out)


It doesn't solve the issue, but at least I can get it working again (when I'm there to make the effort).

---

### Post by fragility14 on 2007-08-27
I have the same problem with the onboard wireless on my Asus a8 v-e...

what happens is the connection goes out, then when I try to reconnect it shows the same strength but cant get past trying to configure the IP at 27% or whereever, and will work again without fail after restarting the computer, but the connection cannot be saved by turning Knetwork manager off and then on, by restarting the router, restarting x-server, or by using the command listed earlier.

the ONLY thing that makes it work again is a full restart.

---

### Post by j4play on 2007-08-29
yeah, similar issue here, asus p5k-e onboard wifi (realtek rtl8187).

connection keeps dropping.  using machine remotely, and sometimes can get away with restarting router.  other times i have to physically click reconnect on network manager.   rarely have to reboot (possibly never, but can't remember).

i found stability was improved by installing latest gusty kernel (2.6.22-10), though still drops out.

---

### Post by fragility14 on 2007-08-30
this is still happening to me, and I still need to restart to fix it,,,anyone have a solution?

---

### Post by scholzilla on 2007-09-01
dboe was kind enough to instruct me how to reboot my wireless without having to reboot my whole computer via these commands:

sudo ifdown -v wlan0
sudo ifup -v wlan0

This seemed to work the first couple of times, but now I get the output below when using these commands and have to reboot my system to correct the problem. I'm using wicd and feisty and have already posted chipset and iwconfig info earlier in the thread if you need it. Can anyone diagnose what is going on? Thanks:
[B]
<sudo ifdown -v wlan0>[/B]

Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5346
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
[B][B]
<sudo ifup -v wlan0>[/B][/B]

Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---


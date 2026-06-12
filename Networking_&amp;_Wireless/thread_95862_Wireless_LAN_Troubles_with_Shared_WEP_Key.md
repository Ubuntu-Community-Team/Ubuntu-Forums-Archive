---
title: "Wireless LAN Troubles with Shared WEP Key"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by Sarek on 2005-11-27
I experience troubles connecting to my LAN access point when enabling WEP protection.

I use a D-Link DI-624 as wireless access point and a HP nc6000 with a built-in Atheros wireless card.

The configuration of my access point is:

```
SSID: XXX
Channel: 7
Authentication: Shared Key
WEP: enabled
WEP Encryption: 128 Bit
Key Type: HEX
Key 1: xxxxxxxxxxxxxxxxxxxxxxxxxx
```

The contents (after trying out almost every combination of the *wireless* options) of my /etc/network/interfaces are:

```
auto lo
iface lo inet loopback

mapping hotplug
   script grep
   map eth0

iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.248
gateway xxx.xxx.xxx.xxx
auto eth0

iface ath0 inet dhcp
wireless-essid XXX
wireless-mode Managed
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
wireless-keymode restricted
auto ath0
```

When I switch to *open system* instead of *shared keys* (and chang the interfaces file accordingly) everything works fine.

However, I shall use the shared key configuration because there are other clients in the WLAN.

Thank you very much for posting directions to get my Ubuntu 5.10 to connecting to my WLAN.

---

### Post by Lambert on 2005-11-27
This is how I got a shared key to work using a card with an atheros chipset

Bring down interface

```
sudo ifconfig ath0 down
```

then

```
sudo iwpriv ath0 authmode 2
``` 
This makes a change in the driver to send packets in a sharedkey mode.

My interface looks like this. (only the ath0 part) and it's only 64 bit but I think the above command is what's needed so just enter your key if you choose 128

iface ath0 inet dhcp
wireless-essid xxxxxxx
wireless-key restricted xxxxxxxxxx

auto ath0


Then bring the interface back up

```
sudo ifconfig ath0 up
``` 
You should connect. If you can't surf then run this command

```
route
``` 
You should have lines like this.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 ath0
default         192.168.1.10     0.0.0.0         UG    0      0        0 ath0


When I first did this I didn't have the default line. If you don't either then run this command.

```
sudo route add default gw <router_ip>
``` 
where <router_ip> = the ip address of your router

---

### Post by Sarek on 2005-11-28
The *authmode* did the trick. Thanks a lot!

These settings, however, are gone after a reboot. Is there a way to make them persistent?

---

### Post by Lambert on 2005-11-28
When you say gone is it all commands or just some?

run iwpriv ath0 get_authmode

Is it 2 or or back to 1?

If it is back to 1 then  add this line in your interface file.

pre-up iwpriv authmode 2

If route is a problem in the interface file under the wireless-key add a line like this

post-up route add default gw <...>

---

### Post by Sarek on 2005-11-28
Thank you very much, again!

My interfaces file looks now like this (only wireless section):

```
# The wireless network interface
iface ath0 inet dhcp
pre-up iwpriv ath0 authmode 2
post-up route add default gw 192.168.0.1
wireless-essid XXX
wireless-key restricted xxxxxxxxxxxxxxxxxxxxxxxxxx
auto ath0
```

My sleepless nights have come to an end!

Thanks!

---

### Post by davidrcuervo on 2006-01-06
Hello.....

My job network uses shared key but when i run "iwpriv eth0 authmode 2" it says that "authmode" is an invalid command..... when i typed iwpriv it says that my available commands are set_power, get_power, det_mode, get_mode, set_preamble, get_preamble, reset, sw_reset and monitor, but nothing about authmode.....

I appreciate any help

---

### Post by Lambert on 2006-01-06
iwpriv is driver specific. Above post is in reference to madwifi driver. 

do you know what driver you're using? if not run this command

```
sudo lshw
```

Find your device in the list and in that section look for a line beginning with *configuration:*   that line should show you what driver is bound to the device   (it will say driver=...)

---

### Post by davidrcuervo on 2006-01-06
Thank you....

My driver is ipw2200.... is authmode supported for that driver??? should i use another method?

Thanks in advanced.

---

### Post by Lambert on 2006-01-06
Open up this file

```
sudo gedit /etc/network/interfaces
```

You should see a section with your card in it something like this

iface eth1 inet dhcp
wireless-essid xxxx
wireless-key xxxxx

auto eth1

Yours won't look exactly like this and there may be more lines. But what you need to do is change the wireless-key line so it looks like this

wireless-key restricted xxxxxx

replace xxx with your key. and if you're using a ascii key it should look like this

wireless-key restricted s:xxxxx

---

### Post by davidrcuervo on 2006-01-06
Thank you 


I did it at home, now it is working fine....

I hope I won't have any trouble at the office


Thank you very much.

---


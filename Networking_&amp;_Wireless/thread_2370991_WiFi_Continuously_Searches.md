---
title: "WiFi Continuously Searches"
date: 2017-09-09
forum: Networking &amp; Wireless
---

### Post by PopsTX on 2017-09-09
Howdy!

I need some help with an oddball problem with a fresh install of 16.04 on an HP-8740w laptop (mobile workstation) -concerning its WiFi connection process.

WiFi connects, as it should, BUT the WiFi indicator light continuously flashes --as if it is "searching - polling" possible area WiFi connections.  All the while the connection is persistent with a chosen WiFi network and doesn't drop out. Aggravating and distracting more than anything else --to have blinking light glaring all the while.

In checking the HP support site(s) --it seems there are times the WiFi adapter gets "stuck" (for the lack of better words) in the "search" mode --and lists a "fix" via the Windows Control Panel... All well and good 'cept -This is a totally Linux office.

In short, I need the machine to "stop searching" for WiFi spots after a connection has been established but, of course, remain able to search for connections when the machine is "on the road."

I've included the network hardware info below.

```
lshw -class network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 06
       serial: 88:ae:1d:b4:da:af
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.12-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d7500000-d751ffff memory:d752a000-d752afff ioport:6020(size=32)
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: wlo1
       version: 35
       serial: 00:24:d7:55:34:20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-33-generic firmware=9.221.4.1 build 25532 ip=192.168.1.225 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:46 memory:d3300000-d3301fff
```

---

### Post by chili555 on 2017-09-09
Is this a possible reason it searches? [https://askubuntu.com/questions/848605/ubuntu-16-04-wifi-disconnect/848609#848609](https://askubuntu.com/questions/848605/ubuntu-16-04-wifi-disconnect/848609#848609)

---

### Post by PopsTX on 2017-09-09
...Multiple "same-named" network -No.  Network-Manager does see all the available WiFi networks -and allows me to connect to the one of choice; it just continues to search for more once the network has connected.

I'm thinking there is a configuring file hidden deep in the bowels of Ubuntu that will tell the network adapter to cease and desist after connecting... I just don't know where, or which one to be looking for and what changes might be needed.

---

### Post by chili555 on 2017-09-09
> the WiFi indicator light continuously flashes --as if it is "searching - polling" possible area WiFi connections.What leads you to conclude that it's searching? Many LEDs are set to flash on RF activity.

Let's try a driver parameter:```
sudo modprobe -r iwlwifi
```Your wireless will drop but we'll restart it in the next command:```
sudo modprobe iwlwifi led_mode=3
```If this helps, we'll make it permanent.

---

### Post by PopsTX on 2017-09-09
[CENTER][SIZE=4][COLOR="#FF0000"]PERFECT!!![/COLOR][/SIZE][/CENTER]
I can now connect and disconnect from the keyboard switch --and no blinking light in either position.

HP support indicated the wlan indicator-on some models, would continue to "search" (blink) and offered a solution via Windows Control Panel.

Should I simply add the "led_mode=3" line to the iwiwifi.conig file to make this a permanent fix?

---

### Post by chili555 on 2017-09-09
Let's shoot it in there!```
sudo -i
echo "options iwlwifi led_mode=3"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```You should be all set.

---

### Post by PopsTX on 2017-09-10
[SIZE=5][COLOR="#FF0000"]Problem Solved -Permanently![/COLOR][/SIZE]
Thank you very much!

As I mentioned in the original post... An oddball problem -and were the indicator light not in direct line of sight during use of this laptop -wouldn't have been such a problem.  Makes this particular laptop much more usable.

Thanks again.

---


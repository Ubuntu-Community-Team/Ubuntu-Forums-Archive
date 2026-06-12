---
title: "Wireless card detected...AP's detected...connect icon just spins !"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by deezy on 2007-06-26
Basically I have this card:

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16839121008](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16839121008)

iwconfig lists it as a rt 61 card

It shows up in the admin config, and I can actually see the wireless access points around my home.  When I try to connect to my AP (which is only mac filtered and I've preset the allowed mac's) the trying to connect to network spinning icon does it's thing then eventunally after 1-2 minutes stops and goes back to the computer icon with exclamation point "no network connection"

I've read the issues and posts about this particular chipset, but it seems this card is working out of the box since it identifys the card and picks up the AP's...why do you think I'm unable to connect?!?

Thanks in advance!

-D

---

### Post by kevdog on 2007-06-26
Please post the following:
ifconfig
iwlist scanning
lshw -C network

That should give us a start
Thanks

---

### Post by deezy on 2007-06-26
denver@Gambit:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:98:10:3A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:60 (60.0 b)
          Interrupt:18 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:14:85:D4:6C:F7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:3 dropped:3 overruns:0 carrier:0
          collisions:6 txqueuelen:1000 
          RX bytes:236344 (230.8 KiB)  TX bytes:2284 (2.2 KiB)
          Interrupt:18 

--------------------------------------

denver@Gambit:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:13:10:FA:E6:46
                    ESSID:"azz kikr"
                    Mode:Managed
                    Channel:5
                    Encryption key:off
                    Quality:61/100  Signal level:-64 dBm  Noise level:-256 dBm
          Cell 02 - Address: 00:18:39:45:96:6E
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:8denver@Gambit:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@02:09.0
       logical name: ra0
       version: 00
       serial: 00:14:85:d4:6c:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 multicast=yes wireless=RT61 Wireless
       resources: iomemory:fdef8000-fdefffff irq:18
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:98:10:3adenver@Gambit:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@02:09.0
       logical name: ra0
       version: 00
       serial: 00:14:85:d4:6c:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 multicast=yes wireless=RT61 Wireless
       resources: iomemory:fdef8000-fdefffff irq:18
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:98:10:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:ec80-ecff iomemory:fdef7c00-fdef7c7f irq:18

       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:ec80-ecff iomemory:fdef7c00-fdef7c7f irq:18

                    Encryption key:on
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
          Cell 03 - Address: 00:90:4C:7E:00:6E
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Quality:0/100  Signal level:-88 dBm  Noise level:-256 dBm

------------------------------------

denver@Gambit:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@02:09.0
       logical name: ra0
       version: 00
       serial: 00:14:85:d4:6c:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 multicast=yes wireless=RT61 Wireless
       resources: iomemory:fdef8000-fdefffff irq:18
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:98:10:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:ec80-ecff iomemory:fdef7c00-fdef7c7f irq:18


I checked in my router and it's showing the Gambit ubuntu pc is being assigned a IP via DHCP...so any ideas?

---

### Post by deezy on 2007-06-26
I just went into the lab after posting the above settings to double check my configurations.  I tried connecting again and still getting the same results.  

?

---

### Post by kevdog on 2007-06-27
From the above posts - three wireless networks are seen 
azz kikr (nice name)
linksys
NETGEAR

Which one are you trying to connect to??

Another question:
Your card is installed with the driver: RT61STA
Where did you get this driver, or did you just "plug and play" with linux built in drivers?
If "plug and play" can you list your /etc/modprobe.d/blacklist file?

---

### Post by deezy on 2007-06-27
Yes, azz kikr is my AP so that's the one I'm trying to connect to.

I did not install any driver, just plugged in the card and went with the linux built in drivers.  Below is my blacklist file:

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

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

---

### Post by kevdog on 2007-06-28
Your card is supposed to be supported "out of the box" with Ubuntu, but Ive heard that before!!

Anyway, this is what I want you to try.  

First turn off any encryption on your router. Turn off WEP/WPA and do not MAC filter on the router. We can eventually add all of this stuff back in later.

Ok we are going to test with a manual configuration. If this works then we can automate it, but for now - since we are kind of struggling I want you to do the following. At the command line I want you to type the following:

sudo ifconfig ra0 down
sudo ifconfig ra0 up
sudo iwconfig ra0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig ra0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient ra0

Tell me what happens!!

If you could also list the contents of your /etc/network/interfaces file that would be great (Just cut and paste).

If the above doesnt work then with the next post can you post the following output in addition to the interfaces  file:
modprobe -l | grep rt[[:digit:]]

We might have to install the serialmonkey drivers for your card that are the new, most up-to-date driver versions of the default drivers already installed.

---

### Post by SuperAndy on 2007-07-07
i am also having the same problem, with the same ralink out of the box driver installed.

just to clarify, the line: sudo iwconfig ra0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY

i will have no WEP key, so woudl the line be sudo iwconfig ra0 key "off"

---

### Post by sampbar on 2007-07-07
Just thought i would say i have exactly the same card with exactly the same problem. I followed kevdog's instructions and it works so i am just wondering how i can now automate this?

Thanks 

Samuel

---

### Post by kevdog on 2007-07-07
Ok its  easy to automate however just a few points.

#1. You need to know what interface your wireless card is assigned to.  This could be wlan0, eth0, eth1, ra0, ra1, etc.  This best way to determine this if the following:

```
lshw -C network
```

Look for the line that states [COLOR="Red"]logical name[/COLOR].  That is your interface name

#2. Network manager does not work with ra cards.  So dont even try to use it or it will screw everthing up.

If the above manual commands worked for you (see previous post above), here is how to automate the process

1.  ```
gksu gedit /etc/network/interfaces
```

2. Look for the section containing your interface name (wlan0, eth0, eth1, etc)
```

auto *interface_name*
iface *interface_name* inet dhcp

```

3. Beneath these lines add the following:
```
	
pre-up ifconfig *interface_name* up
pre-up iwconfig *interface_name* essid YOUR_ESSID
pre-up iwconfig *interface_name* key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

```

4. If using WPA make your section appear like this:
```

auto *interface_name*
iface *interface_name* inet dhcp
pre-up ifconfig *interface_name* up
pre-up iwconfig *interface_name* essid "YOUR_ESSID"
pre-up iwconfig *interface_name* mode managed
pre-up iwpriv *interface_name* set AuthMode=WPAPSK
pre-up iwpriv *interface_name* set EncrypType=TKIP
pre-up iwpriv *interface_name* set WPAPSK="YOUR_WPA_PSK_KEY"
pre-up iwpriv *interface_name* set SSID="YOUR_SSID"

```


To restart everthing and enable the changes:
```
sudo /etc/init.d/networking restart
```

If that doesnt work
```
sudo /etc/init.d/dbus restart
```

If that doesnt work, Reboot!

---

### Post by SuperAndy on 2007-07-07
cheers! works brilliantly! just one thing though, is it possible to get a static IP using this method, as opposed to DHCP?

---

### Post by kevdog on 2007-07-07
Try this:

Where it states 
> 
auto *interface_name*
iface *interface_name* inet dhcp


Substitute this:
> 
auto *interface_name*
iface *interface_name* inet static
address *192.168.168.40*
gateway *192.168.168.230*
dns-nameservers *192.168.168.230*
netmask *255.255.255.0*


I dont know if the dns-nameservers is absolutely necessary so you might want to try with and without it.
Also substitute the appropriate values of the entries in italics for whatever works with your setup
Cheers!

---

### Post by SuperAndy on 2007-07-07
well i know what my dns are, so surely i can substitute it for the ones i have

i wont give it a shot now, but it will be a job for tonight probably. thanks again!

---

### Post by SuperAndy on 2007-07-07
ok, i tried that, and no joy. my ra1 device doesn't appear in ifconfig when i make the change. reverting back to the dhcp still works though [this post is proof :P]

---

### Post by kevdog on 2007-07-07
Can you post both versions of you interface file -- the working (dhcp) version and the non-working (static) version?  I cant believe this wouldnt work!

---

### Post by SuperAndy on 2007-07-07
```

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra1
iface ra1 inet dhcp
pre-up ifconfig ra1 up
pre-up iwconfig ra1 essid USR9110
pre-up iwconfig ra1 key "OFF"

```

that one works, assigned by DHCP.

```

  GNU nano 2.0.2                                   File: /etc/network/interfaces                                                                             

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra1
iface ra1 inet static
address 192.168.2.52
gateway 192.168.2.1
dns-nameservers 195.92.195.94
netmask 255.255.255.0
pre-up ifconfig ra1 up
pre-up iwconfig ra1 essid USR9110
pre-up iwconfig ra1 key "OFF"

```

and that one doesn't. i have tried with and without the dns line, as you suggested

---

### Post by kevdog on 2007-07-08
Still confused why its not working.  I found this section off a French Ubuntu wiki.  It provides an example, but since I cant read French I dont know if all the sections are pertinent.  Since I dont own an ra card, I cant try it out myself.  Possibly you could try and let me know.  Thanks

```
auto wlan0
iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
        pre-up ifconfig wlan0 up
#imposta l'essid della rete
        pre-up iwconfig wlan0 essid "NOMERETE"
        pre-up iwconfig wlan0 mode Managed
#imposta il canale della tua rete:
        pre-up iwconfig wlan0 channel 8
        pre-up iwpriv wlan0 set AuthMode=WEPAUTO
        pre-up iwpriv wlan0 set EncrypType=WEP
#qui inserisci la tua chiave wep
        pre-up iwpriv wlan0 set Key1="TUACHIAVEWEP"
        pre-up iwpriv wlan0 set SSID="NOMERETE"
```

---

### Post by SuperAndy on 2007-07-09
SUCCESS!

my devices file now looks like this:

```

  GNU nano 2.0.2                                       File: interfaces                                                                                      

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra1
iface ra1 inet static
address 192.168.2.52
netmask 255.255.255.0
network 192.168.2.1
gateway 192.168.2.1
        pre-up ifconfig ra1 up
        pre-up iwconfig ra1 essid "USR9110"
        pre-up iwconfig ra1 mode Managed

```

brilliant. thankyou very much!

---


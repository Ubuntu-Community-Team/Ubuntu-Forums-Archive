---
title: "cant connect to WEP"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by uberlube on 2008-02-22
I have all my proper wifi drivers set up but i still cant connect to my WEP home network here is my outputs:

 sudo iwlist scan
```

^[[Alo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:E7:0B:EC:E9
                    ESSID:"TRENDnet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:17:9A:27:BA:E4
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

sudo lshw -C network

```

*-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:6e:ca:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

 sudo cat /etc/network/interfaces

```
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


```

---

### Post by Sam Lars on 2008-02-22
So are you using Network Manager to connect?

---

### Post by uberlube on 2008-02-22
I am trying to use Network Manager to connect plus WiCD (as this is the standard in Mint XFCE). I can see all the networks in my area, but when I try to connect to my WEP encrypted home network, it hangs on 'obtaining IP address'. I know my network works as I have been using it for a long time using Mint KDE. Never had a problem connecting in KDE.

---

### Post by kaginken on 2008-02-22
I had similiar problem, I have my router set to 'open'.  You may also opt for 'shared'.

 include 'open' (or shared) before y the key:

iface wlan0 inet static
wireless-essid Foghorn
wireless-key open 95E7D57871D2B383156FYEARIGHT
address 192.168.1.68
netmask 255.255.255.0
gateway 192.168.1.1

If that doesn't do it, try disabling encryption, try to connect.  If that doesn't work, try disabling EVERYthing, i.e. no more MAC address filtering, etc.  Open it wide open, get connected, then try locking it back down one thing at a time.

Hope that helps!!

Rock on  :guitar:

---

### Post by Sam Lars on 2008-02-22
That's a good suggestion.  Get it working at a simple level and then add the complicated stuff.  Helps find problems, too.
Do you have DHCP enabled in the router?  If you run dhclient, does that work?

---

### Post by uberlube on 2008-02-22
Thanks for the response guys ill give it all a try and ill let you know what happens. And yes DHCP is enabled.

---

### Post by uberlube on 2008-02-22
says:

```
bash: iface: command not found
```

---

### Post by kaginken on 2008-02-22
?  iface isn't a command that I'm aware of...#-o

---

### Post by uberlube on 2008-02-22
I was assuming that these were commands to be entered into the terminal, lol:

```


iface wlan0 inet static
wireless-essid Foghorn
wireless-key open 95E7D57871D2B383156FYEARIGHT
address 192.168.1.68
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by uberlube on 2008-02-22
And i tried to change it to "shared". Didn't help.

---

### Post by kaginken on 2008-02-22
Oh, my bad, that's my wireless settings in my interfaces file.

Check yours:

less /etc/init.d/interfaces

See what it looks like, and then add the 'open' in front of your wireless encryption key

---

### Post by kaginken on 2008-02-22
actually, that's

less /etc/network/interfaces  :D

---

### Post by uberlube on 2008-02-23
Mine looks like this, is this Ok?

```
auto wlan0
iface wlan0 inet dhcp
address 68.151.164.22
gateway 68.151.164.1
dns-nameservers 64.59.184.13 64.59.184.15
netmask 255.255.252.0
wpa-driver wext
wpa-ssid TRENDnet
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK


```

---

### Post by kaginken on 2008-02-23
Hmmm...in your first post, you actually listed the contents and they were different, so somethings changed since then.  Your first post, you said it was like:```

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

```

I also re-read your answer to another post that you are trying to use network manager.  If this is the case, your network interfaces need to look like mine, which is nothing but the loopback:
```

auto lo
iface lo inet loopback

```

Try editing your interfaces file to look like that ( you can just comment out all your current stuff to make it easy to revert back), then restart your network:

```
sudo /etc/init.d/network restart
```

Problem is, network manager ignores any interfaces it finds in your interfaces file.

Hope that does the trick!

---

### Post by uberlube on 2008-02-23
adding a # comments out right?

---

### Post by kaginken on 2008-02-23
that's affirmative, over

good luck

---

### Post by uberlube on 2008-02-23
Wouldnt accept command:
sudo /etc/init.d/network restart

says command not found:(

---

### Post by kaginken on 2008-02-23
networking restart

btw, you can use tab completion, i.e.

type /etc/init.d/net <tab> and it will populate into 'networking'

then type restart

/etc/init.d/networking restart

---

### Post by uberlube on 2008-02-23
Thanks for the 'tab' tip, ill use that from now on. OK so it is telling me that it is ignoring eth0 and wlan0 but I go into WiCD and still have the same issue. Cant connect.

---

### Post by kaginken on 2008-02-23
try a reboot this time.  Can't hurt...

---

### Post by uberlube on 2008-02-23
Still nothing:confused:

---


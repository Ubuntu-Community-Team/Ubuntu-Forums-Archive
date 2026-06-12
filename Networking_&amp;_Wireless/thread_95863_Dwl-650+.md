---
title: "Dwl-650+"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by jafenske on 2005-11-27
I'm new to Ubuntu, but not to Linux...

I've been trying to get my dlink DWL-650 working and I've got it working with other distros.  The lights on the card act like they are connected to my router but when I use mozilla I can't connect to host.  

Here is a portion of dmesg

[HTML][4294881.507000] IPv6 over IPv4 tunneling driver
[4294892.171000] eth0: no IPv6 routers present
[4294950.883000] ath_hal: module license 'Proprietary' taints kernel.
[4294950.890000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294950.898000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294950.905000] ath_rate_sample: 1.2
[4294950.917000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294950.922000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[4294950.922000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294951.511000] Build date: Nov 22 2005
[4294951.511000] Debugging version (IEEE80211)
[4294951.511000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294951.511000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294951.511000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294951.511000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294951.511000] ath0: mac 7.9 phy 4.5 radio 5.6
[4294951.511000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294951.512000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294951.512000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294951.512000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294951.512000] ath0: Use hw queue 8 for CAB traffic
[4294951.512000] ath0: Use hw queue 9 for beacons
[4294951.512000] Debugging version (ATH)
[4294951.512000] ath0: Atheros 5212: mem=0x21000000, irq=11
[4294961.418000] ACPI: PCI interrupt for device 0000:07:00.0 disabled
[4294966.927000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[4294966.927000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[4294967.516000] Build date: Nov 22 2005
[4294967.516000] Debugging version (IEEE80211)
[4294967.516000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294967.516000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294967.516000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294967.516000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294967.516000] ath0: mac 7.9 phy 4.5 radio 5.6
[4294967.516000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294967.516000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294967.516000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294967.516000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294967.516000] ath0: Use hw queue 8 for CAB traffic
[4294967.516000] ath0: Use hw queue 9 for beacons
[4294967.516000] Debugging version (ATH)
[4294967.516000] ath0: Atheros 5212: mem=0x20800000, irq=5
[4295019.149000] ath0: no IPv6 routers present
[4295132.032000] ath0: no IPv6 routers present
[4295286.934000] ath0: no IPv6 routers present
[/HTML]

Why would it be looking for IPv6 and how do I change that

Thanks

---

### Post by jafenske on 2005-11-27
I've done some debugging and I have established that the card works and it's not IPv6 tunneling thats screwing me up.  My router is configured for WPA and when I open my axcess point the card works perfect (thats what I'm using now).  I installed wpa_supplicant and followed the instructions and the error Im getting is that 
/etc/wpa_supplicant.conf ia not reading /etc/default/wpasuppicant the files seem to be configured correctly and linked to one another.

Any suggestions.

---

### Post by jafenske on 2005-11-27
Now, I've got a connection with my router.  The link lights on the card flash so I know the WPA is working.  When I try to run Firefox it still won't connect to host.  I tried to ping out and nothing.  Where is the disconnect.  The card seems to be connecting.  

Thanks

---

### Post by Lambert on 2005-11-27
1. Check to see if you have an ip address assigned to the device

```
ifconfig
``` 
The second line under the device should look something like this.

 inet addr:192.168.1.10  Bcast:192.168.255.255  Mask:255.255.0.0

If not then first step is to get an ip assigned.

If yes then step two.

2. Try to ping an external address using the ip

```
ping 216.239.57.99
``` 
If it's not ok then check this command
```
route
``` should look like this

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 ath0
default         192.168.1.10     0.0.0.0         UG    0      0        0 ath0

If you do not have a default line then try this command

```
sudo router add default gw <router ip>
``` where <router ip> = your routers ip address


If ping is ok then ping using common name

```
ping www.google.com
``` 
If it's not ok then check /etc/resolv.conf to see if you have a dns server set up.

---

### Post by jafenske on 2005-11-28
Here is my Ifconfig

```
ath0      Link encap:Ethernet  HWaddr 00:13:46:0D:A2:D1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:511 errors:1593 dropped:0 overruns:0 frame:1593
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:167233 (163.3 KiB)  TX bytes:7656 (7.4 KiB)
          Interrupt:5 Memory:e0ba0000-e0bb0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:248981 (243.1 KiB)  TX bytes:248981 (243.1 KiB)
```

Here is iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dlink"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A6:14:04
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/94  Signal level=-39 dBm  Noise level=-95 dBm
          Rx invalid nwid:136  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5

```

Trying to PING my router yields network not reachable.

My setup works if WPA is off... 

Any suggestions

---

### Post by mindwarp on 2005-11-28
I know this probably isn't what you are looking for, but I had a DWL-650+ card that gave me nothing but problems, bought a prism2 based card on ebay for $40 and never looked back.  Even supported in AMD64.

---

### Post by jafenske on 2005-11-28
This card worked perfect with WPA in Gentoo, the other parts of my system didn't... Anyway last night I was able to connect to the internet with WPA  for about 5 minutes and then it shut off.  I'm going to try setting a static IP.  Maybe I don't have my DNS information set correctly or DHCP is not config'd correctly.

Any thoughts...

---

### Post by Lambert on 2005-11-28
I know little about gentoo but have heard newer versions make it into the tree fairly quick. Do you know what version of the madwifi driver you were using?

The version in ubuntu is a little dated and it's possible there is a problem in the driver its self. If you were connected for 5 minutes then your config should be ok. Maybe there's code in the driver that wasn't complete or completely debugged where wpa is involved.

Edit: couple quick thoughts. Try these commands to see if they help.

sudo iwpriv ath0 authmode 2 (changes to shared key authentication)

if that doesn't work try this

sudo iwpriv ath0 authmode 3 (changes to 802.1x authentication)

---

### Post by jafenske on 2005-11-28
Thanks for the reply... I am using Madwifi driver 0.1_pre20050420-r1.

---

### Post by jafenske on 2005-11-28
Thanks for the suggestions I'll give them a try

---

### Post by jafenske on 2005-11-28
I can connect to my network if i run the command

```
sudo dhclient ath0
```

where do I tell it to use dhcp...

---

### Post by jafenske on 2005-11-29
Will this fix my problem

```
sudo iface atho dhcp
```

How do I tell it on boot to use dhcp.  I have two computer on my network and they both are getting the same IP address.  Is that a function of my router.

---

### Post by Lambert on 2005-11-29
in your /etc/network/interface file there should be a line like this

iface ath0 inet dhcp

This should tell it to use dhcp for that connection.

If you are using dhcp then yes, your ip's are being assigned by the router. Check router settings as to how it assigns ips. Didn't know the same one could be used twice though.

---

### Post by jafenske on 2005-11-29
This lines is in my /etc/network/interfaces

```
iface ath0 inet dhcp
```

Do I need to tell wpasupplicant that I am using dchp

Thanks

---

### Post by ernst on 2006-03-14
My DWL-650+ both DOES work - and DOES NOT work - (?)

Using Breezy on my nine year old Gateway laptop, GRUB displays three kernels I can boot with:

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.10-5-386

It DOES work using the oldest kernel, 2.6.10-5-386
It DOES NOT work using either version  of 2.6.12 (Browser never recognizes a URL)

I accept all updates.

Older is better - why?

Thanks - Ernst

---

### Post by cromestant on 2006-05-07
Just a quick question...
I had the card also working in gentoo, I had to isntall de madwifi driver and tools...
switched to ubuntu , now I want to know how I can install theses on ubuntu
thanks

Charles

---


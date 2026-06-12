---
title: "Wireless USB Adapter shows up as Wired Connection (wlan0)"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by bootz on 2006-11-05
Hey everyone.

I am using ubuntu 6.10 edgy.  I have a Netgear MA111 v1 USB adapter.  It appears to have installed but when I go to networking it shows up as:

Wired Connection (wlan0)

instead of showing wireless.  For some reason it sees it as an Ethernet device?

When I run sudo iwconfig i get:

wlan0 no wireless extensions

I tried to add my ssid to wlan0 anyways and received:

SET failed on device wlan0 ; operation not supported.


I'd be grateful if someone could help me with these issues!

Best regards,

Adam

---

### Post by dbott67 on 2006-11-05
wlan is 'wireless LAN' --- typically, wired ports are eth0, eth1, etc.

Are you using encryption (WEP or WPA)?  If so, try disabling it for the time being.

Also, what is the ESSID of your AP?

Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
There should be a section similar to:
```
auto wlan0
iface wlan0 iface dhcp
wireless-essid **your_essid**
wireless-key s:**your_wep_key** [COLOR="Red"]*(if applicable)*[/COLOR]

```

If so, try this command:
```
sudo ifup wlan0
```

Next, post the output of:
```
sudo iwlist wlan0 scan
```
```
dbott@dapper:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:XX
                    ESSID:"my_essid"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-46 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

-Dave

---

### Post by bootz on 2006-11-05
Thanks for all your help!  My outputs are below.

> 

Are you using encryption (WEP or WPA)?  If so, try disabling it for the time being.

I am not using WEP or WPA.

> 
Also, what is the ESSID of your AP?

Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
There should be a section similar to:
```
auto wlan0
iface wlan0 iface dhcp
wireless-essid **your_essid**
wireless-key s:**your_wep_key** [COLOR="Red"]*(if applicable)*[/COLOR]

```


I'm using the default ESSID.  (Belkin_Pre_N....)
The output is:

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp

> 
If so, try this command:
```
sudo ifup wlan0
```


The output is:

ifup: interface wlan0 already configured

> 
Next, post the output of:
```
sudo iwlist wlan0 scan
```
```
dbott@dapper:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:XX
                    ESSID:"my_essid"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-46 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

-Dave

The output is:

wlan0      No scan results

---

### Post by FrodoB on 2006-11-05
What is the output of iwconfig?

Should be something like:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"MY ESSID"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:22:DF:12:1D:14   
          Bit Rate:11 Mb/s   
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=96/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2012
          Tx excessive retries:1341  Invalid misc:0   Missed beacon:0

---

### Post by bootz on 2006-11-05
> What is the output of iwconfig?

lo no wireless extensions

eth0 no wireless extensions

wlan0 no wireless extensions

sit0 no wireless extensions

---

### Post by FrodoB on 2006-11-06
If you run dmesg can you see where the kernel finds your device? If so publish the section of output that contains it.

---

### Post by yargevad on 2006-11-06
> **bootz said:**
> 
auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
I have ath0 and wlan0 on my laptop also, and ath0 is the wireless card. wlan0 (I think) is an alias for eth0. I haven't done anything with wlan0, I think it showed up when I upgraded to 6.10 but I'm not actually sure of that.

Try doing ```
ifconfig ath0
``` and ```
sudo iwconfig ath0
``` to see if ath0 is being set up instead of wlan0. You should see ath0 getting an IP in the ifconfig section and there should be a MAC address listed for Access Point in the iwconfig listing.

---

### Post by dbott67 on 2006-11-06
Also, what is the output of ifconfig -a:
```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000


```

---

### Post by Jose Catre-Vandis on 2006-11-07
> **bootz said:**
> Hey everyone.

I am using ubuntu 6.10 edgy.  I have a Netgear MA111 v1 USB adapter.  It appears to have installed but when I go to networking it shows up as:

Adam

How did you install? Using ndiswrapper? or are their native drivers "specifically" for this adapter? i had trouble with drivers that "tried" to be the ones I needed, e.g. rtl8187, that I had to blacklist before my ndiswrapper XP driver would work on a full Ubuntu install.

---

### Post by ricegf on 2007-01-14
OK, I just succeeded in establishing a connection to my wireless network using a D-Link DWL-122 (via a USB port) on a fresh Ubuntu Edgy Eft 06.10 i386 installation.  

The DWL-122 was detected by Ubuntu without any effort on my part, but in System->Administration->Wireless it was identified as as "Wired connection (WLAN0)" rather than a wireless connection. Properties offered no place to add the ESSID information (which would make sense if only we had a wire!).

Here's what worked from me.  

First, enable the universe repository.

Second, at a command line type "sudo apt-get install linux-wlan-ng" (without the quotes), and then enter your password.

Third, type "sudo gedit /etc/network/interfaces". Ensure that you have the following lines in this file before saving and closing:
   iface wlan0 inet dhcp
   wireless-essid [your ESSID name]
You may also need to add the following if you have a secured wireless connection (I'm young and foolish):
    wireless-mode managed
    wireless-key [your encryption key]

Fourth and finally, type "sudo ifdown eth0", then "sudo ifup wlan0".

At this point, my DWL-122 lit up like a Christmas tree, and I was on the Internet.  Linux is my friend again.

System->Administration->Wireless still claims "Wired connection (WLAN0)", though.  Let's not disillusion it; things seem to be working well so far.

Hope this helps you.

---

### Post by MarkFlegg on 2007-02-02
> **Jose Catre-Vandis said:**
> How did you install? Using ndiswrapper? or are their native drivers "specifically" for this adapter? i had trouble with drivers that "tried" to be the ones I needed, e.g. rtl8187, that I had to blacklist before my ndiswrapper XP driver would work on a full Ubuntu install.

I'm pretty sure I'm having the same problem. My USB dongle has Prism 3.0 chipset, but Ubuntu has loaded prism2_usb for the driver and it shows up as a wired connection.

How can I blacklist prism2_usb?

(I've already grabbed the EU3USB.sys and EU3NIC.inf files, which I believe are the correct drivers. They load properly with ndiswrapper, and ndiswrapper reports that the driver and hardware are present)

Thanks in advance!!
---------------------------------------------------------------
Actually here I am 25minutes later, with my own solution.

blacklist these drivers by adding lines to  /etc/modprobe.d/blacklist

Worked great, and now I'm posting via my wifi connection!!

---


---
title: "WIFI problems with ubuntu 8.04"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by breakingcustom on 2008-08-09
So I just installed Ubuntu 8.04 on my notebook and as expected I could not connect to wifi. My wireless card detects the WEP network automatically but for some reason it won't accept the passkey for it. I'm 100% sure i'm typing it in correctly and yet it still won't connect. Could it be that I need to update my wireless card driver?


-David

---

### Post by ThaRabbit on 2008-08-09
> **breakingcustom said:**
> So I just installed Ubuntu 8.04 on my notebook and as expected I could not connect to wifi. My wireless card detects the WEP network automatically but for some reason it won't accept the passkey for it. I'm 100% sure i'm typing it in correctly and yet it still won't connect. Could it be that I need to update my wireless card driver?


-David

You're using the network manager to type in the key?

From what I know, NetworkManager seems to have a problem with correctly passing the WEP key configuration to the driver. Please try this, in a terminal:

First, find your wireless interface, for me this looked like:
```
stefan@lapsteef:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"WLAN-AP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:D4:32:36:74   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**wlan1** is my wireless interface, the command used is iwconfig.

First, let's list some acess points: (for me this looked like:
```
stefan@lapsteef:~$ iwlist wlan1 scanning
wlan1     Scan completed :
          Cell 01 - Address: 00:13:D4:32:36:74
                    ESSID:"WLAN-AP"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
This shows me the ESSID (WLAN-AP), the mode (managed) and the Channel (11)

Now, to configure with the info we just found:
```
sudo iwconfig **wlan1** mode managed
sudo iwconfig **wlan1** channel yourwirelesschannel
sudo iwconfig **wlan1** essid yourwirelessnetworkname
sudo iwconfig **wlan1** key yourWEPkey
```

This should configure your wireless interface, now to get an IP:
```
sudo dhclient wlan1
```

If successful, this will look like so:
```
stefan@lapsteef:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:21:00:1e:d6:aa
Sending on   LPF/wlan1/00:21:00:1e:d6:aa
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.11 on wlan1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.11 from 192.168.1.1
bound to 192.168.1.11 -- renewal in 36643 seconds.
stefan@lapsteef:~$ 
```

Now please note: 
connecting via iwconfig and not via network manager means several applications will think you are offline. These applications include Pidgin and Firefox. You will have to use File -> disable tick for "Work Offline" in firefox when you start it.

You can simply reconnect with Pidgin to solve the issue.

A fix for network-manager seems to be in the pipeline, just not complete yet :)

---

### Post by breakingcustom on 2008-08-09
On step two when I typed in "iwlist wlan0 scanning" the output was "wlan 0 no scan results"

---

### Post by ThaRabbit on 2008-08-10
> **breakingcustom said:**
> On step two when I typed in "iwlist wlan0 scanning" the output was "wlan 0 no scan results"

Please post the output of:
```
iwconfig
```

```
dmesg
```

```
lspci
```

You can use [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) Just paste the output there and pass us the link :)

---

### Post by breakingcustom on 2008-08-10
Alright, well I figured it out. Turns out I need to enter the passkey under WEP ASCII and not WEP Passphrase. :KS

---

### Post by ThaRabbit on 2008-08-10
> **breakingcustom said:**
> Alright, well I figured it out. Turns out I need to enter the passkey under WEP ASCII and not WEP Passphrase. :KS

I'm still confused as to why your iwlist wlan0 scanning didn't produce any results. Is your wlan in hidden mode or something?

Anyways, good that you got it working. Apparently I was completely off. lol.

---


---
title: "iwl3945 performance is terrible"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by notnowlewis on 2008-01-21
Hi all,

My toshiba satalite p100-429 has the Intel PRO/Wireless 3945ABG wireless card, which used to be driven by the ipw3945 driver. I upgraded to Hardy and now the iwl3945 driver has taken over, and performance has dropped to 25% of what it was. I used to transfer files around my home network at 2mb/s, now i'm lucky if I get 500k/s. Checking iwconfig shows I'm only connected at 12mb/s bitrate instead of the 56 i had before.

Is there some configuration I could tweak to take its performance back up to the level of the old driver?

Here's my iwconfig output

wlan0_rename  IEEE 802.11g  ESSID:"mikehwifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:90:D0:EA:29:4D
          Bit Rate=12 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=84/100  Signal level=-50 dBm  Noise level=-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I might be barking up the wrong tree blaming the driver though - is there anything else I should check?

Thanks!

---

### Post by thefatmoop on 2008-01-21
intel ipw3945 ya lol i'm using a hybrid driver, but the new iwl w/e driver is supposed to support packet injection/ more control over the radio production

you should download backtrack 2 load the ipw3945 and compare transfer with backtrack 3, which uses the iwl driver

you could always change the driver back to the ipw3945 =/

---

### Post by joneZ on 2008-02-07
Hi,

upgraded to Hardy this yesterday and I'm also having a problem with the
iwl3945 driver. 

The speed/throughput is terrible, the fastest I get is 20 k/s it doesn't matter 
which server or program I use. With ipw3945 I was getting > 500 k/s

ping for example, it's not seldom I get 15% of packet loss. 

I saw some threads and bugs about that, but have no seen fixes yet ... 
 

This bug for example,

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176271](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176271)

though it's with 2.6.22 but I have the same issue with up2date modules from hardy. 

Also the second is the boot speed, if I  blacklist iwl3945 driver boot speed is normal but
with iwl3945 it waites nearly 1 Minute during booting while saying "Loading driver ... "


Here are some details from my card ... 


```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:d3:a0:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.54 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```


```

eth1      IEEE 802.11g  ESSID:"....."  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:59:23:C6   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=49/100  Signal level=-79 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


Any hints or other people how having this problems.

Many Greetings
Erik

---


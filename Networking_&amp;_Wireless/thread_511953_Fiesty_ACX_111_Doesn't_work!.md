---
title: "Fiesty ACX 111 Doesn't work!"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by sieg01 on 2007-07-28
I am trying to get my wireless to work...  I looked over the forums and I haven't got it to work for me yet!

I followed the directions on here
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)
and disabled network manager

and put
options acx firmware_ver=1.2.1.34
in /etc/modprobe.d/options
so I can use the old drivers

It appears to see my  router...
```
wlan0     IEEE 802.11b+/g+  ESSID:"dd-wrt"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:C5:9D:67   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:29  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:519  Invalid misc:0   Missed beacon:0

```

But when i type ```
sudo dhclient wlan0
``` 
It is unable to get a IP address...

Any Help?!

Thanks

---

### Post by ugm6hr on 2007-07-29
Do you use WPA?  If so - you are out of luck.... ACX1xx driver doesn't do WPA.

If not - I don't know.  But ndiswrapper is an option...

---

### Post by sieg01 on 2007-07-29
Not using WPA

I tried going the ndiswrapper route before and it wasn't working.  I may have to try it again.

Shoot this is frustrating. I thought that my wireless worked out of the box on one of the older versions of ubuntu.

Anyone else have any ideas?

---

### Post by sieg01 on 2007-07-29
Here is some more info.  I haven't gone to trying the ndiswrapper yet though.  It looks like it is almost working... i hope!

Output of iwlist scan
```
iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:C5:9D:67
                    ESSID:"dd-wrt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:29  Signal level:0  Noise level:0
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

lshw -C network

```
  *-network:1
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 00
       serial: 00:e0:98:bf:53:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:cfffa000-cfffbfff iomemory:cffa0000-cffbffff irq:11

```

The card is a Xterasys 802.11g Wireless LAN PCI Card
 [http://www.xterasys.com/xn2523g.htm](http://www.xterasys.com/xn2523g.htm)

Any other helpful commands I could check the output of?

Thanks

---

### Post by ugm6hr on 2007-07-29
Does seem like it is working now...  Not sure why the IP is not forthcoming.  What encryption do you use?  Maybe try it with all security turned off, to see whether that connects.

One idea that is worth trying is to completely uninstall Network Manager in Synaptic (network-manager and network-manager-gnome) and install Wicd:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by sieg01 on 2007-07-30
I tried wicd last night.  Nice program but It doesn't get past trying to get the IP address.

One problem seems to be this line from the iwlist scan.
```
Quality:29  Signal level:0  Noise level:0
```
It seems to show 0 signal level all the time.  The wireless router is in the next room so it should work just fine.  Actually the laptop gets a great signal in the same room.

Maybe the card has gone bad?  Or would this still happen if there were driver problems?

---

### Post by PanFx on 2007-09-29
I am using an adapter (Airlink AWLH3025) with the same chipset (Texas Instruments ACX111), and I had a helluva time trying to get it to work.  I first tried the original driver, which installed and worked fine, but could not connect to my Linksys WRT150N router (with WEP security enabled).  Then I tried ndiswrapper -- it doesn't handle WEP or WPA, the driver even says so in the logs.

Here's how I got mine working:

Some posts here on ubuntuforum, and elsewhere, tell you to add the wireless-key in your /etc/network/interfaces file.  I did, but only until I generated a key using the Linksys router (it's a feature on the router that generates a passphrase -- enter a string, it returns a hex key) did it start to work... here's the relevant portion of my interfaces file contents:

.....
auto wlan0
iface wlan0 inet dhcp
wireless-essid BoogerRouter
wireless-key 980FD63088
gateway 192.168.1.1
.....

My Linksys150N router has security mode set to "WEP", Encryption set to "40/64-bit (10 hex digits)", Key 1 set to 980FD63088 and Tx Key set to 1.

NOTE: Mind you, one might not need to generate a key from a passphrase.  Using the same string in the interfaces file as the one in the "Key 1" field of the Linksys wireless security section of the router might work just fine.  I haven't tested it, so generating a key might or might not be necessary.

As soon as I rebooted with the new info, voila!  Instant connection.

Andy
ananonana at gmail dot com

---


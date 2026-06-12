---
title: "[SOLVED] Linksys WMP54G V4.1 -- rt2561/rt61"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by antiemptyv on 2007-12-29
I realize that there are several threads concerning my wireless card--Linksys WMP54G Ver4.1--as I have read through many of them on these forums and others.  I spent most of yesterday going through tutorials trying to get this card working, and nothing has worked for me...yet.  I am confident today will be more fruitful.  It was a bit of a pain getting this card to work under Feisty, but it did eventually work out, and I'm pretty sure I/we can get it working under Gutsy, too, as I have seen many success stories with the help of wieman01 et. al.

Here's my story so far: A few days ago, I upgraded from Feisty to Gutsy, and my wireless connection was actually working right away with just basic adjusting with network-admin.  After some time, however, it began having issues and failed to connect again.  I messed around some more, relying on my arsenal of tactics that worked in Feisty, to no avail.  I did have glints of success such as (i) being able to detect available networks but not being to connect and (ii) nm-applet telling me I was connected but with 0% connection, etc.  I don't know if tinkering made things worse or not, so...

So, today I again resorted to a fresh Gutsy (32bit, though my processor is 64bit) install, so as of right now, all settings are untouched.  

I will now list some more pertinent information that tends to be requested in other threads of this variety:

matt@ubuntu:~$ lspci
```
01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

matt@ubuntu:~$ sudo lshw -C network
```
 *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wmaster0
       version: 00
       serial: 00:18:f8:b1:2e:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
```

matt@ubuntu:~$ modinfo rt61pci
```
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.0.4
author:         http://rt2x00.serialmonkey.com
srcversion:     916A8D32F139220D9CB02DA
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00pci,rt2x00lib,mac80211,eeprom_93cx6
vermagic:       2.6.22-14-generic SMP mod_unload 586 
```

matt@ubuntu:~$ cat /etc/network/interfaces 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

matt@ubuntu:~$ iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```

matt@ubuntu:~$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have gone through wieman01's tutorial ([http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)), though I don't have the CD that comes with the card, but I found one with the help of google claiming to be the one I was in need of.   I also tried other tutorials where I installed serialmonkey drivers--I tried CVS versions of both the rt2500 and rt61 drivers.  I went through other tutorials that are not exactly my setup, such as the person is running Edgy or they are using the USB version of my card.  I guess I am hoping for more specified help.  Interestingly, on Feisty and upon upgrading to Gutsy, my card was ra0, but after a clean CD install, it's called wlan0, and now there's also wmaster0, whatever that is.

So, right now, from scratch, what is my best option?  Any assistance is much appreciated.

---

### Post by wieman01 on 2007-12-30
Hello, 

All I can offer is my outlined solution using "ndiswrapper". I know some people don't prefer it and rather revert to installing Serialmonkey's driver, however, I think "ndiswrapper" is less hassle.

Should I start by guiding you through my tutorial?

Please blacklist these drivers:
> rt2561
rt61

Once you have done all steps, please post:
> sudo ndiswrapper -l
> sudo iwlist scan
You are on a 32-bit system, is that correct?

---

### Post by antiemptyv on 2007-12-30
Great!  Thanks for getting back to me.  When I get home later today, I will go through the tutorial again and post back.

---

### Post by antiemptyv on 2007-12-30
OK.  Firstly, yes I am running the 32-bit Gutsy.  I went through the tutorial.  Everything seemed to go fine.  I blacklisted rt2561 and rt61.  Here are the requested outputs:

matt@ubuntu:~$ sudo ndiswrapper -l
```
rt61 : driver installed
        device (1814:0301) present (alternate driver: rt61pci)
```

matt@ubuntu:~$ sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:66:FC:87
                    ESSID:"phi tau court"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-74 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002b0da576567
          Cell 02 - Address: 9E:44:99:94:CF:5F
                    ESSID:"Free Public WiFi"
                    Mode:Ad-Hoc
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-62 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000226ee4d46
          Cell 03 - Address: 00:14:6C:3F:95:DE
                    ESSID:"FONZARELLI"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-62 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000a386d268f8

```

The first network belongs to the neighbors, and the second one I no clue about--in fact, I have never seen it detected before.  Anyway, the third one, FONZARELLI, is the one I wish to connect to.

---

### Post by wieman01 on 2007-12-31
Good news. Your adapter seems to work. But before we go ahead, please do me a favor and also blacklist this one:
> rt61pci
Then you could open network manager and try to connect to FONZARELLI. It is listed with encryption turned off, so I reckon it is a breeze from here.

---

### Post by antiemptyv on 2007-12-31
Blacklisted rt61pci and rebooted.  Now iwlist scan (without sudo) returns scan results and the networks show up in the networks list in network-admin.  However, I can't seem to get connected to FONZARELLI or the new Free Public Wifi.  I used to connect to FONZARELLI with DHCP and hexadecimal encoding, so that's what I tried, but I tried the other options as well.

---

### Post by antiemptyv on 2007-12-31
OK, it is working now.  In fact, I'm posting this on my Gutsy box right now.  Very exciting considering the annoyance the past couple days.  

Let me summarize what happened since my last post.  iwconfig was not letting me set the essid for some reason, so I ran nm-applet and tried setting romaing and the manual configuration.  Roaming would recognize the networks in the area, but I could not connect to any of them.  In fact, nm-applet would tell me I was connected to two of the available ones (including the desired one), but programs such as firefox, ping, dhclient, etc disagreed with said connection.  Restarting every time i changed an option thinking this may jar something into place (which is obviously the thinking of the many-years-gone Windows user in my head).  The last time I rebooted, it didn't work--saw the network, but couldn't connect.  I sudo'ed a "/etc/init.d/networking restart" and a "dhclient wlan0," which still yielded nothing, so I figured I'd give up for a little while.  I came back about 20 minutes later, sat down, opened firefox, and who rears its head?  ...google.com!

Thanks for your help wieman01.  I really appreciate it.  

I have a couple additional/follow-up questions:  
(i) Is it a common occurrence that just waiting a little while gets it going?
(ii) Is there a setting that keeps Ubuntu from connecting if the Link Quality is below a certain level?  For example, if the signal is only at say 50%, will it still connect?  What about at 45%?  Just curious.

Thanks again!

---

### Post by wieman01 on 2008-01-02
> **antiemptyv said:**
> I have a couple additional/follow-up questions:  
(i) Is it a common occurrence that just waiting a little while gets it going?
(ii) Is there a setting that keeps Ubuntu from connecting if the Link Quality is below a certain level?  For example, if the signal is only at say 50%, will it still connect?  What about at 45%?  Just curious.

Thanks again!
(i) That's a common bug. Please look at post #2 in my WPA tutorial (signature). I have posted a workaround.
(ii) No, there is no rule of thumb. You can be lucky and it connects at 30% or you simply aren't. Really depends on the physical properties of your network, wireless hardware, etc.

If there are other questions, shoot. :-)

---


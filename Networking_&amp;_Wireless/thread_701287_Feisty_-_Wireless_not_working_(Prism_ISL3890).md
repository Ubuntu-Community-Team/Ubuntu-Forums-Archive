---
title: "Feisty - Wireless not working (Prism ISL3890)"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Malefiz on 2008-02-19
Hello!
I'm trying to get wireless working on my laptop, read my way through endless help and information pages... but I still don't understand what's going on! Hopefully someone here can help me sort the connection, before I break my laptop :-)

The Problems are:
* Connection to Network remains at 0% after following the "Connect to Other Wireless Network" prompts
* Network Settings show two options for wireless connections: wlan0 and wmaster0. What is that about??

I have tried: 
(Apologies in advance - I opted to try only the absolutely fool-proof suggestions I came across! Didn't want to mess with any settings, as I obviously haven't got a clue what to do...)
* Trying to connect via Network Settings and wlan0 or/and wmaster0 didn't work.
* Pressing the wireless button on my laptop, thinking that might have some miraculous effect. It didn't.
* Sitting very, very close to the Router Antenna. 

Running some commands I got the following output:
[I]
lshw -C network[/I]

> *-network:1
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 6
       bus info: pci@03:06.0
       logical name: wmaster0
       version: 01
       serial: 00:60:b3:97:18:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=80 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d2004000-d2005fff irq:21


*lspci -v*

> 03:06.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Z-Com, Inc. XG-600 and clones Wireless Adapter
        Flags: bus master, medium devsel, latency 80, IRQ 21
        Memory at d2004000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

[I]
iwconfig[/I]
> 
wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can anyone help me and tell me what to do in order to get wireless working? 
Any help is greatly appreciated!!! :)

Thanks,
Malefiz

---

### Post by jhetrick62 on 2008-02-19
If it was me, I would just build the driver off of the Windows driver using Ndiswrapper and be done with this problem.  I have had hit and miss resutls using the native linux wireless drivers.  I'd say about a 50% success rate.

Follow this tutorial as it's very indepth and make sure to NOT install the svn version although he warns against it.  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Also, make sure to blacklist your current prism driver, don't even chance it otherwise.  He has details on how to blacklist in there also and you have already identified the driver.

Goodluck,
Jeff

---


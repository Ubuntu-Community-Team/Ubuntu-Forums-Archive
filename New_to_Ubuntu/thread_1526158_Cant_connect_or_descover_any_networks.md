---
title: "Cant connect or descover any networks"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by nooffswitch on 2010-07-07
Recently installed ubuntu 10.04 and it says wireless card is active but I cannot find any networks. Help is greatly wanted.

---

### Post by topolab on 2010-07-07
[http://ubuntuforums.org/showthread.php?t=1345577](http://ubuntuforums.org/showthread.php?t=1345577)

---

### Post by nooffswitch on 2010-07-07
Thank you. I tired that with no luck. Even Wifi radar isnt picking up any networks. My phone and other laptops in the house are connected to our internet.

---

### Post by Rubi1200 on 2010-07-07
Go to Applications > Accessories > Terminal and post the output of:

```
iwconfig
```

```
ifconfig
```

```
/etc/network/interfaces
```

---

### Post by nooffswitch on 2010-07-07
ben@ben-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:22:68:93:8e:bb  
          inet6 addr: fe80::222:68ff:fe93:8ebb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1d:72:66:e4:f2  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe66:e4f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:652016 (652.0 KB)  TX bytes:107534 (107.5 KB)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6064 (6.0 KB)  TX bytes:6064 (6.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-22-68-93-8E-BB-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:38902 (38.9 KB)
          Interrupt:23 






ben@ben-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Ben Fixed It"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




ben@ben-laptop:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied

---

### Post by nooffswitch on 2010-07-07
if it helps the contents of /etc/network/interfaces
is..


auto lo
iface lo inet loopback

---

### Post by jerenept on 2010-07-07
Try moving nearer to the Acess Point. Ubuntu sometimes does not get coverage as well as Windows, but not always.

---

### Post by nooffswitch on 2010-07-07
Well at the moment im right next to the router as i have to wire up to it. When i take the cable out, still no wireless connections detected. Im lost :P.

---

### Post by nooffswitch on 2010-07-07
If it matters my wireless card is Atheros Ar5001

lspci -v | less 

07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137b
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath_pci
        Kernel modules: ath_pci, ath5k


aswell as lot of other stuff :P

---

### Post by qwerty2009 on 2010-07-07
try installing the wireless backports from synaptic

or you can copy and paste the following in terminal

sudo apt-get install linux-backports-modules-wireless-lucid-generic

you will need to restart after

---

### Post by nooffswitch on 2010-07-07
Still no joy. Same error as before. Cant find any networks dont even think that its scanning. Although when i restarted i did get a nvidia graphics error saying ubuntu will have to start in low graphics mode, but i think that's been fixed now. Even with the problems during installing im still preferring Ubuntu over windows :P.

---

### Post by nooffswitch on 2010-07-08
After booting up my laptop today, the switch for the wireless says its off but its working and i can connect to my wifi. Thanks guys, rebooted again just to make it was working :P.

---

### Post by nooffswitch on 2010-07-08
Ok now unsolved. Since enabling back ports my wifi has gone back down again, I have no sound and get video display errors when starting up and a few games saying no video device has been found or is unsupported.

---

### Post by Miljet on 2010-07-08
If it helps, here is what mine looks like.
```
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network
 Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0425
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

```

Looks like you are running a different kernel driver.

---

### Post by nooffswitch on 2010-07-08
Ah, do you know how I can change my kernel to ath5k? And get rid off the one I'm using?[PHP][/PHP]

---


---
title: "Wifi Won't Connect"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by theaverageidiot on 2006-10-20
I've had Ubuntu installed on my Dell XPS (gen 1) before. It installed fine and everything, and then when I went to try to set up wifi, it didn't work. It took me days to figure it out - I forget all what I did but I remember "ndis", "wifi radar", stuff like that. I have no idea what I did but after messing around with tons of stuff I got it to work.

I uninstalled Ubuntu for a while and just installed it again, same problem. I don't even know what my wireless card is.

Can someone tell me how to get wifi to work without going through the hassle I had last time? I do seem to remember downloading wireless drivers and running them through some program. Please help! ](*,)

---

### Post by TheWizzard on 2006-10-21
can you please post the output of 
```
iwconfig
and
cat /etc/network/interfaces
```

few tips:
- always backup your /etc folders. this allows you to copy settings from previous installs. 
- always make installation notes. 
- use the command line to install programs and for configuration. now you can use the command "history" to make a log of your installatiuon and configuration. 
```
history > history.txt
```

---

### Post by theaverageidiot on 2006-10-21
Here's that output:

```
josh@josh-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

josh@josh-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid linksys
wireless-key 7*******9 <--- Edited out

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth1
```

I did get ndiswrapper working, though. I went to the Synaptic Package Manager and installed ndiswrapper then used "ndiswrapper -i [path]/bcmwl5.inf" and "ndiswrapper -i [path]/bcmwl5.sys", which appeared to work, but still no wireless.

---

### Post by theaverageidiot on 2006-10-21
bump

---

### Post by TheWizzard on 2006-10-22
try to comment out the 
> auto eth1
at the end of your /etc/network/interfaces file

---

### Post by TheWizzard on 2006-10-22
> wireless-key 7*******9 <--- Edited out

the wep-key is usually much longer.

for the rest, your configuration doesn't look odd. maybe you should check the router configuration.

---

### Post by theaverageidiot on 2006-10-23
I commented out that line and it still doesn't work. ](*,)

---


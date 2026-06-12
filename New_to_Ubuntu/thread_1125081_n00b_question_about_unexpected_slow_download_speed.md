---
title: "n00b question about unexpected slow download speed"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by apollocontrol on 2009-04-14
Hello! Please excuse my noobish-ness, and thanks in advance for any help.

I am running 8.10 and am finding that my download speeds are surprisingly slow, much slower than my windows machine. My Network card, a RaLink RT2500, seems to be listed on the supported cards list as "works out of box", but its so slow that I'm wondering if I missed anything. When I say slow, I mean that it is going at about 1% of the speed of my windows machine. On top of that, it has a lot of trouble connecting to the router, and staying connected.

I have nothing but time, and patience, so any help that can be offered will be well received =P

---

### Post by hyper_ch on 2009-04-14
what's the output of
```

iwconfig

```

---

### Post by coffeeaddict22 on 2009-04-14
Hi,
Sounds odd.  If you're able to open pages, then you've got a
 connection.  Try
```
sudo iwlist rate
```
in a terminal and see what it says/post it back.  In a modernish setup, you should have 54  Mb/s as your current rate.
If the rate is OK, is it dropped packets?  Try ```
ifconfig
``` and post it back.

---

### Post by apollocontrol on 2009-04-14
> **hyper_ch said:**
> what's the output of
```

iwconfig

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Golsch"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:DD:FC:55   
          Bit Rate=1 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=7/100  Signal level:-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by apollocontrol on 2009-04-14
> **coffeeaddict22 said:**
> Hi,
Sounds odd.  If you're able to open pages, then you've got a
 connection.  Try
```
sudo iwlist rate
```
in a terminal and see what it says/post it back.  In a modernish setup, you should have 54  Mb/s as your current rate.
If the rate is OK, is it dropped packets?  Try ```
ifconfig
``` and post it back.

should I be posting my replies in code boxes for the sake of formating? I'll give that a go and can edit the post later if thats the wrong thing to do. this is for the sudo iwlist rate.

```
lo        no bit-rate information.

eth0      no bit-rate information.

wmaster0  no bit-rate information.

wlan0     unknown bit-rate information.
          Current Bit Rate=1 Mb/s

pan0      no bit-rate information.

```

for ifconfig I get:
```

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:4d:f7:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:737 errors:0 dropped:0 overruns:0 frame:0
          TX packets:737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55505 (55.5 KB)  TX bytes:55505 (55.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:82:38:e0  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe82:38e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95030343 (95.0 MB)  TX bytes:6821739 (6.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-82-38-E0-38-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by hyper_ch on 2009-04-14
when asked to post the output of a command or a file then enclose it individually into [noparse]```

```[/noparse] brackets. That makes it easier to read.

---

### Post by hyper_ch on 2009-04-14
Have a look at this here:  [http://ubuntuforums.org/showpost.php?p=7010517&postcount=8](http://ubuntuforums.org/showpost.php?p=7010517&postcount=8)

And it would be also good if you could reply to this bug report: [https://bugs.launchpad.net/ubuntu/+bug/282053](https://bugs.launchpad.net/ubuntu/+bug/282053)

---

### Post by apollocontrol on 2009-04-14
> **hyper_ch said:**
> Have a look at this here:  [http://ubuntuforums.org/showpost.php?p=7010517&postcount=8](http://ubuntuforums.org/showpost.php?p=7010517&postcount=8)

And it would be also good if you could reply to this bug report: [https://bugs.launchpad.net/ubuntu/+bug/282053](https://bugs.launchpad.net/ubuntu/+bug/282053)

that sounds like it would work, but I am still unfamiliar with the terminal. IF anyone would hold my hand a bit more, the directions were:
> 

```

sudo nano /etc/network/if-up.d/rate54M

```

and paste

```

#!/bin/sh

# set the wireless bit rate
iwconfig wlan0 rate 54M

```

In that file.

And then chmodding it
```

sudo chmod 0755 /etc/network/if-up.d/rate54M

```

Wifi is now set at 54M


but after I follow the first instruction, the terminal displays various options at the bottom like ^G Get Help. I hit enter after pasting the contents of the second codebox, but nothing happened so I guess I need to do something else. I dont want to experiment and mess stuff up, so do I just past the third code box's contents and hit enter? or do I need to do something more?

---

### Post by hyper_ch on 2009-04-14
you can exist "nano" by issuing  ctrl-x. You'll then be asked if you want to save it "y" and then what the name should be "enter"

---

### Post by apollocontrol on 2009-04-14
well now it seems that my ubuntu machine is one tenth the speed of my windows machine, which does seem to be an improvement. I have very fast Internet, and my windows is getting a download speed of 6.13 Mbps while Ubuntu is getting 0.68 Mbps

Any clues?

---

### Post by hyper_ch on 2009-04-14
you need to reboot after doing that

---

### Post by apollocontrol on 2009-04-14
> **hyper_ch said:**
> you need to reboot after doing that

restarted once, shut down and then powered back up the second time. Same result.

---

### Post by hyper_ch on 2009-04-14
what does iwconfig say now?

---

### Post by apollocontrol on 2009-04-14
> **hyper_ch said:**
> what does iwconfig say now?

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Golsch"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:DD:FC:55   
          Bit Rate=54 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=25/100  Signal level:-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by hyper_ch on 2009-04-14
do you have a 54mbit card? or slower? or faster?

---

### Post by apollocontrol on 2009-04-14
looked it up and it says its just a 54mbit card, but thats still very slow internets.

---

### Post by hyper_ch on 2009-04-14
No clue, that should work fine.

---

### Post by coffeeaddict22 on 2009-04-14
Hi,
It looks like you've got a 54Mb connection, but the link quality is average.  There's a command line toy for looking at signal quality- a recent and good post on it is here:
[http://www.ubuntugeek.com/howto-check-wireless-link-quality-in-ubuntu-linux.html]("http://www.ubuntugeek.com/howto-check-wireless-link-quality-in-ubuntu-linux.html").

Basically, type in```
route -n
```
to a terminal.  That'll give you a list of places on your local network; mine looks like this:  ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

```

The one you care about at present is the one with a destination of 0.0.0.0; the second column then gives you the Gateway address for your network.

A tool for checking your network is iwspy.  You have to run it as superuser, and you need the network address you're looking at and the port you're going through; in your case(replace the x's with the gateway address):
```
sudo iwspy wlan0 xxx.xxx.x.x
```
wait a few secs, then run 
```
sudo iwspy wlan0
```
which will give you some info on the quality of your wireless network.  
turn off iwspy after that:
```
sudo iwspy wlan0 off
```
If your network is the problem, it's either something mechanical (not in your case if they're fine with Windows), or the signal is being interfered with.  My guess is that there's a competing signal on a close channel, and changing the router frequency should fix it.

---

### Post by apollocontrol on 2009-04-14
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

matt@MattUbuntu:~$ sudo iwspy wlan0 192.168.1.1
Interface doesn't accept addresses...
SIOCSIWSPY: Operation not supported

```

tried it twice, same result, did I enter something wrong?

---

### Post by coffeeaddict22 on 2009-04-14
Dunno.   What do you get from ```
arp
```?
It shows you the table of addresses your PC knows about...
And what does ```
sudo iwlist scan
``` come back with?
Do you have the network manager applet running? 
If you go into System/Administration/Network tools in the menu, what results do you get from pinging?

---

### Post by apollocontrol on 2009-04-27
couldn't tell you why, but with the new version of Ubuntu, my Internet speed is where it should be. Thanks for all the help guys!

---


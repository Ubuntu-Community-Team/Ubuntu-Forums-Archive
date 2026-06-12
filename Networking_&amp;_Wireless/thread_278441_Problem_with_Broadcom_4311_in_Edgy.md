---
title: "Problem with Broadcom 4311 in Edgy"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by dpw2atox on 2006-10-16
I am unable to get my broadcom 4311 network card working on the 64bit version of edgy no matter what I try. The closest I have gotten so far is that it shows up as detected, network manager see's I have a wireless adaptor and can see my mac address, but I can not connect to any wireless access points, even unsecured ones. It scans for about 30sec or so then stops. I am using the version of network manager that comes with edgy. This is an integrated broadcom 4311 adaptor rev 01.

---

### Post by ricks1950 on 2006-10-16
Has your wireless ever worked since the upgrade to Edgy?

I'm using 32 bit.  When I first upgraded to Edgy, wireless was broken, with the symptoms you describe.  Nothing I tried would get it on-line.  Wired would not accept a gateway with fixed IP -- had to use DHCP or manually configure gateway on every boot.

Couple of updates later, all is well, working like it did in Dapper.

---

### Post by dpw2atox on 2006-10-16
my wireless never worked. this is the farthest i have gotten it so far. my wired internet works fine, its only the wireless that has this issue. I blacklisted the old bcm43xx driver, installed the 64bit windows driver, it shows up as hardware detected. network manager see's that there is wireless, i type in an ssid to connect to and it looks like its searching but nothing happens. Does anyone with the 64bit ubuntu running edgy have the broadcom 4311 rev01 working? If so what did you do?

---

### Post by dpw2atox on 2006-10-17
anyone?

---

### Post by Old Pink on 2006-10-17
I'd be interested to know if you get this sorted, at least for the 32bit version as I'll be updating myself soon. :)

---

### Post by dpw2atox on 2006-10-18
So i got it working...i had to use firmware rev 3.x and it works.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

thats the guide i used.

---

### Post by odelay on 2006-10-27
Wouldn't that mean you can no longer use ndiswrapper?  I thought you had to use ndiswrapper for BCM4311 (in my case, Dell 1390) to work?  Either way, I'm hesitant about switching from ndiswrapper to fwcutter...I had everything working so well in Dapper with ndiswrapper.

---

### Post by AlReece45 on 2006-10-28
when I used the bcm43xx drivers I could never get out of G mode, and it was always too slow. (14Kbps)

---

### Post by meyrd on 2006-10-28
I have a broadcom 4306 in a compaq r3000. I just did a fresh install of edgy and can't get my wireless card to work either. I would love it if someone could write a list from start to finish of all packages required to install and the process of making this work. I'm new to ubuntu and would appreciate the help.
Thanks in advance.

---

### Post by Angry penguin on 2006-10-30
@meyrd:
Guide for ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by joergenlie on 2006-10-30
I've got 4311 working like a charm with a compiled ndiswrapper 1.26 and network manager. I never got nm to work with ndiswrapper on dapper.

fwcutter is still locked to rate 11M, so theres no reason to use it.

Jørgen

---

### Post by FrodoB on 2006-11-19
Gentlemen;

This is kind of late, but I just completed the installation of bcm4311 using ndiswrapper on Edgy Eft yesterday. I have attempted to document this, but I may have missed something.  

Could you all take a look and see if this makes sense to you:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Best Regards,

FrodoB

---

### Post by luis.torres.gomez on 2006-11-20
:KS  Yes!!! this guide works for me. [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")
Before I was trying with ndiswrapper from synaptic and don't works.

---

### Post by FrodoB on 2006-11-20
Luis;

Did you find anythings that need to be updated in the documentation?

FrodoB

---

### Post by Jamie Jackson on 2006-11-23
FrodoB,

I followed along with your documentation on a Dell D620 from a fresh installation. The laptop has the same sad wireless device.

Errata:

When you wrote:

[INDENT]Edit the /etc/modprobe.d/ndiswrapper changing eth1 to wlan0:
```
user@ubuntu:~/wusb11/bcm4311$ sudo gedit /etc/modprobe.d/ndiswrapper
```[/INDENT]

I believe you meant:
[INDENT]Edit the /etc/modprobe.d/ndiswrapper changing wlan0 to eth1:
```
user@ubuntu:~/wusb11/bcm4311$ sudo gedit /etc/modprobe.d/ndiswrapper
```

So file becomes:
```
alias eth1 ndiswrapper
```[/INDENT]

I think the above is true, because the stock file reads "wlan0" and the rest of your docs refer to "eth1".

Also, your docs are very detailed, so you might as well mention that you need to enable the right repository (universe, or whatever it is), and do a
```
sudo apt-get install cabextact
``` ...before the cabextract step. I think this is the only step that's really "missing."

Thanks a lot for the docs. (My next post, however, will contain my problems.)

Jamie

---

### Post by FrodoB on 2006-11-23
Well for some strange reason, I did have to do exactly what I said there. 

My ndiswrapper was tied to eth1 and it refused to play with ifup and ifdown until I changed it to wlan0. 

This could have been left over from a previous ndiswrapper install I suppose. 

I will change the wording to clarify that we just want to make sure that our ndiswrapper is wlan0.

Good suggestion on the cabextract. I will figure out which repository it is in and add that.

Thanks for the helpful suggestions, that is what I was hoping for.

Have a good one.

---

### Post by liljoe76 on 2006-11-23
good day,
well mr frodob your walkthrough is as stellar as ever. its the only one thus far that has worked for my 4311. just some quick comments.
a duplicate in the walkthrough;
[COLOR="Red"]user@ubuntu:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf
reprice@xw4200:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf[/COLOR]
and i'm not understanding this;
[COLOR="Red"]Move the 14E4:4311.5.conf file into .conf:
user@ubuntu:~/bcm4311$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf[/COLOR]
i've found no reference to 4324 in any hardware output, not sure why i need to edit that file instead of 4311. though i did. 
my alias was wlan0 as well upon ndiswrapper -m
my wireless came on, which had only happened with fwcutter (but didnt allow a usable connnection, i could assoc but could barely get into router config, much less browse). 
rebooting lost the light, but 
user@ubuntu:~/bcm4311$ sudo depmod -a
user@ubuntu:~/bcm4311$ sudo modprobe ndiswrapper
brought it back up. doing this a few times has made it stick... i think. i've done so many changes in interfaces i dont know if i did it or not. 
so again GREAT how-to. you got my laptop acting like a real laptop. 
on to different issues, maybe.
-wifi radar, it only see's lo connection and i cant use it to connect, a bummer since i dont know the ssid's of folks i'm connecting to.... at the moment i'm using it to see them so i can manually type them into network config. 
-i'm being booted randomly offline, the connection dies, but i still have an ip, etc etc. i try to init restart, nothing, disabling network device, nothing. i need to reboot to get it back. it's quit random, 1 minute or 2 hours... i've simply been browsing. 
-beryl 1.3 kills the connection instantly. again reboot without it on is the only cure. 
i'm certainly not looking for answers, just throwing all this out there.
i'm running an HP dv2120us, edgy, broadcom 4311, nvidia 9742
take care, 
joe

---

### Post by FrodoB on 2006-11-23
Joe thanks for catching the duplicate line.

Was the file 14E4:4324.5.conf not in your installed directory? It was in mine.
user@ubuntu:~/bcm4311$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf

In my case it is the first ndiswrapper installation that is as stable as any kernel driver I have ever seen. Wifi-radar is working for me as well.

---

### Post by Jamie Jackson on 2006-11-23
FrodoB,

I'll go through again with the fresh install image and see if anything else shakes out. I seem to be able to fairly easily get the card to scan and connect, but it seems to take some voodoo to actually be able to hit the Internet.

I'll also see what happens when following your eth1 vs. wlan info now that you've updated it.

If there are any diffs in my experience, I'll let you know, and I'll continue with the former NDISWrapper, as you seem to have used it in your own experiments.

I'm pretty dedicated to getting your howto rock solid, so I can declare victory against this card. It's personal.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2006-11-23
FrodoB,

I confirmed that the stock /etc/modprobe.d/ndiswrapper is
```
alias wlan0 ndiswrapper
```

Then:

```
jamie@mercury:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"jackson"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:E9:7F:84:04   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jamie@mercury:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

jamie@mercury:~$ sudo ifdown eth1
ifdown: interface eth1 not configured

jamie@mercury:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

jamie@mercury:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3620
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:ce:77:39:50
Sending on   LPF/wlan0/00:16:ce:77:39:50
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
jamie@mercury:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:ce:77:39:50
Sending on   LPF/wlan0/00:16:ce:77:39:50
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.188 -- renewal in 34202 seconds.

jamie@mercury:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:7F:84:04
                    ESSID:"jackson"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

jamie@mercury:~$ ping google.com

jamie@mercury:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.115 icmp_seq=1 Destination Host Unreachable
From 192.168.0.115 icmp_seq=2 Destination Host Unreachable
From 192.168.0.115 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3007ms
, pipe 3

```

...So there seems to be some mixup between eth1 and wlan0. I get the wireless light, and I seem to connect and get a DHCP IP, but can't ping the router nor hit the Internet.

Whaddya think?
Jamie

---

### Post by FrodoB on 2006-11-24
It is wlan0 rather than eth1. For some reason when I did mine it assigned eth1. I have corrected the instructions so that they correctly refer to the interface wlan0 only.

Your surely looks like it is working. Check the instructions once more please. My previous eth1 problem probably misled your checkout.

---

### Post by Jamie Jackson on 2006-11-24
Okay, thanks. I'll start fresh again and report back.

---

### Post by Jamie Jackson on 2006-11-24
FrodoB,

Several things so far:

**1**
I thought it was a fluke at first, but following your comments about the sources.list just won't work for me for some reason (some files fail to download on *apt-get update*). I tried two separate fresh install attempts at this, but same problem both times. So now, instead of doing your manual edit/update, I'm going to the synaptic GUI, checking all five repositories, and doing the synaptic update. Then, I continue with your instructions verbatim.

**2**
I don't know if ndiswrapper 1.29 caused this or not:
```
jamie@mercury:~/bcm4311$ ndiswrapper -l
installed drivers:
bcmwl5  invalid driver!
```

...but 1.28 doesn't seem to cause this problem, so I'm using 1.28 instead.

**3**
Suggestion: After copying the .conf file over, you might add
```
sudo gedit /etc/ndiswrapper/bcmwl5/.conf
``` ...since you give the gedit command everywhere else.

**4**
Also, here's my problem right now. The first thing in step 6 doesn't match up with yours, after following your directions exactly.

You'll see mine lists eth1 in contrast to yours, which lists wlan0.
```
jamie@mercury:~/bcm4311$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```

I'm going to stop right here, and wait for your recommendation.

Thanks again,
Jamie

---

### Post by FrodoB on 2006-11-24
This eth1 thing actually happed to me, but someone suggested that it was just me, so I changed everything to refer to wlan0.  

It must be wlan0 on this device for some reason, because mine never worked until I changed it. This is in the instruction now.

Here is the new section, and I will add your other suggestion on gedit:

Make the driver permanent using the ndiswrapper method:  
 user@ubuntu:~/bcm4311$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.
user@ubuntu:~/bcm4311$

Critical Notice: Check the file /etc/modprobe.d/ndiswrapper file and make sure that the ndiswrapper alias is wlan0 an not something else such as eth1. 
 Use cat to look at /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:  
 user@ubuntu:~/bcm4311$ cat /etc/modprobe.d/ndiswrapper

Make sure that it contains only the wlan0 identifier and no other: 
 alias wlan0 ndiswrapper 

If it contains anything else edit /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else: 
 user@ubuntu:~/bcm4311$ sudo gedit /etc/modprobe.d/ndiswrapper

Save the file. 
 Reboot your system in preparation for testing and validation of your work.

The bad thing here is that we now know that sometimes it assigns the device to eth1 and others to wlan0, I know from looking at many dmesg outputs that it only seems to work when we call the device wlan0 for some reason.

---

### Post by Jamie Jackson on 2006-11-24
Sorry, I'm more confused now. When all is said and done, am I supposed to be able to control the device by the name "wlan0"?

If so, that's not working for me. The device is instead known by "eth1".

Did I do something wrong?

Pertinent-seeming information below.

Thanks,
Jamie

```
jamie@mercury:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"jackson"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:E9:7F:84:04   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


``````
jamie@mercury:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
iface wlan0 inet dhcp
wireless-essid jackson
auto wlan0

``````
jamie@mercury:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

```
```
jamie@mercury:~$ dmesg | grep eth1
[17179591.512000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[17179591.536000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179592.052000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179602.676000] eth1: no IPv6 routers present
jamie@mercury:~$ dmesg | grep wlan0
[17179591.508000] wlan0: vendor: ''
[17179591.508000] wlan0: ethernet device 00:16:ce:77:39:50 using NDIS driver bcmwl5, 14E4:4311.5.conf
[17179591.508000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179591.512000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
jamie@mercury:~$ 

```

```
jamie@mercury:~/bcm4311$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:39:96:a5 arp 1
eth1 mac 00:16:ce:77:39:50 arp 1

```

---

### Post by FrodoB on 2006-11-25
Jamie;

Normally I would expect it to be wlan0, if eth1 works fine for you then do not worry about it. 

On my particular laptop it would not work after a reboot until I forced ndiswrapper to call it the default name of wlan0.

I now explain how to change the name in the instructions if it is not working correctly for you.

So does it work as expected or not, that is the question.

FrodoB

---

### Post by Jamie Jackson on 2006-11-25
No, I have no wireless Internet. I seem to associate with the AP, but that's the end of the success.

As far as I can tell, I'm already trying to do what you want me to do to force the device to be called wlan0:

jamie@mercury:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

But I seem to be getting the opposite effect in dmesg:
[17179591.512000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'

Did you see anything wrong with the diagnostics (two posts up from this one)?

Thanks,
Jamie

---

### Post by FrodoB on 2006-11-25
Edit the iftab file and comment out the line that associates your device's MAC identifier with eth1 with a "#" character and it will likely be wlan0 on a reboot.


eth0 mac 00:15:c5:39:96:a5 arp 1
# eth1 mac 00:16:ce:77:39:50 arp 1


It seems that you are associated with your access point so you are close. I could just work on a reboot.

Reboot and let's see what you get.  Also what is the out put of netstat at this point?

netstat -rn

---

### Post by Jamie Jackson on 2006-11-25
> eth0 mac 00:15:c5:39:96:a5 arp 1
# eth1 mac 00:16:ce:77:39:50 arp 1

Yay, this works as you said! Now the device is known as wlan0 after a reboot.

However, same issue with the AP, I connect and get an IP, but no Internet.

Below are some diagnostics.

Thanks!
Jamie

```
jamie@mercury:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"jackson"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:E9:7F:84:04   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jamie@mercury:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
jamie@mercury:~$ sudo iwlist wlan0 scanning
Password:
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:7F:84:04
                    ESSID:"jackson"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

jamie@mercury:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.115 icmp_seq=1 Destination Host Unreachable
From 192.168.0.115 icmp_seq=2 Destination Host Unreachable
From 192.168.0.115 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3007ms
, pipe 3
jamie@mercury:~$ ping google.com
ping: unknown host google.com
jamie@mercury:~$ 


```

---

### Post by FrodoB on 2006-11-25
OK, it is sounding like you are down to router issues. Try pinging [www.google.com](www.google.com) by ip address:

ping -c3 72.14.203.104

If you get your pings, back, then it would seem to be a router or AP setup issue with DNS.

---

### Post by Jamie Jackson on 2006-11-25
You're right, something's goofy with DNS.

What's also weird is the fact that I can ping Google by IP*, but I can't ping my own router.

(*I used a different IP than the one you provided. Yours didn't work for some reason.)

Does this IPv6 dmesg stuff have anything to do with this?
```
[17179815.668000] wlan0: no IPv6 routers present

```

Thanks,
Jamie

```
jamie@mercury:~$ ping -c3 64.233.187.99
PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=243 time=26.9 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=243 time=41.0 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=243 time=64.7 ms

--- 64.233.187.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 26.977/44.273/64.783/15.600 ms
jamie@mercury:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.115 icmp_seq=1 Destination Host Unreachable
From 192.168.0.115 icmp_seq=2 Destination Host Unreachable
From 192.168.0.115 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
, pipe 3
jamie@mercury:~$ ping google.com

jamie@mercury:~$ ping -c3 google.comm

jamie@mercury:~$ ping -c3 google.com
ping: unknown host google.com
jamie@mercury:~$ 


```

---

### Post by FrodoB on 2006-11-25
I always have the same ipv6 message, so I don't think that that is your problem.

You could do a search on the forum for how to remove ipv6, some folks swear by it.

---

### Post by Jamie Jackson on 2006-11-25
Yeah, I don't think it's the problem anymore, either, especially since I've got both IPv4 and IPv6 addresses in iwconfig:

jamie@mercury:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:CE:77:39:50  
          inet addr:192.168.0.188  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe77:3950/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1723666 (1.6 MiB)  TX bytes:370837 (362.1 KiB)
          Interrupt:177 Memory:dfdfc000-dfe00000 

Also, out of curiosity: Do you happen to know how to see what DNS servers I've been assigned by the DHCP server? In windows, an *ipconfig /all* will show me this, but I can't figure out how to see my DHCP DNS servers in Linux.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2006-11-25
Well, I've got wireless. I went to System >> Administration >> Networking, and put in some DNS servers. I then had Internet. What's weird is that if I go back into the DNS tab, those servers I input have disappeared, but it's still working, even after a reboot.

So, I've got working Internet, but I still want to take the voodoo of the above step out of it.

Thanks for all the help.

Jamie

---

### Post by FrodoB on 2006-11-25
Wonderful, I glad to hear that it is working for you.

---

### Post by liljoe76 on 2006-11-26
great thread!
frodo i did have all the files, i was just curius why we were editing that particular file. 
a short update, i'm trying network manager after finding that wifi radar wouldnt let me actively choose a network, it listed 127.0.0.1 as my ip, even after changing the hardware to wlan0 in its config file.... 
i'm still getting network crashes, i'll just lose connectivity. i still have an ip, dns, dhp, all that good stuff i just cant restablish a link. a reboot does it, but thats a pain. i'm thinking its the nvidia since others are having problems with wireless. and like in my last post beryl kills wireless immediately. weird wacky stuff...
thanks again, 
joe

---

### Post by Jamie Jackson on 2006-11-27
FrodoB,

Maybe you don't have an interest in NetworkManager with WPA, but in the off-chance that you've done this, could you share any notes?

I followed this [guide]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") and can use NM with wired, unencrypted wireless, and WEP wireless, but can't connect to WPA APs.

I think I'm almost there, but have no clue how to troubleshoot this.

Thanks,
Jamie

P.S. I started a thread for this [here]("http://ubuntuforums.org/showthread.php?t=307326"), but it's  not very promising.

---

### Post by FrodoB on 2006-11-28
At some point I am going to investigate using WPA. For the moment I live in a neighborhood were there are two to three other access points. WEP is not secure, but then again the internet is not particularly secure either unless you are communicating through secure web pages. 

The biggest issue is will someone steal your bandwith and use it for nefarious purposes, and I only turn my wireless on when I need to use it. This makes me a very unreliable source of free bandwith, so I am not too concerned.

If I lived in tighter quarters like an apartment I would likely have it working already.

---

### Post by Jamie Jackson on 2006-11-28
I'm not so much worried about neighbors borrowing bandwidth as much as someone gaining access to my private network behind the router.

Oh well. If I get it done first, I'll let you know what it took. ;-)

Thanks,
Jamie

---

### Post by Jamie Jackson on 2006-11-30
FrodoB,

Thanks again for all the help. 

Giving back:
I got mine going with WPA, NetworkManager, and NDISWrapper. I (rather heavily) modified [your  wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#preview") to document what I did.

Thanks,
Jamie

---

### Post by FrodoB on 2006-11-30
Very good I will have to try it when I get a chance, Thanks.

---

### Post by jofobuntu on 2006-11-30
> **FrodoB said:**
> [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Oh, thanks to FrodoB, I am So Close I can almost taste it.  And yet, i am still denied.  Everything goes as planned right up until I load the ndiswrapper.  When I do, here is the output from dmesg:

```

[ 2506.402539] ndiswrapper version 1.30 loaded (preempt=no,smp=yes)
[ 2506.424085] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[ 2506.424545] PCI: No IRQ known for interrupt pin A of device 0000:03:00.0. Probably buggy MP table.
[ 2506.424844] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 2506.431533] setup_irq: irq handler mismatch
[ 2506.431557]  <c01497d7> setup_irq+0x127/0x140  <f8d8af10> ndis_isr+0x0/0xc0 [ndiswrapper]
[ 2506.431595]  <c0149889> request_irq+0x99/0xb0  <f8d8989d> NdisMRegisterInterrupt+0x8d/0x110 [ndiswrapper]
[ 2506.431648]  <f8d919c6> IofCallDriver+0x36/0x70 [ndiswrapper]  <f8d98114> miniport_init+0xa4/0x140 [ndiswrapper]
[ 2506.431721]  <f8d982f0> NdisDispatchPnp+0xc0/0x960 [ndiswrapper]  <f8d91cf2> IoAllocateIrp+0x62/0x90 [ndiswrapper]
[ 2506.431778]  <f8d92755> IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]  <f8d8d619> get_current_nt_thread+0xb9/0xe0 [ndiswrapper]
[ 2506.431825]  <f8d928a7> IoQueueThreadIrp+0x17/0xf0 [ndiswrapper]  <f8d919c6> IofCallDriver+0x36/0x70 [ndiswrapper]
[ 2506.431874]  <f8d9422b> IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]  <f8d94573> pnp_start_device+0x53/0xb0 [ndiswrapper]
[ 2506.431936]  <f8d947a3> wrap_pnp_start_device+0x1d3/0x2b0 [ndiswrapper]  <f8d948c5> wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[ 2506.432002]  <c01edc33> pci_match_device+0x13/0xe0  <c01e0f5f> kobject_get+0xf/0x20
[ 2506.432014]  <c01edd76> pci_device_probe+0x56/0x80  <c0245f44> driver_probe_device+0x44/0xc0
[ 2506.432027]  <c011d497> __cond_resched+0x17/0x30  <c02460c2> __driver_attach+0x82/0x90
[ 2506.432040]  <c02458bb> bus_for_each_dev+0x3b/0x60  <c0245e86> driver_attach+0x16/0x20
[ 2506.432052]  <c0246040> __driver_attach+0x0/0x90  <c024552c> bus_add_driver+0x8c/0x140
[ 2506.432063]  <c02462f1> driver_register+0x41/0xa0  <c01edf17> __pci_register_driver+0x47/0x70
[ 2506.432074]  <f8d87778> loader_init+0x138/0x260 [ndiswrapper]  <f89be0c7> wrapper_init+0xc7/0xd2 [ndiswrapper]
[ 2506.432118]  <c013cda8> sys_init_module+0x148/0x19c0  <c0149540> disable_irq+0x0/0x30
[ 2506.432161]  <c0102fbb> sysenter_past_esp+0x54/0x79
[ 2506.432177] ndiswrapper: request for IRQ 0 failed
[ 2506.432325] ndiswrapper (miniport_init:270): couldn't initialize device: C000009A
[ 2506.432332] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[ 2506.437470] unregister_netdevice: device eth%d/f618a000 never was registered
[ 2506.437674] ndiswrapper (miniport_halt:327): device f618a400 is not initialized - not halting
[ 2506.437678] Trying to free free IRQ0
[ 2506.438049] ndiswrapper: device eth%d removed
[ 2506.438198] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[ 2506.441389] usbcore: registered new driver ndiswrapper

```

As you can see, it seems to be complaining about some IRQ thing. As you might guess, the device is never recognized by the kernel.  

For background, I am running this on an HP Pavillion dv9000 with an AMD Turion 64 but I am using the i386 kernel for now.  I've been booting with the following kernel options: "noapic nolapic acpi=off pnpbios=off"  I've sort of settled on those because I was having some freezing issues on boot and those options, found on google, pretty much stopped them.

Any help would be appreciated.  Thanks!

---

### Post by FrodoB on 2006-11-30
You really have a problem that is over my head here. 

Do you perhaps have anyway in your bios to change how the system handles interrupts?

---

### Post by jofobuntu on 2006-11-30
Well, I'm back on track!  Based on some troubleshooting tips on the ndiswrapper FAQ, I took a gander at /proc/interrupts and randomly picked an IRQ that wasn't already in use (56, for example.  BTW, I had no idea there were so many IRQs! I think I remember when you had like 8 or something)  Then I just mannually specified that when loading the ndiswrapper module:

sudo modprobe -o irq=56 ndiswrapper

Now my wireless light blue instead of red and the iwconfig output is similair to what is in your howto.  I still have not gotten connected to an access point yet but I think I'm back to center at least.

Onward! (and thanks again!)

---

### Post by keflavich on 2007-02-01
jofobuntu: I tried that fix, but got a lot of errors spat back at me:

```
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] kmem_cache_create: duplicate cache wrap_mdl
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]  <c0167b68> kmem_cache_create+0x398/0x560  <f8d68b65> add_bus_driver+0xf5/0x140 [irq=56]
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]  <c0106959> do_gettimeofday+0x19/0xc0  <f8d6af00> ntoskernel_init+0x1d0/0x200 [irq=56]
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]  <f8ab509e> wrapper_init+0x9e/0xd2 [irq=56]  <c013cda8> sys_init_module+0x148/0x19c0
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]  <c0157f25> do_wp_page+0x205/0x300  <c0149540> disable_irq+0x0/0x30
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] ndiswrapper (ntoskernel_init:163): couldn't allocate MDL cache
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000004
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]  printing eip:
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] c022b8a8
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] *pde = 00000000
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] Oops: 0002 [#1]
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] SMP 
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] Modules linked in: irq=56 binfmt_misc rfcomm l2cap bluetooth powernow_k8 cpufreq_userspace cpufreq_stat
s freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery 
asus_acpi ac ipv6 ndiswrapper sbp2 parport_pc lp parport af_packet joydev snd_hda_intel snd_hda_codec tsdev snd_pcm_oss snd_mixer_oss snd_pcm snd_timer usbhi
d sg snd agpgart sdhci mmc_core psmouse soundcore snd_page_alloc shpchp pci_hotplug i2c_core serio_raw pcspkr evdev ext3 jbd ohci1394 ieee1394 ohci_hcd ehci_
hcd forcedeth usbcore ide_generic ide_cd cdrom generic sd_mod amd74xx sata_nv libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor ve
safb capability commoncap
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] CPU:    1
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] EIP:    0060:[misc_deregister+72/176]    Tainted: P      VLI
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] EFLAGS: 00210246   (2.6.17-10-generic #2) 
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] EIP is at misc_deregister+0x48/0xb0
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] eax: 00000000   ebx: f8d8d820   ecx: f1988000   edx: 00000000
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] esi: f8d8d82c   edi: 000000ff   ebp: 00000500   esp: f1989e98
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] ds: 007b   es: 007b   ss: 0068
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] Process modprobe (pid: 5378, threadinfo=f1988000 task=f6895560)
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] Stack: f8d8e500 f8d8e500 f7ec7cd0 f8d619ee 45c20645 000868ee f8d8e500 f8d8e500 
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]        f8d75c95 f8ab5055 f8d7e1c0 f8d7b0dd f8d7b0d8 f8d7b0d5 f8d7b0d1 c013cda8 
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000]        f8d8e548 c02f1471 f8d8e50c c0157f25 000284d1 0000009b f8d8e50c f8d8e500 
Feb  1 08:24:53 adam-laptop kernel: [17180343.112000] Call Trace:
Feb  1 08:24:53 adam-laptop kernel: [17180343.116000]  <f8d619ee> loader_exit+0xe/0x90 [irq=56]  <f8d75c95> module_cleanup+0x5/0x40 [irq=56]
Feb  1 08:24:53 adam-laptop kernel: [17180343.116000]  <f8ab5055> wrapper_init+0x55/0xd2 [irq=56]  <c013cda8> sys_init_module+0x148/0x19c0
Feb  1 08:24:53 adam-laptop kernel: [17180343.116000]  <c0157f25> do_wp_page+0x205/0x300  <c0149540> disable_irq+0x0/0x30
Feb  1 08:24:53 adam-laptop kernel: [17180343.116000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
Feb  1 08:24:53 adam-laptop kernel: [17180343.116000] Code: 75 11 8b 1c 24 8b 74 24 04 8b 7c 24 08 83 c4 0c c3 89 f6 e8 db dd 0a 00 f0 ff 0d 54 94 37 c0 0f 8
8 b3 04 00 00 8b 53 0c 8b 46 04 <89> 42 04 89 10 c7 46 04 00 02 20 00 8b 13 c7 43 0c 00 01 10 00 
Feb  1 08:24:53 adam-laptop kernel: [17180343.116000] EIP: [misc_deregister+72/176] misc_deregister+0x48/0xb0 SS:ESP 0068:f1989e98
Feb  1 08:27:49 adam-laptop kernel: [17180343.116000]  <6>ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000] kmem_cache_create: duplicate cache wrap_mdl
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000]  <c0167b68> kmem_cache_create+0x398/0x560  <c011d497> __cond_resched+0x17/0x30
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000]  <f8d9bb65> add_bus_driver+0xf5/0x140 [irq=101]  <c0106959> do_gettimeofday+0x19/0xc0
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000]  <f8d9df00> ntoskernel_init+0x1d0/0x200 [irq=101]  <f8afe09e> wrapper_init+0x9e/0xd2 [irq=101]
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000]  <c013cda8> sys_init_module+0x148/0x19c0  <c0157f25> do_wp_page+0x205/0x300
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000]  <c0149540> disable_irq+0x0/0x30  <c0102fbb> sysenter_past_esp+0x54/0x79
Feb  1 08:27:49 adam-laptop kernel: [17180519.372000] ndiswrapper (ntoskernel_init:163): couldn't allocate MDL cache

```

Any thoughts?  After a google search, I've guessed that it could be a kernel problem, which would make sense considering this problem happened after I got ndiswrapper working, then installed alsa and ran into some kernel crashes, so I suppose the answer is to wait for a kernel update and/or reinstall ndiswrapper, but I was hoping to get some understanding of the problem rather than just start over.

Thanks,
Adam

---


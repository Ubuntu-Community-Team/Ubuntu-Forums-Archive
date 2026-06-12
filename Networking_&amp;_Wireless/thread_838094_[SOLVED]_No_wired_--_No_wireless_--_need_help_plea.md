---
title: "[SOLVED] No wired -- No wireless -- need help please"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by xXOtherPeoplesWasteXx on 2008-06-23
Ok so I'm really new to Ubuntu/Linux.
Like within the last few days.
First install was a breeze. But
--No wireless--
I live on wifi so --No Wired-- either
Ok so I followed several tutorials on 
fw-cutter,
ndiswrapper,
blacklisting,
just about everything.
Some things I am UNABLE to do without a wired connection.
So I decided before posting this to Install Ubuntu again
Clean Install  --Fresh--
So heres what I'm having trouble with:
--Broadcom4318 wireless driver--
This thing is driving me nuts.
I need some help on getting this thing working
right now Im on my other computer
So I'll be able to respond quickly.
Just remember I have no wired connection.
Nor do I have a wireless connection on 
Ubuntu.8.04 Hardy 2.6.24-16
If there is any other info you need 
before we get started on this
Just let me know.

Thank you in advance if anyone does decide to help me.

---

### Post by xXOtherPeoplesWasteXx on 2008-06-23
--[COLOR="Red"]**bump**[/COLOR]--

---

### Post by xXOtherPeoplesWasteXx on 2008-06-24
~clearing throat~
Sorry had to

---

### Post by pokipoki08 on 2008-06-24
Use sypnatic to remove Network Manager (including the gnome counterpart) and wicd.

Try these commands at the terminal & post the output here

```
dmesg | grep ndiswrapper
ndiswrapper -l
```

```
dmesg | grep wlan
cat /var/log/messages | grep wlan
```

```
ifconfig
cat /etc/network/interfaces
```

```
iwlist wlan0 scan
iwconfig wlan0
```

Are you trying to connect to an encrypted wireless network? Is it WEP or WPA?

---

### Post by xXOtherPeoplesWasteXx on 2008-06-24
EDIT

When I rebooted after doing the first on I got some type of error that read (No Operating System) --fixed it though
and here is the new post -which came out different(?)

```
eric@dell:~$ dmesg | grep ndiswrapper
eric@dell:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
eric@dell:~$ dmesg | grep wlan
eric@dell:~$ cat /var/log/messages | grep wlan
eric@dell:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68836 (67.2 KB)  TX bytes:68836 (67.2 KB)

eric@dell:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

eric@dell:~$ iwlist wlan0 scan
wlan0     No scan results

eric@dell:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


And for the time being my wireless network is OPEN &#8211;no passwords or any of that

---

### Post by pokipoki08 on 2008-06-24
Your wifi adapter doesn't seem to be detected by the kernel.

I suggest you follow this thread below to enable the wifi modules

[http://ubuntuforums.org/showthread.php?t=766560&highlight=4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=4318)

Or you can go the ndiswrapper route.

---

### Post by xXOtherPeoplesWasteXx on 2008-06-25
> **pokipoki08 said:**
> Your wifi adapter doesn't seem to be detected by the kernel.

I suggest you follow this thread below to enable the wifi modules

[http://ubuntuforums.org/showthread.php?t=766560&highlight=4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=4318)

Or you can go the ndiswrapper route.


Ok I'll give it a shot.
Thanks for the nod.

If I get it going you will be the first to know

---

### Post by xXOtherPeoplesWasteXx on 2008-06-25
[B]```
[CENTER]I'm online --wireless--
Thank you for the help!!
[/CENTER]
```[/B]

---


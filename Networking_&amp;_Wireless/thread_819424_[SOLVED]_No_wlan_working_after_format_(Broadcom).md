---
title: "[SOLVED] No wlan working after format (Broadcom)"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by ThorRune on 2008-06-05
Hey!

I installed ubuntu for the first time just after 8.04 was out, and it to my amazement made my broadcom wlan card work! It is the first release ever to do so. However, i installed it as a dualboot with win Vista and decided to go for a reformat to get a more logically sized filesystem in a better cooperation with the better-then-Vista XP Pro. But after this latest format, i am having killing problems getting my wlan up-and-running!

When i go into "Hardware Drivers", i can install the driver, and all seems to be going swell, drivers are downloaded and apperantly installed... But then, when it seems to be done and just telling me everything is fine, the whole system crashes. No mouse movement, no response to any keyboard thing. So i'm forced to do a hard reboot.

Now, the hw drivers section says that the wlan driver is enabled, and network manager seems to think it has a wlan. However, Wifi-Radar is unable to find the wlan that i was connected to before the reboot (Or any other wlan for that matter). What is happening here!? All was swell first install, but second and third format it's messing up! :S Any ideas?

---

### Post by Ayuthia on 2008-06-05
Can you post your lshw -C network info?  It will help us see if it is loading the driver.

---

### Post by ThorRune on 2008-06-05
Sure thing :)

---

### Post by Ayuthia on 2008-06-05
It looks like everything is there.  If you go to the Terminal, are you able to see any wireless networks?

```
sudo iwlist scan
```

Can you also post your ifconfig and iwconfig info?

---

### Post by ThorRune on 2008-06-05
As you wish :)

```
thorrune@thorrune-laptop:~$ sudo iwlist scan
[sudo] password for thorrune: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

thorrune@thorrune-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:08:4a:64:e6  
          inet addr:192.168.1.107  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe4a:64e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:412061340 (392.9 MB)  TX bytes:24796514 (23.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70400 (68.7 KB)  TX bytes:70400 (68.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:0d:0e:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-0D-0E-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

thorrune@thorrune-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thorrune@thorrune-laptop:~$ 


```

---

### Post by uberlube on 2008-06-05
You cannot initiate your Broadcom with the restricted driver manager, I just doesnt work. What you need to do is use ndiswrapper to extract the firmware from the windows version of the driver and then install it on your system via the terminal. I have set up a very simple Howto in my sig for this process. It works in 7.10 but I havent tested it in Hardy, so if you could and let me know the results id much appreciate it.

---

### Post by Ayuthia on 2008-06-05
> **uberlube said:**
> You cannot initiate your Broadcom with the restricted driver manager, I just doesnt work. What you need to do is use ndiswrapper to extract the firmware from the windows version of the driver and then install it on your system via the terminal. I have set up a very simple Howto in my sig for this process. It works in 7.10 but I havent tested it in Hardy, so if you could and let me know the results id much appreciate it.

I disagree.  I have a Broadcom 4311 rev 01 and a 4306 rev 03 using the restricted drivers and have no problems with them.  However, I will say that NDISwrapper does sometimes produce different results than the b43 drivers.  Some days I have better luck with NDISwrapper and most other days I use b43.

---

### Post by Ayuthia on 2008-06-05
You can try and see if what happens if we reload the drivers:
[CODE]sudo modprobe -r b43
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
[CODE]

---

### Post by uberlube on 2008-06-05
I have never seen a broadcom wireless device work OOTB with the restricted driver manager, that is something of an oddity. Or did you use the b43xxcutter  or whatever its called.

---

### Post by Ayuthia on 2008-06-05
> **uberlube said:**
> I have never seen a broadcom wireless device work OOTB with the restricted driver manager, that is something of an oddity. Or did you use the b43xxcutter  or whatever its called.
You are correct that the Broadcom card does not work out of the box without the firmware installed.  The restricted driver manager (now called Hardware Drivers in Hardy) installs the b43-fwcutter and will download the firmware for you.  You still need to have a working internet connection for it.

---

### Post by uberlube on 2008-06-05
I still havent tried out hardy yet as I am stricktly LinuxMint so I havent really kept up with the changes theyve made, I suppose the least I could have done is read the release notes, lol. Anyway thats handy that theyve thrown that in there for broadcom users, cuz it does tend to be a pain in the *** to use NDISwrapper after every clean install. Thanks for the tidbit, ill keep it in mind the next time im giving advice for Hardy users.

---

### Post by ThorRune on 2008-06-06
Hmm! Thanks for the help everyone, but i did not get a chance to check the solutions out. I was forced to do yet another, hopefully my last, format. This time, it worked from-the-box, and i am now connected to the wlan and sending you this across it. :) Thanks for all the help. These forums helpfulness never cease to impress me. :D Sorry for the hassle :)

---

### Post by radical3 on 2008-06-06
[http://ubuntuforums.org/showthread.php?t=820588](http://ubuntuforums.org/showthread.php?t=820588)

readpost nine the bit at the end will explain a trick i use to get wlan to work in ubuntu

---


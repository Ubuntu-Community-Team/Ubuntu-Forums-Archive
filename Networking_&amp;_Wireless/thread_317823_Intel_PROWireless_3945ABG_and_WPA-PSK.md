---
title: "Intel PRO/Wireless 3945ABG and WPA-PSK"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by n00b@linux on 2006-12-13
I have an Intel PRO/Wireless 3945ABG PCI network interface card:```
n00b@Ubuntu:~$ lspci | grep '3945'
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```I have the ipw3945 kernel module loaded:```
n00b@Ubuntu:~$ lsmod | grep 'ipw3945'
ipw3945               124576  1 
ieee80211              35272  1 ipw3945
```It is detected correctly as  interface 'eth1':```
n00b@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0D:4B:2A:59  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe4b:2a59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1462761 (1.3 MiB)  TX bytes:15257770 (14.5 MiB)
          Interrupt:225 Base address:0x6800 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:36:3F:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14045 errors:0 dropped:189 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:b3000000-b3000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```I have configured it with iwconfig:```
n00b@Ubuntu:~$ sudo iwconfig eth1 mode managed essid ShagNet channel 10
Password:
n00b@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"ShagNet"  
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:203   Missed beacon:0

sit0      no wireless extensions.
```My problem is that I am trying to get it working with WPA-PSK.
My card is not supported by wpa_supplicant.
I have a very strong network key:```
jX[@r7g5Yw}vlT:F8yJ|o(:v25.d/q^i)ip3*3TdyG_tzfnq+k;}BxSgN2UZ
```which I think may need some special configuration.  
btw, the above is not actually my network key but it is similar in that it's a series of completely random characters.
I did have initial problems configuring PSK with the above key on my Arch Linux install but I have it working now with the above key.

Is there another way of configuring WPA-PSK in Ubuntu?

---

### Post by compwiz18 on 2006-12-13
May I suggest you try some sort of wireless network manager?  Maybe the one in my signature, network-manager, or wifi-radar.  (network-manager and wifi-radar are avaliable in Synaptic - but network-manager will ask for your password on boot - give them all a shot and see what you think)

If you need more help, ask :D

---

### Post by wieman01 on 2006-12-13
You can try this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=202834"). I am pretty sure WPA won't be much of an issue.

---

### Post by n00b@linux on 2006-12-13
> **wieman01 said:**
> You can try this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=202834"). I am pretty sure WPA won't be much of an issue.Thanks wieman01.   I read the thread and had it up and running within 5 mins!  I was so impressed, I've put a link to it on my sig.

The thread needs to be stickied.  Period.

---

### Post by wieman01 on 2006-12-13
You're welcome. Glad it did the job. Not sure what we need to do to have it "stickied" though... And what difference it would make... Any idea?

---

### Post by n00b@linux on 2006-12-14
Getting it stickied would help a lot of newbies to see it (at the top of the foorum) and would answer their question before they paste a thread. 

One of the downsides about Ubuntu is the success of the forums.  I feel they are TOO popular.  It's a harsh reality that many users - and I'm guilty of this myself at times - don't use the search function well enough.  Reading through 20+ threads before you find a solution is not an attractive proposition to someone who has become lazy from an 'it just works' background with Windoze.  I dare say the majority (not all, of course) of those that install Ubuntu are of this type.  Having your thread stickied would serve to alleviate this problem IMHO. 

I think you should approach a moderator about having your thread stickied.  The poll results for it prove its appeal.  It now needs to go mainstream!

---

### Post by wieman01 on 2006-12-14
Thanks for the feedback, mate. I have contacted one of the administrators... So let's see what their response is. If you have suggestions as to how we can improve the thread, you are more than welcome to tell me. Will mention you contribution in the HOWTO of course. :-)

---


---
title: "Absolute Beginner - Wireless not detected"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by Farivan on 2008-04-20
Hi, 

I'm an absolute beginner to Ubuntu. I have no idea about how to use the console, install drivers etc. 

My current problem, like many others, is that I cannot get Ubuntu 8.04 to detect my wireless card. It's a Atheros5007 card used inside my HP Pavillion dv6700. Could someone set me off in the right direction so that I can fix this problem?

I am desperate to stop using Windows Vista.

I'd consider myself quite an advanced windows user. Having said that, being new to Linux, most of the forums are unintelligible to me. The use of abbreviations and technical language in all the forums is very off putting for a beginner. 

I'd be very grateful for help, but please bear in mind that I am new to Linux. I've tried switching before, but always failed to get the wireless working, and the lack of easy-to-follow guidance has always forced me back to Windows. 

Thanks

---

### Post by jnorthr on 2008-04-20
Hi Far - welcome aboard :KS

Time to learn a bit - so look for the main menu icon (looks like an orange ubuntu wheel) > Accessories > Terminal. Click Terminal to open the ubuntu equivalent of a dos prompt.
There is a message log and we can see what's in it using a command called dmesg which will copy all the messages in the log file to your console. Then you can scroll back/forward.

The time stamp down the left is in seconds and counts the elapsed sec.s since the most recent reboot. So we're looking for any messages related to your atheros card.

while you are on the terminal, try these two commands
ifconfig
and
iwconfig
these commands give a snapshot of what ubuntu thinks is connected to your wireless hardware. Your values may be different but you may see something like this:
```
jim@Tiny:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"spooky"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:00:6A:B0:BA:04   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and from there we can continue.  ;)

---

### Post by Farivan on 2008-04-22
Hi Jnorthr, 

Thanks for your help with this - I appreciate it. I hoped to reply sooner, but the forum was down last night. I typed in the commands that you gave to me: 

john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:fa:d1:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9700 (9.4 KB)  TX bytes:9700 (9.4 KB)

john@john-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


I also tried typing "dmesg" but the result did not seem to refer to any wireless hardware (though I could have missed something). I'm guessing the reference to "no wireless extensions" is the main problem here. How do you think I should proceed?

Thanks 

John

---


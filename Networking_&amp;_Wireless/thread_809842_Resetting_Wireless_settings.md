---
title: "Resetting Wireless settings"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by ucal on 2008-05-27
Is there a way to reset the wireless settings so that they are the same as a fresh install (short of reinstalling?  I don't want to have to start over with the programs)?  There was a topic that had specific instructions on installing ndiswrapper for the broadcom 43xx to increase wireless speed, but it didn't work, and I assume that it is because I have done some work on my wireless before hand (to no avail).   

Actually, if you could just go ahead and help me with my wireless set up, that would be great.  At times I get truly vista quality download speeds, as well as web surfing, but at other times, it can take minutes to load a primarilily text page, with downloads reaching the lofty 3 kb/second (I'm used to 70 at least).  The land line is fine, with speeds of 1500ish kb/sec at times.  

I'm sorry that this is probably the thousandth topic related to this, but I need some help here.  Thanks!

---

### Post by ucal on 2008-05-28
Bumping with iwconfig.  

adam@adam-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:44:5B:FC   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=115/100  Signal level=-40 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ucal on 2008-05-28
Bumping with new iwconfig.  Sorry about this, but my download just went straight to hell, so on a suspision, I iwconfigged again.  The results are different.

adam@adam-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:44:5B:FC   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/100  Signal level=-77 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The bitrate just went from 54 to 1 mb/s.  How do I change it so it is permanently 54 mb/s, or is that even possible?

---

### Post by ucal on 2008-05-29
Daily bump.  After finding the command to change the bitrate (sudo iwconfig wlan0 rate XM, x is the desired bitrate), and trying it with several bitrates (5.5 and 54 to be exact), I think the bitrate is just a symptom of the larger problem.

---

### Post by chili555 on 2008-05-29
Please check here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) especially this section: *Ubuntu 8.04 LTS (after installation) [The CORRECT way to disable IPv6]*. See if this helps your speeds.

---

### Post by elamericano on 2008-05-29
Did you notice that your signal quality dropped dramatically? Your wireless card has to send at a lower rate or your data won't be received. You can get closer to the AP, or you can put the AP on a different channel that has less traffic (if it's your AP to configure). You're on channel 11. 6 is usually bad, since many APs default to that. So, try channel 1 if you can.

Other sources of interference are: Microwave ovens and Cordless phones, if they're 2.4Ghz. If it only works bad when someone is heating up their sandwich, then there's your problem :D

11a works in the 5GHz, but you probably don't have 11a.

---

### Post by elamericano on 2008-05-29
...and don't manually set your bitrate. It will just work worse.

---

### Post by ucal on 2008-05-29
chili555:
adam@adam-laptop:~$ip a | grep inet 6
grep: 6: No such file or directory

I assume that means I don't have ipv6 enabled right? I have tried to disable it before.  

elamericano:

I don't think it is an issue of interference, because when running vista, I can get 70~150 kb/sec downloads from this exact spot.  While on Ubuntu, I get about .1~.9kb/sec on most days, 16~70kb/sec on a good day.

Along the lines of signal strength, I have noticed that as I get closer to the router (a meter away from it), the download rates are considerably more normal.  Would I be correct in assuming that this means it is a driver problem?

---

### Post by elamericano on 2008-05-29
This line:

Link Quality=56/100 Signal level=-77 dBm Noise level=-70 dBm

indicated a poor link quality. In fact, it says that you're signal is lower than the noise floor, which is impossible or you wouldn't be connected at all.

It could still be a driver problem. I'd work at getting ndiswrapper working.

---

### Post by chili555 on 2008-05-30
> chili555:
adam@adam-laptop:~$ip a | grep inet 6
grep: 6: No such file or directory
Please correct the command:```
ip a | grep inet6
```It's inet6, not inet 6.

---

### Post by ucal on 2008-05-30
Okay, I corrected the command, and followed the instructions.  I guess I'll see if it works out.  I'll bump this in a day and see what happens.

---

### Post by ucal on 2008-06-03
Bump.  I wasn't able to access the internet for a few days, so I couldn't really evaluate ubuntu's performance.  But it isn't good.  Even with ipv6 turned off, everything is slow as molasses in winter, with a few fast spots sporadically scattered throughout.  

One thing I've noticed is that with Ubuntu, if I'm a meter or two away from the wireless router I'm connecting to, the connection is top notch.  Or at least what I've come to expect with vista.  However, with Vista, I can be all the way across the house and still get that connection.  I hope that helps diagnosis.

---

### Post by chili555 on 2008-06-03
May we please see:```
iwconfig
```Thanks.

---

### Post by ucal on 2008-06-07
adam@adam-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:44:5B:FC   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=68/100  Signal level=-65 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2008-06-07
> Bit Rate=1 Mb/sPlease try:```
sudo iwconfig wlan0 rate auto
```Do things speed up?

---

### Post by ucal on 2008-06-07
Nope.

---

### Post by ucal on 2008-06-08
Any more ideas?

---

### Post by ucal on 2008-06-09
Bump.  The connection has been really weird lately. Last night, and early this morning, I was getting speeds of 837 kb/sec which breaks my vista record.  It didn't last though.  I've seen what this system can potentially do connection wise, I'd love to unlock that potential all the time.

---

### Post by ucal on 2008-06-11
This will be my last bump.  Overall, the connection speed has improved, quite a bit actually, so that it may just be the sites I'm visiting (this forum does seem to be the slowest actually), but it still isn't up to par. I guess I'll just have to hope that the wireless support improves in the next distribution.

---


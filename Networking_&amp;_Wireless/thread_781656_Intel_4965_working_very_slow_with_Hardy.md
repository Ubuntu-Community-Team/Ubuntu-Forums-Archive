---
title: "Intel 4965 working very slow with Hardy"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by exactopposite on 2008-05-04
I just put a new intel 4695 wireless card in my laptop a few days ago to replace a broadcom card. However the speeds i'm getting wiht the new card are very slow. It was a pain getting the boradcom card working (I didn't find the fix for it until after I ordered the intel card) but it was working great. WIth the intel card i have a lag when accessing things over my lan which was not the case at all before with the broadcom card. I use nfs to access all of my media over my lan so it becomes obvious pretty quick if there is a problem with the connection.

What's strange is that all indicators are that I have a great connection with the router. The wireless applet always shows the connection at 95-100% with a speed of 54 meg. Here is the output from iwconfig:

```
wlan2     IEEE 802.11g  ESSID:"xxxxxxxx"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
```


I'm using WPA AES for security. This is a fresh install of hardy 32 bit that was just installed a week ago. The machine is a dell vostro 1400 with a 2ghz  core2duo and 2 gigs of ram. the router is an asus 520gu running ddwrt. I got the 4695 so that I can transition to wireless N in the future, but for now I'm using a G router. I also noticed that the LED ont he laptop that indicates wireless is active does not light up when i'm using this card, but it did with the broadcom card. I'm gonna put the other card back in for now, but hopefully somebody has some ideas on what's going on here

---

### Post by greatgrahambini on 2008-06-10
I'm having the same problem, slow speeds with the intel 4965 in hardy.  Have you figured out the problem?  The problem seems to be between my laptop and the router.  Even though I am showing a strong connection to my router, at 99%, the latency is very high, averaging 44ms with 12% packet loss.  The same laptop in windows XP averages around 2ms with 0% packet loss, so it would seem to be a driver issue.  Let me know if you come accross a solution, thanks.

---

### Post by mariner09 on 2008-06-10
If you don't have a wireless LED, I would recommend installing backports and restricted modules for your kernel.  What's the version of the iwl4965 driver that you're currently using?

I'm currently at 1.2.25 with the 2.6.24-19-generic kernel from the ubuntu proposed repository.  You can activate this repo in synaptic...

---

### Post by Guranic on 2008-06-24
Hi. I had same problem. Hardy and newest kernel driver gave me about 100 kb/s speeds in LAN and from internet too. I found this solution and it worked.

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1623#c9](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1623#c9)

So, just build new driver from linuxwireless.org and load it. It worked for me.

---


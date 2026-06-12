---
title: "No WiFi, IBM Thinkpad, Ubuntu 14 New Install"
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by webmanoffesto on 2015-05-26
I have a new install of Ubuntu on an IBM Thinkpad. I see the WiFi indicator but I'm unable to even turn it on and off on the toolbar. Using 
```
sudo service network-manager restart
```
doesn't work.
I ran the Wireless Info Script I found here [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
and posted the output here [http://pastebin.com/3RPempj6](http://pastebin.com/3RPempj6)

The rfkill below seems significant. 

##### rfkill ############################
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
           BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

  

wlan0     IEEE 802.11bgn  ESSID:off/any             Mode:Managed  Access Point: Not-Associated   Tx-Power=off   

           Retry short limit:7   RTS thr=2347 B   Fragment thr:off

           Power Management:off


Please help me resolve this problem.

---

### Post by chili555 on 2015-05-26
> The rfkill below seems significant.

##### rfkill ############################
1: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]That's likely the only thing that's interfering with your wireless. Have you manipulated the wireless switch or key combination? What model Thinkpad is it? I have two and they both have wireless slide switches like this: [http://designblog.nzeldes.com/wp-content/uploads/2008/05/t61wirelessswitch.jpg](http://designblog.nzeldes.com/wp-content/uploads/2008/05/t61wirelessswitch.jpg)

---

### Post by webmanoffesto on 2015-05-26
Wow, I had no idea that switch was there ([http://www.notebookcheck.net/fileadmin/_migrated/pics/SK-RV-1_02.jpg](http://www.notebookcheck.net/fileadmin/_migrated/pics/SK-RV-1_02.jpg)) , and I don't know how it got switched off. Now I have WiFi on my ThinkPad L412.

Thank You!

And thank you for the Big Bang reference
"Oh Ubuntu, you are my favorite Linux based operating system".
[http://www.youtube.com/watch?v=u6BpSyru4GQ&t=0m8s](http://www.youtube.com/watch?v=u6BpSyru4GQ&t=0m8s)

---

### Post by chili555 on 2015-05-26
Awesome! Glad it's working. Have fun!

---

### Post by webmanoffesto on 2016-01-24
I just fixed the same problem again on another ThinkPad. Same annoying tiny little switch that almost nobody knows is even there.

---

### Post by Vladlenin5000 on 2016-01-25
> **webmanoffesto said:**
> Same annoying tiny little switch that almost nobody knows is even there.

Indeed :p, but that's what user manuals are for.

---


---
title: "Link Quality fluctuates wildly"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by stringkarma on 2008-12-02
Hello,

Ever since I got my new wireless dongle I have seen the network manager signal strength (bars) indicator fluctuate often from full to very low. I have since checked with iwconfig and have seen that this seems to correspond to the Link Quality varying wildly.

Literally seconds apart I get:

```

wlan1     IEEE 802.11bg  ESSID:"--Network Name --"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1F:B3:01:6F:21   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=5/100  Signal level:71/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

then

```

wlan1     IEEE 802.11bg  ESSID:"--Network Name --"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1F:B3:01:6F:21   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:72/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Does anyone know what this number represents or what I can do to stablize it? NB. I seem to have consistent connectivity. Also this didn't happen with my old dongle.

Thanks

Running Intrepid x86_64

Hardware Info:
AMD Turion x2 (64 bit)

lsusb:
Bus 002 Device 003: ID 0ace:1215 ZyDAS WLA-54L WiFi

cat /proc/modules | grep zd:
zd1211rw 59528 0 - Live 0xffffffffa0816000
mac80211 253440 1 zd1211rw, Live 0xffffffffa07d1000
usbcore 175376 4 zd1211rw,ohci_hcd,ehci_hcd, Live 0xffffffffa004d000

---

### Post by baruch60610 on 2008-12-02
I think you may find some useful information in this article:

[http://lists.shmoo.com/pipermail/hostap/2006-December/014831.html](http://lists.shmoo.com/pipermail/hostap/2006-December/014831.html)

From the article it seems that "link quality" is based on many factors other than just signal to noise ratio.  That being the case, you may need to look at issues unrelated to the wireless hardware, for example a problem with a driver, or maybe some conflict somewhere.  HTH.

---

### Post by prshah on 2008-12-02
> **stringkarma said:**
> 
```

          Link Quality=5/100  Signal level:71/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

          Link Quality=100/100  Signal level:72/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


"link quality" is a pure hardware and driver related issue. As long as you're getting a good signal level (you are) and no errors / artifacts (invalid, excessive, etc) you should be facing no problems.

Why does this bother you? Is it jus the aesthetics, or are you losing out connectivity, or do you feel that it is indicative of some deeper problem?

If it is the first, I would suggest you live with it. If it is any of the latter, then I would suggest taking a look at the driver. Is it a native driver or is it ndiswrapper'd INF? In the latter case, try changing to a Windows NT/2000 inf driver instead of XP, or vice-versa.

If it is a native driver, perhaps you should wait for, or contribute to, a future / beta version.

---

### Post by stringkarma on 2008-12-02
Basically just aesthetics. However this problem means that the icon for signal strength jumps so badly that I cannot use it to assess the quality of my connection. I have to go to the command line. 

I also am always on the lookout for usablility of Ubuntu and Linux. This would be the sort of problem that would get users knocking on my door asking why their connection was bad, even though it isn't.

To answer about the driver, I am using the native kernel module driver as listed in my first post /proc/modules

---

### Post by miatawnt2b on 2009-01-26
I have the same problem with my 8.04 install.  I am using an Intel IPW2200 driver on a 2915ABG card.  Do you know what brand AP you guys have?

-J

---


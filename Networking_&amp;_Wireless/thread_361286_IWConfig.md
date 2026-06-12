---
title: "IWConfig"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by brandoncolorado on 2007-02-14
Hey, I have been having wireless problems (low signal etc.) in Ubuntu.

Does this IWConfig printout tell me anything?

wlan0     802.11b/g linked  ESSID:"linksys"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:39:40:AC:EC   
          Bit Rate=54 Mb/s   
          Retry: on   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


I know that a lot of the problem is that my card is not fully supported (RTL8185), so I think that accounts for the link quality, and signal level being 0, but should power management be off, and what is fragment thr?

---

### Post by corax on 2007-02-14
Hi !

Sorry I can't understand you :( Is it working or not ? Yes the link quality should be more than 30 for an "acceptable" connection :)  the signal and noise levels should be negative dB values the link quality is calculated from these two values ...

The power management is off on my card but it is working though ... I guess (!) it is about power saving for example in notebooks and other mobile devices ... just a guess

About fragment thr I have no idea but google maybe helps :)

or type

```
man iwconfig
``` and read :)

---

### Post by brandoncolorado on 2007-02-14
Hi,

Maybe some screenshots will better explain my situation.

I have attached these screenshots:

1) One screenshot to show my network manager icon.  This icon ALWAYS says signal strength is 30% NO MATTER WHAT.

2) One screenshot showing IWConfig printout

3) One screenshot showing device manager with my wireless highlighted

4) One screenshot showing connection information from network manager

notes:  I am online and Ndiswrapper is empty but installed.

---

### Post by corax on 2007-02-16
Hi !

If you do some research you can find some useful information ... for example here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
or here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I have never used ndiswrapper but i think if you check these lists and you find out that your card is supported then it will probably work... just hack it :)

bye & good luck

---

### Post by brandoncolorado on 2007-02-19
Hi, I've tried with Ndiswrapper, and either I can't find the right driver, or the driver doesn't load (nothing shows up).

---


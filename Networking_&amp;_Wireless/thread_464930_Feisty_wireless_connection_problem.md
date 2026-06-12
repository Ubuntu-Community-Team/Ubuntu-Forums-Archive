---
title: "Feisty wireless connection problem"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2007-06-05
Fresh Feisty install on laptop. Wired connection worked immediately, but no wireless (worked in Edgy).

Here is my kernel description
dexter@dexim-laptop:~$ uname -a
Linux dexim-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

Here is my connection data
dexter@dexim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and scan results

dexter@dexim-laptop:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:C0:B8:D6
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz
                    Quality=57/64  Signal level=57/65  
                    Encryption key:off
                    Extra:tsf=00000068c9308e96



Any advice would be appreciated.

Also what is wmaster0 and how does it differ from wlan0?

---

### Post by Buster95 on 2007-06-09
Still struggling with getting wireless to work.

In the absence of advice from anyone on the forum, I repeated all previous steps. Strangely,  iwlist scanning returned a different result this time.

dexter@dexim-laptop:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

Summarising what I know:
1 My laptop wireless card worked with Edgy, but not with Feisty.
2 My laptop ethernet connection works better on Feisty than it did on Edgy. Before, I had to disable ipv6 to get the ethernet to work. This time it just "kicked in".
3 I have enabled wireless on wlan0  in system/networking with ESSID "NETGEAR" and the default password. That's the same one that gets me into the Net gear DG834G wireless router setup.
4 I have disabled wireless on wmaster0 (because I have no idea what it is).
5 I downloaded WIFIRadar. It cannot see my router (or any other local router).
6 I have other family users of the wireless router, so I know it works.

Unless I can get advice from anyone, I will assume that Feisty simply doesn't like my wireless card driver. I will then attempt to make it more palatable with ndiswrapper. However, I'd like to be sure that I've done every thing possible first.

Any advice?
Thanks

---

### Post by kev_l1 on 2007-06-13
What version of firmware is loaded on the dg834g router? I upgraded my version yesterday to 4.01.28 and my Feisty wireless connection stopped working.

Just reverted to 4.01.20 and up it came! Cannot see anything on the netgear website/upgrade details as to why the upgrade killed my Fiesty wireless connection.

Worth a try?

---

### Post by Buster95 on 2007-06-14
Hello kev,
The routers firmware is the latest available as of a few weeks ago. One of the first things I did when I couldn't get it to work was to update the firmware. It made no change. It didn't work before and it doesn't work now.

The wireless router works well with my daughters laptop running XP, so I know it works. My sons Apple Powerbook works OK on the router with ethernet but can't find the wireless. My Feisty works on the ethernet connection but also can't find the wireless. I suspect that our on-board drivers are the problem but I'm not sure what to do about it.

Cheers

---


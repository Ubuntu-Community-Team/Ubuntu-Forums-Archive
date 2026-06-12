---
title: "Can't enable wireless network (noob question)"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by switchcase on 2007-12-02
Hi, I just installed ubuntu and im having trouble connected to my wireless router. It seems that even when I enable networking and wireless the wirless card is still disabled (according to the output of "lshw -c network").

Im using an ASUS WL-138G V2 wireless network card and a Netgear DG843G router.

There is no avaiable wireless netowkrs apearing in the menu but if I "connect to existing network" and type the ESSID in iit appears to be connected to the router, with the bars icon showing but its on 0%.

Any help would be great.

Thanks,
Chris.


[Edit:] It works fine in Windows... im using it right now using ASUS WLAN Utitlies.

---

### Post by cmp1988 on 2007-12-02
Output of the command "iwconfig" (without quotes)?

---

### Post by switchcase on 2007-12-02
The output of iwconig was:

> lo
        no wireless extensions.



eth0
      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"

          Mode:Managed  Access Point: Invalid   

          RTS thr:off   Fragment thr:off

          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

... although when I tryed this time i couldnt even get to the point where the icon changes to the bars.

There are no networks listed and it appears that the card cannot see the router.

i just read that the card I am using (ASUS WL-138G V2) is only partially supported out of the box... what do I need to do to sort this out? bearing in mind I have no other way to connect to the internet other than through wireless.

thanks.

---

### Post by Lord DarkPat on 2007-12-02
this might seem silly, but if u are running windows on that computer too, boot windows, enable ur wireless card, then reboot back into ubuntu. The same thing happened to me and I made a thread a while ago, Hopefully it will work now

---

### Post by switchcase on 2007-12-02
Ive tryed that.. didnt work. Thanks anyway Lord DarkPat.

---

### Post by switchcase on 2007-12-02
Woohoo! Got it working!

For anyone who's having this problem -> [read this.]("http://ubuntuforums.org/showthread.php?t=405990")

Ubuntu is brilliant by the way!

---


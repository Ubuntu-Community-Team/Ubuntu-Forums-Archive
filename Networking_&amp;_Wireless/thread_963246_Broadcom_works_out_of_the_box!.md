---
title: "Broadcom works out of the box!"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by agim on 2008-10-30
My only constant annoyance, since I switched to linux about a year and a half ago, was my motherf*****g Broadcom wireless card. With 8.10, it worked out of the box. I guess Dell and Broadcom, together with Canonical, released a Broadcom driver for us.
I love this new version.
Great work!

---

### Post by kspncr on 2008-10-30
Could you post the output of "lspci | grep Broadcom"? I'm hoping we might have the same wireless card and it will work out of the box for me too, so I'll know before I install Intrepid.

---

### Post by beta.tester on 2008-10-30
Failing that just try to "live cd" option :)

Mine run on an Atheros Chipset from the box and found it worked brilliantly even in the live version! Highly impressed ;)

It still continues to work after installing and applying updates and even a new kernel revision ;)

All you guys out there take a BIG pat on the back for all your hard work!

kind regards   john

---

### Post by JohnBUK on 2008-10-30
I have a Dell (about 5 years old Inspiron 8600) which still has the same problem re Broadcom Wifi card. But a couple of days ago saw an article on Lifehacker showing how one can run a small Distro from a USB stick using Unetbootin. I downloaded at random PuppyLinux and it runs first time using my Wifi card!! So presumably they have a driver - in which case how does one find it?

---

### Post by agim on 2008-10-30
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)


Link to article discussing new broadcom drivers:
[http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive](http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive)

Link to Broadcom drivers (though they come with the ubuntu 8.10 rc):
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Ayuthia on 2008-10-30
It does cover the 4311, 4312, 4321, 4322, and 4328 cards.  The 4328 card is not listed, but there have been reports that it does work with the 4328 card.

---

### Post by Metaleks on 2008-10-30
> **Ayuthia said:**
> It does cover the 4311, 4312, 4321, 4322, and 4328 cards.  The 4328 card is not listed, but there have been reports that it does work with the 4328 card.
It doesn't work with the 4328 card for me.

---

### Post by Ayuthia on 2008-10-30
> **Metaleks said:**
> It doesn't work with the 4328 card for me.

Out of curiosity, did you unload the b43, ssb, ndiswrapper modules before loading the wl driver?  Also are you using encryption (if so, what kind)?  I have seen a few out there that have also said that they were not able to use it with the 4328 card, but it was posted in the sticky where we were not able to provide any community support so I have not been able to see why they did not work.

---

### Post by Metaleks on 2008-10-30
> **Ayuthia said:**
> Out of curiosity, did you unload the b43, ssb, ndiswrapper modules before loading the wl driver?  Also are you using encryption (if so, what kind)?  I have seen a few out there that have also said that they were not able to use it with the 4328 card, but it was posted in the sticky where we were not able to provide any community support so I have not been able to see why they did not work.
The fix is trivial. It seems that the ssb module is loaded first, as its part of the kernel. The wl module is loaded after, and clearly something isn't being blacklisted. Anyhoo, the fix is:

EDIT: FIX REMOVED! [Visit this thread for a better fix and discussion on this issue.]("http://ubuntuforums.org/showthread.php?t=959451")

---

### Post by Ayuthia on 2008-10-30
> **Metaleks said:**
> The fix is trivial. It seems that the ssb module is loaded first, as its part of the kernel. The wl module is loaded after, and clearly something isn't being blacklisted. Anyhoo, the fix is:

```
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
```

For anyone following the thread: the first command isn't needed if it spits back an error.

I think I am confused.  So you were able to get it to work after you did that or are you saying that you did that and the 4328 card still did not work?  If it still did not work, were you using encryption?  Also, could you post the results of lspci -nnm for your card?  I just want to keep track of it for future reference.

---

### Post by Metaleks on 2008-10-30
> **Ayuthia said:**
> I think I am confused.  So you were able to get it to work after you did that or are you saying that you did that and the 4328 card still did not work?  If it still did not work, were you using encryption?  Also, could you post the results of lspci -nnm for your card?  I just want to keep track of it for future reference.
Sorry for the misunderstanding! It worked *after* I applied the fix.

---

### Post by kspncr on 2008-11-07
> **agim said:**
> 01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)


Thanks! It works out of the box for me too. Awesome, huh?

---


---
title: "Meerkat AP (mode master) fails with Aethros ath9k"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Eric.B on 2011-02-10
I am trying to setup my linux box as an access point (and bridging to a network connection), but failing miserably at step 1.  How to get it in AP mode?

My system is:
Linux ubuntu 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

As I understand it the ath9k drivers support the master mode, however I get this error:
user@ubuntu:~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

I have seen a few comments on the web about it being a problem with the driver configuration but no clues as to how they fixed it.  Can someone point me in the right direction?

(FYI -- I've looked into the madwifi drivers but the install seems pretty complicated and I would hate to break something that is already working)

Thanks

---

### Post by cariboo on 2011-02-10
Linux is case sensitive, you may need to use the following command to set master mode:

```
sudo iwconfig wlan0 mode Master
```

---

### Post by Eric.B on 2011-02-10
Actually I found this might be the problem:

> This is failure by design.  The mac80211 stack does not contain the  required components to run in master mode by itself&#8230; Rather than let  users set it to master mode and not have it work, it tells you that the  operation is not supported&#8230;..With mac80211, you NEED hostapd for any  sort of functional access point. from [http://acx100.erley.org/stable.html](http://acx100.erley.org/stable.html)

So now on to hostapd to see if I can get my AP up....

---


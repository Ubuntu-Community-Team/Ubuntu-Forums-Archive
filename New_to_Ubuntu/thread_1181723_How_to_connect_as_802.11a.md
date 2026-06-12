---
title: "How to connect as 802.11a"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by PingMonster on 2009-06-08
Hi..I have Intel Pro Wireless 2915ABG.
How can I connect to wireless using 802.11a?

Any other Windows machine are using 802.11a and connecting fine but not ubuntu.
It always use 802.11g.

Can anyone?

---

### Post by 3rdalbum on 2009-06-08
So, does Ubuntu successfully connect to the router via Wireless G? If so, then there's no problem as far as I can see. As long as the Windows machines can connect to the router, and the Ubuntu machines can connect to the router, it doesn't matter how they are connecting. If you are having trouble getting the computers to interoperate, then the wireless protocol is not the problem.

If Ubuntu is failing to connect because the router doesn't understand G, then there's a simple solution to force your wireless card to work in A mode only.

On the command line, type this:

```
sudo iwconfig wlan0 modu 11a
```

That is, assuming your wireless card is "wlan0". It should be.

I'd highly suggest upgrading your router to something capable of G speeds. A is terribly slow.

---

### Post by PingMonster on 2009-06-09
Thank you for that. That did the trick.

Yes, there is no problem connecting as 11g.
And my wireless router do provide a/b/g.

I just want to force my notebook to connect as 11a.

BTW... "A is terribly slow"....???
Do you mean.."B is terribly slow"...!!!

---

### Post by nandemonai on 2009-06-09
```

                       802.11b	802.11g	802.11a	802.11n
Max Data Rate (Mbps)	11	54	54	300
Actual Throughput	5	20	22	146
Interference	        High	High	Low	Low
Compatibility	        b	b/g     a	a/b/g/n
Spectrum	        2.4GHz	2.4GHz	5GHz	2.4 & 5 GHz

```

---

### Post by PingMonster on 2009-06-09
Thanks, nandemonai.


Wish I could get 11n....just wish... (Does Aironet 1230AG have 11n support?)

---


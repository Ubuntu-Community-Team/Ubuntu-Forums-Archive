---
title: "MCE Remote works in Ibex but not in Hardy. Need help."
date: 2009-01-26
forum: New to Ubuntu
---

### Post by MockY on 2009-01-26
My MCE remote works out of the box with Intrepid. All I have to do is install Lirc and set the config to use mceusb.

This is not the case in Hardy Heron unfortunately and I need some help setting it up.

I have followed the instructions noted here [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote), complied it and tried to run it. It fails pretty hard.

Once I install Lirc via apt-get again, I get this message:
```
************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

Setting up lirc (0.8.3~pre1-0ubuntu7.1) ...
 * Reloading kernel event manager...                                     [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC  lircd: there seems to already be a lircd process with pid 28336
lircd: otherwise delete stale lockfile /var/run/lircd.pid                                                 [fail]


```

So I went and killed that process and ran 
```
sudo /etc/init.d/lirc restart
```
which resulted in 
```
* Stopping remote control daemon(s): LIRC                               [fail] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 

```
If I run it again right afterwards, I get all [ OK ], but when I run irw, it bails. If I restart lirc right after that I get the same as above, one fail which goes away if I restart lirc again.

I am very confused to why it should be so damn hard to set it up. Even GeexBox supports it...but not Hardy. Bizarre.

Could someone please help

---


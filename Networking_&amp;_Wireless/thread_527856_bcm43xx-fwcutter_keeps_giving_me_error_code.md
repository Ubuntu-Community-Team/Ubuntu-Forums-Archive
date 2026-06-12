---
title: "bcm43xx-fwcutter keeps giving me error code"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by helsabot on 2007-08-17
i've read various guides on how to get my wireless working and most say to get bcm43xx-fwcutter and get firmware drivers but it keeps returning with an error code saying ```
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
02:08:28 ERROR 404: Not Found.
```
I have a Compaq V6105NR

---

### Post by Slychilde on 2007-08-17
What kernel are you using? To check type

uname -r

in a terminal.  If it says 2.6.22, you may have it installed right, but it could be the kernel is borked.  I have had my broadcom wireless card working for quite a while using fwcutter and it just broke with the new kernel. ><  

Have you had it working before?  Does typing

sudo iwlist eth1 scanning

return anything, where eth1 is the name of your wireless card (Wlan0, eth1, eth2, whatever)?  What does iwconfing eth1 say?  Especially note the link quality.

---

### Post by helsabot on 2007-08-17
hmm it may be the kernel cause mine says 2.6.20-16-generic. and i haven't had a wireless connection yet and i have a slide switch on my laptop and it doesn't turn blue like it did on windows ever. and what can i do to change or update the kernel?

---

### Post by helsabot on 2007-08-17
and it says my interface doesn't support scanning.

---

### Post by helsabot on 2007-08-17
any suggestions?

---

### Post by Slychilde on 2007-08-17
You can turn it on by hitting Fn+ F2 on your keyboard; it may be different on yours, just take a look.  It won't work unless the wireless light is on.

I never had a problem with that kernel version, so I don't think it's the kernel.  The regression seems to have started in 2.6.22.  Can you paste the output from some of the commands I posted before?

---

### Post by helsabot on 2007-08-18
when i did the sudo iwlist eth1 scanning i got

```
eth1      Interface doesn't support scanning : No such device
```

and i have built in WiFi

---

### Post by helsabot on 2007-08-18
also my light is on but it's red, and it's supposed to be blue when it's wireless is searching.

---

### Post by Slychilde on 2007-08-18
That means the driver is not installed.  Try using the [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29") method, maybe.

---

### Post by helsabot on 2007-08-18
hmm  i went through all the steps on that and all of them returned an error code, and i did a second time and it had the sam results so i'm not sure of what to do.

---

### Post by spd106 on 2007-08-18
If you still want to use the bcm43xx-fwcutter then download the SoftMAC firmware from this page, [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

It will be a more reliable source because it's the main development website for open source Wifi drivers on Linux.

It you've decided to go with ndiswrapper instead, then by all means continue with that.

---

### Post by Slychilde on 2007-08-19
Your link didn't work. =\

Can you relink? Not sure why it doesn't work.

---


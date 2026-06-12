---
title: "rt2870 driver"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by t_virus on 2009-05-04
hi all,
i have an issue... rt2870 drivers work in wusb600n but not in smswusbs-N. even though i connect to wireless but i cant reach inetrnet.

any solution?

thankx

---

### Post by mizunoX on 2009-05-04
Hey there,

I'd like to try to help you but your post isn't very clear - at least not to me.

Are you saying that you've downloaded driver for the ralink 2870 chipset, installed it but it's not working for your USB 802.11n device (which I'm assuming is called 'smswusbs-N')

Who makes this device?  I googled the name above and found nothing.  
First we should confirm that it uses the 2870 chipset, then we'll work on adding an identifier to the driver before compiling.

---

### Post by t_virus on 2009-05-04
thankx for replaying mizunoX,
smcwusbs-n is from [www.smc.com](www.smc.com) and this adapter shows like unmanaged, dont capture my network. although i have a linksys wusb600n that can connect to wireless but internet pages dont open. its connected but its like it isnt.
sorry if it sounds a little confusing... im portuguese!!:guitar:

ps: i got the ralink rt2870 from ralink.com that should work in bouth but only works with the linksys. linksys (a,b,g,n) smc (b,g,n)

---

### Post by mizunoX on 2009-05-04
I used these tips to get my card working for the last release of ubuntu:
[https://answers.launchpad.net/ubuntu/+question/45440](https://answers.launchpad.net/ubuntu/+question/45440)

So with the device plugged in go to the terminal and type
```
lsusb
```

..then find your network card in results.

Mine was:

```
Bus 001 Device 006: ID 1737:0071 Linksys 
```

Now download and extract this file: [http://rapidshare.com/files/160951015/WUSB600N.tar](http://rapidshare.com/files/160951015/WUSB600N.tar) (this is an older version of the driver.. only because I don't know where to make these changes in the new version) , edit rt2870.h from the include folder.
Now see in the screenshot where I've added my card using the identifier that I found with lsusb?  If your card's identifier is not listed in this driver, add it using the same format that I did.
[IMG]http://img100.imageshack.us/img100/9150/wusb.png[/IMG]

Then compile and use the driver by following the rest of the instructions from my first link.

A bit confusing, but I hope this gives you something to try.

---

### Post by t_virus on 2009-05-06
hey there,
i cant install that driver in this kernel...:(:(

how can i change the option of A/B/G/N to B/G/N??
if i do this i could have the SMC (smcwusbs-n) working. i think the adapter dosent work cause of wireless A. SMC is only B/G/N

thankx

---

### Post by acaa on 2011-05-13
Hi. did you find how to solve the problem?

thanks in advance

---

### Post by t_virus on 2011-05-13
yes i did man, just follow all Thread and you´ll find it

---


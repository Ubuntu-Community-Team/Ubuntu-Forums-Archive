---
title: "Hi, new user getting confused by lack of wireless"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by veryunknowledgableuser on 2008-12-28
Hi I have decided to try ubuntu, the latest version, and it looks very nice and is very quick, but why wont my wireless Netgear WG311v3 work? the only solutions I have found are way over my head,so I'm asking,is there an easy way to install this, or do I have to go back to using windows? I dont really want to but not having the net is a bit of a large problem.

Many thanks in advance.

---

### Post by masque7 on 2008-12-28
What you need to understand is that with every peripheral out there, someone from the Linux/ubuntu team (or community) has to write device drivers for it. It's not the fault of the operating system you're using, but in this case Netgear for not writing a Linux driver.

In many case, you should check if your hardware/peripherals are supported before making the move to Linux (saves a lot of headaches). 

However, if you go [here](http://www.linuxquestions.org/questions/linux-wireless-networking-41/success-netgear-wg311v3-400257/) it seems like someone has had success... :)

Hopefully you might be able to get them working following that thread, or just keep posting back here. If all else fails, could always buy a wireless adapter that 100% works natively with Linux.

---

### Post by ieee488 on 2008-12-28
> **masque7 said:**
> What you need to understand is that with every peripheral out there, someone from the Linux/ubuntu team (or community) has to write device drivers for it. It's not the fault of the operating system you're using, but in this case Netgear for not writing a Linux driver.

In many case, you should check if your hardware/peripherals are supported before making the move to Linux (saves a lot of headaches). 



**Excellent** point!!!

Some users, not the OP, get all huffy about how their particular piece of hardware doesn't work in Linux and works in Windows.

Well, the manufacturer has to pay someone to write the driver for Windows unless Windows already has that driver which means Microsoft paid for someone to write the driver. Nothing "just works" with Windows. 

And, the people who write the drivers for Linux don't get paid. Hats off to them!

---

### Post by ugm6hr on 2008-12-28
> **masque7 said:**
> However, if you go [here](http://www.linuxquestions.org/questions/linux-wireless-networking-41/success-netgear-wg311v3-400257/) it seems like someone has had success... :)

Check the output from:

```
lspci
lshw -class network
```

This will confirm the chipset / device.

If it is indeed the WG311v3 - see the ndiswrapper entries #29, 35-38 for that device here: [http://burnthesorbonne.com/ndiswrapper/m-n.html](http://burnthesorbonne.com/ndiswrapper/m-n.html)

Is does appear like you will have to use ndiswrapper to get it to work with the Windows 2000 driver (on your CD).  Unfortunately, the link to the Netgear driver appears to be dead.  This may help: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

So - will it be easy? No.  Is it possible? Yes.

---


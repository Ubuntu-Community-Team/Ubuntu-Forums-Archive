---
title: "something wrong with my ubuntu"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-30
i have ubuntu 10.10 installed in my laptop.i have an EVDO cdma usb modem. everything was fine till some days back.my cdma modem was working fine on ubuntu but it seems something is wrong now as ubuntu is not recognising it as a modem but just a usb pen pendrive
also ubuntu 10.04 doesnt support my modem.so is it likely that my ubuntu has automatically degraded to 10.10?wat is the real problem? please help... thanx in advance to all:mad::mad::mad:

---

### Post by Megaptera on 2011-01-30
Hi,
I can't help much other than to say if you installed 10.10 it still is 10.10, you'd have to remove 10.10 to put 10.04 on - it wouldn't happen without a lot of intervention from you. So I hope that helps abit 'til some more help comes along?

---

### Post by nm_geo on 2011-01-30
> **neo_aryan said:**
> i have ubuntu 10.10 installed in my laptop.i have an EVDO cdma usb modem. everything was fine till some days back.my cdma modem was working fine on ubuntu but it seems something is wrong now as ubuntu is not recognising it as a modem but just a usb pen pendrive
also ubuntu 10.04 doesnt support my modem.so is it likely that my ubuntu has automatically degraded to 10.10?wat is the real problem? please help... thanx in advance to all:mad::mad::mad:

  Let's find out first.. open a terminal..copy and paste the following

```
lsb_release -a
```Then
  ```
uname -a
```

---

### Post by Rab22 on 2011-01-30
> **neo_aryan said:**
> i have ubuntu 10.10 installed in my laptop.i have an EVDO cdma usb modem. everything was fine till some days back.my cdma modem was working fine on ubuntu but it seems something is wrong now as ubuntu is not recognising it as a modem but just a usb pen pendrive
also ubuntu 10.04 doesnt support my modem.so is it likely that my ubuntu has automatically degraded to 10.10?wat is the real problem? please help... thanx in advance to all:mad::mad::mad:

Have you changed anything since the last time it worked? Did you unplug and replug it back in? 

Can you provide the output of ```
lsusb -v
```

---

### Post by vivek.pandey on 2011-01-30
> **nm_geo said:**
> Let's find out first.. open a terminal..copy and paste the following

```
lsb_release -a
```Then
  ```
uname -a
```

lsb_release -a

vivek@NEO:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
vivek@NEO:~$ 

uname -a
vivek@NEO:~$ uname -a
Linux NEO 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
vivek@NEO:~$

---

### Post by asmoore82 on 2011-01-30
> **neo_aryan said:**
> ... ubuntu is not recognising it as a modem but just a usb pen pendrive ...

These types of flip-flop devices require the "usb-modeswitch" package.
The problem must lie there.

---

### Post by vivek.pandey on 2011-01-30
> **asmoore82 said:**
> These types of flip-flop devices require the "usb-modeswitch" package.
The problem must lie there.

thanx a lot for your answer 
what i did was i went to synaptic and upgraded usb-modeswitch and usb-modeswitchdata..and bingo its working.....

---

### Post by desnaike on 2011-01-30
Just so u know some kernal updates break wireless and u have to reinstall such is my case 3 out of last 5 updates.

---


---
title: "[SOLVED] d-link g122"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-02-22
Hi,
I recently installed Ubuntu 7.10 (alternative) as a dual boot on my desktop pc.
The other OS is XP Pro.
I have a d-link g122 usb adapter that has got its drivers installed for my XP Pro OS - this works great.

On my Ubuntu install I noticed that the d-link g122 recognized my wireless modem (even when I did not install any drivers) - does this mean that I never need to install drivers?

The question I have is that at first the d-link g122 got me wireless internet on my Ubuntu OS (very slow connection though), then without warning the d-link g122 stopped picking up my wireless modem. This is very strange behavior. What is the best solution?

---

### Post by Hightide on 2008-02-23
HI Rytron

have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188").it may help.

regards

:)

---

### Post by Rytron on 2008-03-06
that link is tough to follow for a Ubuntu beginner.

sometimes I can get an hour on my internet connection via wireless.
other time it may cut out after 5 minutes. and amazingly when I remove the usb adapter and plug it back in - the connection reestablishes itself. I have installed drivers via ns-wrapper - .inf file I got. This .inf was in a d-link g122 driver package I downloaded.

the only hitch I have with Ubuntu is the trouble with wireless connectivity.

---

### Post by Rytron on 2008-06-09
I used this tip to speed up the internet when using Ubuntu:

Terminal:
```
sudo gedit /etc/modprobe.d/aliases

#alias net-pf-10 ipv6

change to:
alias net-pf-10 off

save,close,exit

reboot

```

Regarding the wireless connection dropping, I used ndiswrapper and downloaded the inf files. I tried each inf file until one worked(it should say Hardware Present:Yes in ndiswrapper).

---


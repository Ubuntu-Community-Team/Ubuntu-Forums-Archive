---
title: "Atheros bad reception on Ubuntu"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by heluani on 2008-08-01
Hello there, I am trying to return to Linux after several years of Mac OS X. I just installed Heron on a Lenovo Thinkpad x61t tablet
```
****@****:~$ uname -a
Linux ***** 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux
****@****:~$ 

```
with the Atheros based wireless card:
```

****@*****:~$ lspci | grep theros
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

```
```

****@*****:~$ dmesg | grep Atheros
[   36.220419] wifi0: Atheros 5212: mem=0xfdf00000, irq=17

```
but I'm stupid enough that I don't even know which restricted driver am I using. The problem is that I can't get any reception if I am further than 10 feet from my router. I have found several people pointing this issue here but no answer (at least that I understand). I was wandering if this issue was solved or if you have any kind of advise. Should I compile madwifi from svn? ....

Thanks

R.

---

### Post by heluani on 2008-08-02
[UPDATE] Well, I tried ndiswrapper instead of Madwifi and still same problem, I have to be on top of my router to connect. I can't control the sensitivity directly with iwconfig (says not supported) and I think this is the issue. Any help will be appreciated.

R.

---

### Post by heluani on 2008-08-02
Hi there, I was using the wrong Windows driver for ndiswrapper. Now with ndiswrapper running instead of ath_pci I get the right speed and signal everywhere, but the problem is that after reboot, sometimes (not always, but almost) the card doesn't negotiate with my router.

Looking at the router logs I see that it shows attempts all the times from mac address 00:00:00....

but iwconfig shows the right Hardware address...

I'm confused... sometimes it works, sometimes it doesn't...

R.

---


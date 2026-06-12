---
title: "Network not identified"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by rohitwason on 2011-01-02
Newbie for Ubuntu (10.10)...just installed on a dual-boot machine (alongside Windows-7)

Neither wireless nor wired connections work. I am sure I am missing something small

Tx

---

### Post by synicalx on 2011-01-02
Do you happen to know what network device your computer is using? Not so common with wired connections, but wireless cards are always a bit of fun...

---

### Post by ivanovnegro on 2011-01-02
> **rohitwason said:**
> Newbie for Ubuntu (10.10)...just installed on a dual-boot machine (alongside Windows-7)

Neither wireless nor wired connections work. I am sure I am missing something small

Tx

Can you see some network options in Ubuntu?
Is it working on Windows?

---

### Post by rohitwason on 2011-01-02
yes, networks are both working in Win7. The devices I'm using are:

1) Broadcom NetLink Gigabit Ethernet
2) Dell Wireless 1397 WLAN Mini-card

My wireless router is Linksys WRT160N V3

But I guess my problem is not only wireless, but ethernet too?

Thanks

---

### Post by rohitwason on 2011-01-03
> **rohitwason said:**
> yes, networks are both working in Win7. The devices I'm using are:

1) Broadcom NetLink Gigabit Ethernet
2) Dell Wireless 1397 WLAN Mini-card

My wireless router is Linksys WRT160N V3

But I guess my problem is not only wireless, but ethernet too?

Thanks
Anybody???

---

### Post by ivanovnegro on 2011-01-03
> **rohitwason said:**
> Anybody???

Ok, Im not a specialist and hoping that somebody could join also.
I think we need more output here, errors and so on.
[Here]("https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html") a Link to some problems with network on Ubuntu and some how to's. You could check some things and post it here.

---

### Post by spiky001 on 2011-01-03
rohitwason Hi can you boot the live cd option ( thats the cd you used to install) but use option to use without changes to pc, make sure eth0 cable is in see if it works then.

---

### Post by rohitwason on 2011-01-03
> **spiky001 said:**
> rohitwason Hi can you boot the live cd option ( thats the cd you used to install) but use option to use without changes to pc, make sure eth0 cable is in see if it works then.

Thanks all for helping with the 1st step: my wired n/w works now. Woohoo! I used the CD and it connected and may be installed a driver that wasn't there

Now onto the wireless connection. Is there a way  to get that going too? I installed some "Broadcomm" drivers from System --> Administration --> Additional Drivers

But to no use. I have even restarted my m/s after that

ONE DIFFERENCE: the PC is able to detect all wireless connections around me, it just gives up trying to connect after a while

Thanks again!

---

### Post by Ronin_301 on 2011-01-04
> **rohitwason said:**
> Thanks all for helping with the 1st step: my wired n/w works now. Woohoo! I used the CD and it connected and may be installed a driver that wasn't there

Now onto the wireless connection. Is there a way  to get that going too? I installed some "Broadcomm" drivers from System --> Administration --> Additional Drivers

But to no use. I have even restarted my m/s after that

ONE DIFFERENCE: the PC is able to detect all wireless connections around me, it just gives up trying to connect after a while

Thanks again!

Currently having the same problem. The Broadcom STA driver doesn't work at all, and the B43 driver shows the same symptoms you have of finding the network but never connecting. I post here when/if I find a solution.

---


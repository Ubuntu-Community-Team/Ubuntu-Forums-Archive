---
title: "PPPoE in Linux Mint"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Olhado on 2009-02-17
Question begins [here](http://ubuntuforums.org/showthread.php?t=1070462).

Now I have installed Linux Mint in dual boot with Ubuntu 8.10. Internet connection works in second OS, but still struggles in first OS.

For using my ADSL in Ubuntu I just typed 'pppoeconf' in terminal and got Internet working after one minute. But I can't do the same in LM and I don't know why. Everything gets right during following steps after running command, but in the end no connection appears in fact. No one from the 'Internet' section applications can do anything.

Here is result of 'plog' command ran just after the 'setting-up'. 

```

 plog dsl-provider
tail: cannot open `dsl-provider' for reading: No such file or directory
Feb 17 23:42:51 olhado-laptop pppd[7007]: Connect: ppp0 <--> eth0
Feb 17 23:42:51 olhado-laptop pppd[7007]: CHAP authentication succeeded
Feb 17 23:42:51 olhado-laptop pppd[7007]: CHAP authentication succeeded
Feb 17 23:42:51 olhado-laptop pppd[7007]: peer from calling number 00:15:C7:70:D4:19 authorized
Feb 17 23:42:51 olhado-laptop pppd[7007]: not replacing existing default route via 192.168.1.1
Feb 17 23:42:51 olhado-laptop pppd[7007]: Cannot determine ethernet address for proxy ARP
Feb 17 23:42:51 olhado-laptop pppd[7007]: local  IP address {IP goes here}
Feb 17 23:42:51 olhado-laptop pppd[7007]: remote IP address {IP goes here}
Feb 17 23:42:51 olhado-laptop pppd[7007]: primary   DNS address {IP goes here}
Feb 17 23:42:51 olhado-laptop pppd[7007]: secondary DNS address {IP goes here}

```

Wired connection, ADSL modem.

What should I do?

---

### Post by superprash2003 on 2009-02-17
are you trying to connect via ppoeconf on both pcs simultaneously?? if so , you cannot do that in an ADSL connection.. you need to set your modem to ppoe mode for that..

---

### Post by Olhado on 2009-02-18
> are you trying to connect via ppoeconf on both pcs simultaneously? No.

---

### Post by superprash2003 on 2009-02-18
post output of **ifconfig** from the terminal

---


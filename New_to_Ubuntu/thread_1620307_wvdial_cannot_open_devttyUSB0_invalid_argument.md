---
title: "wvdial: cannot open /dev/ttyUSB0: invalid argument"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by alecodd on 2010-11-12
sometimes i get this message when i try to run command "sudo wvdial". why? and how to fix it...

cheers

---

### Post by lkraemer on 2010-11-13
Why are you running sudo wvdial?  If wvdial and all it's dependencies are
installed, and you configured wvdial with:
```

sudo wvdialconf /etc/wvdial.conf

```
wvdial should locate your modem, and build your configuration file.

But, before you got that far you should have set up your pap-secrets
file with:
```

sudo pppconfig

```

Once wvdial is working setup Gnome-PPP.

REF:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4

lk

---

### Post by azertyh on 2010-11-13
hello,
have you configured your wvdial.conf?

---

### Post by alecodd on 2010-11-14
i tried to send a private message, but i was not successful whatever..

so thanks for both of you!

---

### Post by lkraemer on 2010-11-14
alecodd,
Your PM's worked fine.

Thanks.

lk

---

### Post by azertyh on 2010-11-14
hello,
see the doc about wvdial [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

see also this [http://platonic.techfiz.info/2008/03/04/hacking-bsnl-evdo-on-linux/](http://platonic.techfiz.info/2008/03/04/hacking-bsnl-evdo-on-linux/)

---


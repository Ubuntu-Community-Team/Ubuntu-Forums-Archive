---
title: "problem with dial-up driver hsfmodem_7.80.02.04full_i386: not recognizing modem"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by sstewart207 on 2009-05-05
hello again. i seem to be having trouble with my dial up modem. i installed hsfmodem_7.80.02.04full_i386.deb and then ran the sudo pppconfig command and typed in all my settings but when i try to connect using 'pon' or the Network program, it just doesnt dial anything. 

i need help!!! linux can be very frustrating and confusing sometimes!! :(

---

### Post by sstewart207 on 2009-05-05
help! plz? ;)

---

### Post by sstewart207 on 2009-05-06
hellooo??? lol

---

### Post by lkraemer on 2009-05-06
207,
If you're sure that you have the proper settings inserted when
you ran pppconfig, then I'd suggest that you try wvdial and see what
that gives.

Assuming that your modem Driver was installed correctly, and you
received the proper help from the folks at [www.linmodems.org](www.linmodems.org),
you should be able to make it work......but, winmodems can be a bugger
and that is why I still use an External Serial USRobotics modem.

your /etc/ppp  files...... pap-secrets and chap-secrets should have 
the following.  Better double check them!

```

yourlogin@isp.net * yourpassword

```

```

sudo wvdialconf /etc/wvdial.conf

```

use:
```

sudo gedit /etc/wvdial.conf

```
to change your loginname, password, and phone number.
Also add:
```

New PPPD = yes
stupid Mode = yes.

```
to wvdial.conf

to dial out use

```

wvdial

```

Good Luck!

lkraemer

---

### Post by sstewart207 on 2009-05-06
> **lkraemer said:**
> 207,
If you're sure that you have the proper settings inserted when
you ran pppconfig, then I'd suggest that you try wvdial and see what
that gives.

Assuming that your modem Driver was installed correctly, and you
received the proper help from the folks at [www.linmodems.org](www.linmodems.org),
you should be able to make it work......but, winmodems can be a bugger
and that is why I still use an External Serial USRobotics modem.

your /etc/ppp  files...... pap-secrets and chap-secrets should have 
the following.  Better double check them!

```

yourlogin@isp.net * yourpassword

```

```

sudo wvdialconf /etc/wvdial.conf

```

use:
```

sudo gedit /etc/wvdial.conf

```
to change your loginname, password, and phone number.
Also add:
```

New PPPD = yes
stupid Mode = yes.

```
to wvdial.conf

to dial out use

```

wvdial

```

Good Luck!

lkraemer

thanks! :) :guitar:

---

### Post by sstewart207 on 2009-05-07
solved!! :)
i usrd the command 'sudo hsfconfig' to get the driver working. yay!!! :D

---


---
title: "Trouble accessing WEP secure wireless network"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by deanh42 on 2008-08-13
Hey Gang:

   When I got Ubuntu installed on my laptop, it shows my network on the network manager. When I click on it, it tells me to enter the passphrase. When I put in my 10 digit code, it tries to connect but fails. What went wrong? Any help would be great!

                     Thanks, Deanh42

---

### Post by tangibleorange on 2008-08-13
Hi.

Do you know what wireless card you have? Could you please post the output of the commands:

```
lspci
```
and
```
iwconfig
```

---

### Post by chili555 on 2008-08-13
> it tells me to enter the passphrase. When I put in my 10 digit codeI think it wants 10-digit codes in '64-128 bit Hex' and not in passphrase or password. Have you tried that?

---

### Post by kennedy7 on 2008-08-13
Hey you can try hard shock. That resets your router and password.
you just hold down the reset button turn it off then back on still holding reset hold 20 more seconds.

---

### Post by deanh42 on 2008-08-13
I had to use the 64/128 hex, that did the trick.

                        thanks, Deanh42

---

### Post by FallFromGrace on 2009-01-21
Very very new to Linux --- have been dual-booting Ubuntu for less than 2 weeks, and this particular problems was driving me crazy (especially since it was my first wifi issue). This post was really helpful! Thanks!\\:D/

P.S. Why does Ubuntu make you select the format in the first place?

---


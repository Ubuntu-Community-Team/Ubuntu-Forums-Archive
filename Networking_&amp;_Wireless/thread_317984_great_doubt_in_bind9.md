---
title: "great doubt in bind9"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by nortoncillo on 2006-12-13
i suscribed to google apps, to take out the mail server from my network, due to serious problems of hardware...

so i'm not 100% sure about how to add the mx records for the google mail in my host definition....

they should be go like this?

> mail        IN MX 1 ASPMX.L.GOOGLE.COM.
            IN MX 5 ALT1.ASPMX.L.GOOGLE.COM.
            IN MX 5 ALT2.ASPMX.L.GOOGLE.COM.
            IN MX 10 ASPMX2.GOOGLEMAIL.COM.
            IN MX 10 ASPMX3.GOOGLEMAIL.COM.
            IN MX 10 ASPMX4.GOOGLEMAIL.COM.
            IN MX 10 ASPMX5.GOOGLEMAIL.COM.

or like this?  :-k 

> @ IN MX 1 ASPMX.L.GOOGLE.COM.
@ IN MX 5 ALT1.ASPMX.L.GOOGLE.COM.
@ IN MX 5 ALT2.ASPMX.L.GOOGLE.COM.
@ IN MX 10 ASPMX2.GOOGLEMAIL.COM.
@ IN MX 10 ASPMX3.GOOGLEMAIL.COM.
@ IN MX 10 ASPMX4.GOOGLEMAIL.COM.
@ IN MX 10 ASPMX5.GOOGLEMAIL.COM.

has anyone done this before?

---


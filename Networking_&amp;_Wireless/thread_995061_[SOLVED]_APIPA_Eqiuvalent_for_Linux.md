---
title: "[SOLVED] APIPA Eqiuvalent for Linux?"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-11-27
Hi,
I was doing this PrepLogic test and came across this question. Then I got to think - What is the APIPA equivalent for Linux?
Picture of question attached!

---

### Post by TutonicMonkey on 2008-11-27
This is a very good question I would also like to know the answer. I searched all over the web but found nothing. Going to flip off DHCP and see what happens.

---

### Post by Rytron on 2008-11-28
> **TutonicMonkey said:**
> This is a very good question I would also like to know the answer. I searched all over the web but found nothing. Going to flip off DHCP and see what happens.

What was the result?

---

### Post by puppywhacker on 2008-11-28
a zeroconf technique where an interface is asigned an address starting with 169.254 so that at least an ip-address is assigned.

the linux implementation is AVAHI

---

### Post by Rytron on 2008-11-29
> **puppywhacker said:**
> a zeroconf technique where an interface is asigned an address starting with 169.254 so that at least an ip-address is assigned.

the linux implementation is AVAHI

Thanks for clarifying that.

---


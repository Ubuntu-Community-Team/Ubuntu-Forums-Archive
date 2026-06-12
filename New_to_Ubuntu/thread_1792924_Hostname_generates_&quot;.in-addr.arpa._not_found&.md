---
title: "Hostname generates &quot;.in-addr.arpa. not found&quot;"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by numala on 2011-06-28
Hi
I am using Ubuntu 10.04.
When I type

> host myIPaddress

I get

> Host myIPaddress.in-addr.arpa. not found: 3(NXDOMAIN)

My file /etc/hosts starts with:
127.0.0.1       localhost
127.0.1.1       my-host-name

and my /etc/hostname reads:
my-host-name

Does anybody know how to solve it?
Thanks

---

### Post by Bachstelze on 2011-06-28
You can't have reverse DNS through a hosts file, you *need* a DNS server for that. What kind of IP (i.e. private or public) are you trying to get reverse DNS for?

---

### Post by numala on 2011-06-29
Hi
the IP is static and in a private network.

> **Bachstelze said:**
> You can't have reverse DNS through a hosts file, you *need* a DNS server for that. What kind of IP (i.e. private or public) are you trying to get reverse DNS for?

---

### Post by haqking on 2011-06-29
> **numala said:**
> Hi
the IP is static and in a private network.

you havent got reverse DNS, what exactly do you need ?

---

### Post by Bachstelze on 2011-06-29
> **numala said:**
> Hi
the IP is static and in a private network.

So you must have your own DNS server on the network to provide PTR records for your private IP addresses.

---

### Post by numala on 2011-06-30
Thanks for answering guys, I will talk again to the system administrator, even though he supports only windows :((
Thanks for answering guys :)

---


---
title: "Running squid and would like to keep SRC addresses"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by jared20 on 2014-05-15
Hey guys,

I know it sounds a little counter-intuitive but I would like Squid3 to keep the source IP addresses on all the packets (instead of rewriting itself as the source). I need this because I have an authentication mechanism further up that identifies users by matching their source IP.
 
I have looked at http_forward and a couple other ones but I was hoping that someone with a little more experience could help me, already spent a good couple hours on just this task.

Thanks in advance :)

Jared

---

### Post by SeijiSensei on 2014-05-15
It's not possible.  Squid resends the packet as if it is the HTTP client, not the machine behind it.

Maybe if you expand a bit on the "authentication mechanism" we can figure out a work-around.

I manage a Squid proxy in front of a few hundred desktops.  We control all access by IP address using ACLs in Squid.

---

### Post by HiImTye on 2014-05-15
you can but it requires some iptables and squid configuration, and it requires you to set squid up to run in transparent mode

---

### Post by jared20 on 2014-05-21
Hi guys! 

Sorry for the delay, been man down for a couple days.
I am running in transparent mode (its the same as intercept now right?). I have hypothesized a workaround, which basically involves switching around what is processed first (so now it will authenticate first and then pass onto squid). However, this is not ideal so please can you elaborate on those iptables + squid config @ HilmTye

---


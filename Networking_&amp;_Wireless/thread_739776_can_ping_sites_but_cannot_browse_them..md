---
title: "can ping sites but cannot browse them."
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by gkanu7 on 2008-03-30
Hello all,
i installed ubuntu 7.10 on my desktop.
my system config is
AMD Athlon 64.
MSI K8MMV mobo
768MB of RAM.

now the issue is, i can ping google or any other site thru the Terminal.
But i am unable to surf any using the browser.

i have ADSL connection,with dlink 502T as the ADSL router.
the ip is DHCP.

any suggestions on whts going wrong...

thanks :)

---

### Post by koenn on 2008-03-30
> **gkanu7 said:**
> 
now the issue is, i can ping google or any other site thru the Terminal.
But i am unable to surf any using the browser.

please show the output of ```
ping www.google.be
```
and post your browser proxy settings

---

### Post by superprash2003 on 2008-03-30
might want to try open dns server 208.67.222.222 and 208.67.220.220

---

### Post by stream303 on 2008-04-01
I'd also advise putting those opendns server addresses directly into the router's setup page for total ease of mind.  (Or your own isp's dns server addresses)

You can doublecheck them here at the lower right hand bottom of the page:

[http://www.opendns.com](http://www.opendns.com)

Being able to ping, yet not resolve any urls is a common pointer to dns troubles.

---


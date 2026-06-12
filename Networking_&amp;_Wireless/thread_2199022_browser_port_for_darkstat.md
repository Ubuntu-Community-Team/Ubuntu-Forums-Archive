---
title: "browser port for darkstat"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by ljube on 2014-01-11
HI all
I tried several times to access the address localhost:666, as written in the manual for darkstat, [here]("http://www.debianhelp.co.uk/darkstat.htm"), however I can not access the page. In the document file darkstat.c says
  unsigned short opt_bindport = 667;
static void cb_port(const char *arg)
{ opt_bindport = (unsigned short)parsenum(arg, 65536); }

however 667 also doesn't open. Please help

---

### Post by ian-weisser on 2014-01-14
Is darkstat running?

---


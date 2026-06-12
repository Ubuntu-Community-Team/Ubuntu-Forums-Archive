---
title: "No Drivers found?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Saudrapsmann on 2009-10-31
Hi, I'm new to Ubuntu. I just installed Ubuntu 9.10 onto my 5-year-old laptop and nothing is working. I can't connect to the internet, be it wireless or wired, and I can't put a new driver onto it because it doesn't recognize any USB flash drive. Help?

---

### Post by clhsharky on 2009-10-31
HI

Have you tried to activate wifi or Ethernet in network connections?
Wired has always worked in Unbuntu for me on everything I have used.
Also how you installed Ubuntu would help. "5-year-old laptop" doesn't tell us enough to help you. More info please.

---

### Post by sdpiowa on 2009-10-31
Did your peripherals work when running from the Live CD?

---

### Post by Saudrapsmann on 2009-10-31
I installed via Wubi. Had the same problems when I used LiveCD, thought Wubi would be easier.

The laptop is a Gateway with an AMD64 processor.

---

### Post by sdpiowa on 2009-10-31
Did you install the 32 bit version or the 64 bit version?

---

### Post by sandyd on 2009-10-31
please post the output of
```

uname -a

```

---

### Post by Saudrapsmann on 2009-11-01
32-bit.

uname -a results:

Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Edit: I looked it up, and doesn't that mean I'm actually running 64-bit? It didn't give me the option in Wubi between the two. Does this mean I'm going to have to uninstall this and reinstall the 32-bit version without Wubi?

---

### Post by Saudrapsmann on 2009-11-01
Uninstalled 64-bit and installed 32-bit. Found out the way to do it through Wubi.

uname -a:
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Exact same problems.

---


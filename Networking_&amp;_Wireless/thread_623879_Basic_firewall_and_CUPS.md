---
title: "Basic firewall and CUPS"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by stukov on 2007-11-26
Hi all,

    I have a Ubuntu 7.10 machine with simple iptables rules that allow everything OUT and only specific services IN. My first though was that allowing any traffic to ports 631 and 515 would do the trick. However, when I load the rules, the compute does not detect properly my network printers.

    I have a CUPS server running on a dedicated machine that shares all the printers I have. "iptables -L -n -v" shows my rules are correct and "lpstat -a" shows that printers are properly detected when the firewall is down.

Any thoughs?

Thanks !

---

### Post by timcredible on 2007-11-26
> **stukov said:**
> Hi all,

  
Any thoughs?


yeah, why are you filtering anything?

---

### Post by stukov on 2007-11-26
> **timcredible said:**
> yeah, why are you filtering anything?

The system is running on a laptop that connects often to public networks via wireless access points. Very sensitive information is stored into this laptop and this is why filtering packets via a firewall is very important for the users of this laptop.

The problem is not the use of a firewall but more in understanding how my CUPS client talks with my CUPS server. Sounds like IPP is not the only protocol used for printers detection.

---

### Post by stukov on 2007-12-07
The problem came from the firewall rules. They were not allowing traffic to the local CUPS server. That was the problem.

---


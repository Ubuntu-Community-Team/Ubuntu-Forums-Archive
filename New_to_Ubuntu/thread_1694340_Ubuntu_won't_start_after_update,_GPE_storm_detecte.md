---
title: "Ubuntu won't start after update, GPE storm detected"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Jarod_008 on 2011-02-24
Hi all,

I'm new on this forums and with ubuntu I hope someone can help me with my problem.

I was using Ubuntu without problems for a long time, but after installing an update my Ubuntu installation won't start anymore.

When I choose Ubuntu, Linux 2.6.32.-24-generic in the GNU GRUB the computer will go to the ubuntu login screen but will freeze there, I cannot even move my mouse.

When I choose Ubuntu, Linux 2.6.32-24-generic (recovery mode) the computer will freeze at this line:

**[5.813349] ACPI: EC: GPE storm detected, transactions will use polling mode.**

I hope someone knows what this means and how I can solve it. I already searched on google for the problem and on this forum but I cannot find how to solve it.

Thanks in advance for your reply.

Regards,

Jarod

---

### Post by Jarod_008 on 2011-02-28
Nobody who can help me? Is additional information needed, if so please tell me!

---

### Post by wep940 on 2011-02-28
I'm not sure of the exact syntax, but you might try putting ACPI=NO (it might be OFF, I don't know) to the boot line temporarily to see if it helps.  When at the grub menu, edit the boot line for the recovery console and try adding this.  I have no real idea if this will help, nor do I know if this is recommended.
 
I did a search on the web, and this has been happening to some people since at least 2008.  Some indicate it's a kernel bug, others that they just didn't find a solution.

---


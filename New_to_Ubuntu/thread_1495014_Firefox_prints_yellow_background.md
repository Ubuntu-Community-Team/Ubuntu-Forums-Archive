---
title: "Firefox prints yellow background"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-05-27
I have made a clean install of Lucid 10.04 on three different machines.

Bizarrely, when printing from Firefox, it prints a pale yellow background. This happens with all web pages on all three computers.

Not only is this rather irritating but also you can imagine that this uses up my yellow print cartridge really fast.

All other programs print perfectly fine. It's only Firefox with this problem.

This problem did not happen before, when the machines ran a mix of Hardy and Jaunty.

I've tried deleting the [FONT=Courier New]~/.mozilla[/FONT] folder so that Firefox starts with a clean slate, but the problem persists.

Does anyone have any idea how to solve this problem on Lucid?

More information:
One laptop with Lucid 32-bit; one netbook with Lucid 32-bit; one laptop with Lucid 64-bit.
Printer is HP Officejet Pro L7780.

---

### Post by Zill on 2010-05-27
Could be [bug 578920]("https://bugs.launchpad.net/hplip/+bug/578920").

A "fix" is suggested.

---

### Post by Paddy Landau on 2010-05-27
> **Zill said:**
> Could be [bug 578920]("https://bugs.launchpad.net/hplip/+bug/578920").

A "fix" is suggested.
Thank you, Zill! It worked for me on three Ubuntu machines and one Xubuntu.

I've subscribed to the bug; in the meantime I'll mark this as solved.

---


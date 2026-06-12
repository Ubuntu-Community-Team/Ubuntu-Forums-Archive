---
title: "[SOLVED] Linksys card was dected in 8.04 Desktop, not in Server"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by sjokomunn on 2008-10-27
Hey folks,

I've been searching through the threads but I haven't found a post that refers to this specific issue. If I've missed it, my apologies. A link would be greatly appreciated. Anyway, as the title suggests, my wireless works out of the box in 8.04 Desktop but when I install the Server edition the card does not exist as far as lspci or iwconfig are concerned. I'm wondering, what's the best first course of action to get this working? Thanks in advance.

-Sjoko

---

### Post by nixscripter on 2008-10-28
What is the card? The shortest path to the solution is to boot an 8.04 client LiveCD and see what driver is being used with the terminal command: ```
lshw -C network
```

---

### Post by sjokomunn on 2008-11-05
Thanks for the reply. I really didn't do enough investigation before posting. I've learned my lesson though. It wasn't even a linksys card although it does have an atheros chipset. Once I installed madwifi it started working just fine. Cheers.

-Sjoko

---

### Post by nixscripter on 2008-11-05
Glad to hear it. Please mark the thread as solved (under the thread tools menu).

---


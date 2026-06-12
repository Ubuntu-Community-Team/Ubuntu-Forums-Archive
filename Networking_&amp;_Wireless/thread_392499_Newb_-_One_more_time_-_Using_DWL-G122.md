---
title: "Newb - One more time - Using DWL-G122"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by dmizesr on 2007-03-24
OK, so I've seen this around the forums a few times but I'm wondering if there's anything new.

1. I'm running Edgy
2. I have a DWL-G122 Rev A2
3. I know virtually nothing about Linux

Now, unless you already hate me, could someone give me a concise, "for dummies" guide to getting the DWL-G122 working on my box? I did a standard live-cd install of Ubuntu downloaded right off the website.

Remember, I know NOTHING about Linux.

Any takers?

---

### Post by chili555 on 2007-03-24
No one here hates you because they were all newbies once, too; even old Chili!

It will help us to know what kind of pain we are signing up for if we knew which chipset this device uses. Open a terminal (don't you fell more experienced in linux already?) and type:```
lspci -v | less
```See that vertical pipe | above the \ on your keyboard? That means pipe the output from lspci -v through another command: less. That will allow you to scroll through the voluminous output you get.

Tell us the particulars of your G122 and we will probably take your case.

---

### Post by dmizesr on 2007-03-24
Appreciate it! I'll do it tonight when I get home. I'm fairly sure it's a Prism chipset, but I'll cut and paste the output just so we're all on the same page.

DWM

---


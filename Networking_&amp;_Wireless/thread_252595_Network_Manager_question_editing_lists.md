---
title: "Network Manager question: editing lists"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by montag451 on 2006-09-07
Is it possible to edit the Trusted and Preferred lists that Network Manager uses to connect to networks? Network Manager continually tries to connect to a network I don't have the password for, and I have to manually tell it to connect to my own.

---

### Post by mrvw0169 on 2006-09-09
Yes, any help would be great as this drives me nuts! But on the other hand, I think I found a way to fix our problem after looking around a little bit:

Goto your home folder and hit Ctrl+H (to view hidden files)
Navigate to .gconf/system/networking/wireless/networks/
Delete the offending network folder (or in terminal use rm -rf)

I have to restart to find out if this works... Deleting this key using gconf-editor won't work...

But any help on configuring the ORDER of the networks connected would be greatly appreciated! i.e. I get both my school's wireless network which sucks but I use at school and my own at home -- it will connect to the school's when it feels particularly stupid or somehow the school's network strength is greater than mine...

---


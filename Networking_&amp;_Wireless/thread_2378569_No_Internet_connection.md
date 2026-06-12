---
title: "No Internet connection"
date: 2017-11-24
forum: Networking &amp; Wireless
---

### Post by Jack_Shankle on 2017-11-24
Don't ask me how or why as I haven't the foggiest idea.
I went back to wiffies computer and it was downloading updates which it refused 
to do for me. The computer is now running ok.....

My wife's Ubuntu computer has no internet connection. She has been running Ubuntu
for over a year with no problems. I am on a windows computer trying to fix her problem. 
I know just enough about Linux to get myself into trouble.
Please, if you use abbreviations spell it out once.  
I restored a previous backup and that did not fix the problem.
I am also unable to do any updates. Reason Ubuntu says there is NO internet connection.

I am on the internet now in Windows with no internet problems. I also checked the cable
to see if any were lose. They seemed OK.
I have looked at the "check if already posted" and did not understand 90% of what I read.
Please help.
Thanks for any suggestions

Jack/Donna Shankle

---

### Post by chili555 on 2017-11-24
Let's gather some diagnostics first and then decide how to fix this thing. Please open a terminal Ctrl+Alt+t and run these commands one at a time:```
rfkill list all
lspci -nnk | grep -e 0280 -e 0200 -A3
```Jot those down and post them here and we'll take the next steps.

---


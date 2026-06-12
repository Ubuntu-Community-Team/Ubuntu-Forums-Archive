---
title: "Some basic knowledge...again (space on HD)"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by OllieGab on 2009-10-06
As a newbie I'm lacking some basic knowldege...again!
On my harddrive I've got just under 100G for my Ubuntu OS and all its folders and files. According to my system I have used 93%, which I feel is a rather large amount.
Should I interpret the output (below) as 90 G in / and the rest as being part **of** that 90G? I can understand that I have around 36G in my own home folder but should there really be so much "left over" in other folders? 
Doing:
 **sudo du / --max-depth=2 | sort -g**
I get a whole wack back, the end of it being:
[B]3423844	/usr
36895948	        /home/abcde
36896012	        /home
49076656	        /root/.local
49079652   	/root
90965264 	/[/B]

---

### Post by arrange on 2009-10-06
> **OllieGab said:**
> 
Should I interpret the output (below) as 90 G in / and the rest as being part **of** that 90G? Yes.

Normally */root/.local* does not occupy so much space. Have a look at */root/.local/share/Trash/* - you may find some bulky files in the root trash.

---


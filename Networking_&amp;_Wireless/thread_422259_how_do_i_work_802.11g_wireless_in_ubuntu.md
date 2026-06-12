---
title: "how do i work 802.11g wireless in ubuntu?"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by daninja on 2007-04-25
i have ubuntu 7.4 now and the 6.6 ver. but i dont know anything about ubuntu and hoping someone can help me load my built in wireless. i dont know anything else about it lol but u can ask and maybe tell me how i can help you to help me. please write back.

---

### Post by zvbxrpl on 2007-04-25
First, you should know that enabling wireless networking in Linux is more complicated than in windows.  This is entirely the fault of unhelpful manufacturers, who either do not bother to ship Linux drivers for their products, or produce drivers that cannot be included in most distros due to licensing restrictions.

If you have built in wireless I assume you are using a laptop.  How you go about enabling your wireless depends on what chipset your wireless card uses.  To find out, open a terminal (Konsole or equivalent) and type:

lspci -a

Look for something that might be a wireless card and cut and paste the results back here.  Are you using Ubuntu 7.04 (Feisty) or 6.06 (Dapper)?

It would also be useful to have some more information - what is the make and model of your laptop?  What kernel version is loaded (type uname -r to find out)?

---

### Post by Rickmeister on 2007-04-25
Hey

Absolute new-by. Installed Ubuntu last week and still, after reading 100s of forums can't get internet!!!!!!!
I have got a D-Link DWL-G520+, which worked on windows flawlessly...

If u can help me it would be mostly appreciated, otherwise i'm going back to windows...

---


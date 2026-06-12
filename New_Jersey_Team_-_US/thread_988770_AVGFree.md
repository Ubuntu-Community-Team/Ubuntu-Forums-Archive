---
title: "AVGFree"
date: 2008-11-20
forum: New Jersey Team - US
---

### Post by Dave2244 on 2008-11-20
Hello All,

I have a quick question. Ive installed avg on my 8.10. I get an error when my package installer goes to install it error: wrong architure 'i386'. My laptop running 8.04 - installed the avg no problem! <-- interesting! Any thoughts on what the deal could be?? 

Thanks
Dave
Central Jersey

---

### Post by prshah on 2008-11-20
> **Dave2244 said:**
> 
I have a quick question. Ive installed avg on my 8.10. I get an error when my package installer goes to install it error: wrong architure 'i386'. My laptop running 8.04 - installed the avg no problem! <-- interesting! Any thoughts on what the deal could be?? 


Both your AVG installer package and your laptop must use the same architecture; either i386 or amd64. The first is for 32-bit, the second for 64bit. To find out what operating system you are using, open a terminal and see```
uname -m
``` If it shows i386 or i686 then you're using 32bit and require the 32bit version of AVG. If it shows x64 or similar then you're using 64bit and need the 64bit version of AVG.

---

### Post by tvtech on 2008-11-20
> **Dave2244 said:**
> Hello All,

I have a quick question. Ive installed avg on my 8.10. I get an error when my package installer goes to install it error: wrong architure 'i386'. My laptop running 8.04 - installed the avg no problem! <-- interesting! Any thoughts on what the deal could be?? 

Thanks
Dave
Central Jersey

really? antivirus on nix?? really really? are you sure about that?

---

### Post by Dave2244 on 2008-11-21
> **tvtech said:**
> really? antivirus on nix?? really really? are you sure about that?


Yea it installed no problem on my notebook running 8.04


it has a problem with my desktop running 8.10

I figure it out sometime!!!!:guitar:

---


---
title: "Conky FAIL."
date: 2010-03-06
forum: New to Ubuntu
---

### Post by sven.cintern on 2010-03-06
First things first: I have searched extensively through the forums, but I can't find this bug. (that's probably due to me not having the foggiest idea what to search for, so if this is a repost, sorry)
 

 Anyway, my problem:
 For some reason my conky (Ubuntu Karmic) no longer works properly.  
 Even with the default script. It will launch, but then it places itself over the top of other windows, and messes up the system, So I can't close windows and if I try and move them, I get the whole drag effect, so it makes it look like there a hundred open windows.  
 At first I thought this was a script problem, but as I said, it even happens with the default script.  
 I did change my system (I installed bleachbit and did a cleanup), and after conky stopped working I removed it and reinstalled. No luck.  
 

 I started it from the terminal, and all seems fine.
 Here's the output
 
[INDENT]**Conky: desktop window (fc) is root window **
**Conky: window type - desktop **
**Conky: drawing to created window (0x4200001) **
**Conky: drawing to single buffer** 
[/INDENT] 

 Thanks in advance for your help,
 Sven

---

### Post by agnes on 2010-03-06
try the options

own_window no
double_buffer yes

---

### Post by sven.cintern on 2010-03-07
Thats, better, thanks.

:KS

---

### Post by proxess on 2010-03-08
Seems like the FAIL wasn't conky...

---


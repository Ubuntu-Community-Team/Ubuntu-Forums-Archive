---
title: "Shutting down says a program running"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-04-11
Hi Ya'll,
 I am using Lucid at the moment, when i go to shut down it tells me there is a program still running and asks if I am sure if I want to shut down. How do I find out what is running and when I do, how do I close it out? Also as a side note, I have gotten twice today a pop up that says I have encountered a serious kernel problem and I need to restart? What is this going on about?
Thanks

---

### Post by Sef on 2010-04-12
Do you get a message that says what is the problem?  Both could be related.

---

### Post by quadproc on 2010-04-12
> **AndyP79 said:**
> Hi Ya'll,
 I am using Lucid at the moment, when i go to shut down it tells me there is a program still running and asks if I am sure if I want to shut down. How do I find out what is running and when I do, how do I close it out? 
You can use several tools to see what is running.  Probably ps is a good place to start.  The running program might not be owned by you so you may need to use some options with ps, perhaps afx. You could also look in the System Monitor processes tab; some things such as background system tasks don't show up there so you might need to dig deeper.

Once you find the running process, you can use its PID (process ID number) and the kill command.
> Also as a side note, I have gotten twice today a pop up that says I have encountered a serious kernel problem and I need to restart? What is this going on about?
ThanksIt sounds like you have encountered a serious bug.  If your hardware is running OK with other operating systems then it would be useful to report a bug to the Ubuntu folks.

quadproc

---


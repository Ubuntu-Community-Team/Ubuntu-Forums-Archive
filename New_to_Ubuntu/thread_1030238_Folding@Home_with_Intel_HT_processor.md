---
title: "Folding@Home with Intel HT processor"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by LNB on 2009-01-04
Hi Guys, I have a PC that utilizes an older Intel Pentium 4 Hyper Threading CPU at 2.8 Ghz that makes the physical CPU act like two CPUs.  I've been successfully running Xubuntu on the box for the last week thanks to all the help from this forum.

I've installed Folding@Home and Origami using the instructions here:

[_https://help.ubuntu.com/community/FoldingAtHome#Installation_]("https://help.ubuntu.com/community/FoldingAtHome#Installation")  

When I check on the status of the folding, it seems to be running two work units, as shown below.

My question is as follows:  I think Folding@Home is using 100% of "both" of my CPUs, but I want to only use half the capacity as it seems to be slowing down other applications that I am running.  Is there a way to configure this app so that it either only uses 50% of both of my CPUs or only uses 100% of one of the CPUs?  

Thank you


```


LNB@ubuntu:~$ origami status

#########################################
current status of origami on ubuntu
#########################################
Status of FAH client(s): OK 

Completed WU on CPU #1: 
Completed WU on CPU #2: 

Current Work Unit
-----------------
Name: p4457_Seq50_Amber03
Tag: P4457R60C1G1
Download time: January 4 02:56:51
Due time: March 8 02:56:51
Progress: 14%  [|_________]
Current Work Unit
-----------------
Name: p4447_Seq45_Amber03
Tag: P4447R779C1G2
Download time: January 4 02:59:51
Due time: March 8 02:59:51
Progress: 13%  [|_________]

```

---

### Post by jbrown96 on 2009-01-04
not sure how to change folding@home but you can alter the priority of any process with nice and renice. You should check out the manpages for them ```
man nice
``` ```
man renice
``` You can find the pid (process id) from ```
top
``` then run ```
sudo renice PRIORITY -p PID
``` replace PRIORITY with a number -20 to 20 (more on priority below) and PID wiht the PID.

Priorities for user processes are usually at 0 and kernel stuff around -5. the lower the number the higher the priority. If you set it to 20, then folding@home will only run when nothing else wants to. You probably want something around 15-20. 

Next time you start folding@home, use nice to start it, and then you don't need to hunt down the pid.

---

### Post by LNB on 2009-01-04
Thanks for your reply.  I used the "top" command and got the following output with respect to Folding@Home.  If I'm reading this right, it looks like the program has a priority of 19.  If so, does that mean that Xubuntu will take away processing capacity away from Folding@Home on the fly when I run / work on other apps with higher priority?

Thank you.

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
 4911 origami   39  19 20068  11m 1216 R   94  0.4   1329:12 FahCore_78.exe       
 4914 origami   39  19 20072  11m 1216 R   91  0.4   1309:10 FahCore_78.exe       

```

---

### Post by swoody on 2009-07-02
LNB, just to answer your question, yes, the F@H client will clock itself back to allow any other apps to have the CPU power they require. The folding client will only use what's left over after everything else takes it's piece of the pie.

Just to let everyone know, Ubuntu's Folding at Home team does have it's own IRC channel! If you're looking for guidance, or answers to any questions you may have about folding, please feel free to stop by and pick our brains, or just hang out! You can find us at #ubuntu-folding on the FreeNode server!! I look forward to seeing you all on there :D

---


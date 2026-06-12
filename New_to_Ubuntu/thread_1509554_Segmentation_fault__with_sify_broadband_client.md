---
title: "Segmentation fault  with sify broadband client"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Prakash Premkumar on 2010-06-14
[SIZE=3]hi everyone,

I use ubuntu 9.10 karmix (x86).. My ISP is sify broadband..[/SIZE] [SIZE=3]
I installed their broadband client and was using it for quiet a while.
every time when i have to connect to network i have to type a command in  the terminal :

code :[/SIZE] [SIZE=3]
sudo sifyconnect

to execute the binary file which is bundled with the client the ISP  provides..[/SIZE] [SIZE=3]
but recentely it has started to behave strangely.. i get an error like  this:

code:[/SIZE] [SIZE=3]
prakash@prakash-laptop:~/ sudo sifyconnect

Checking reachability of Sify Server... : Success[/SIZE] [SIZE=3]
Checking whether instance sifyclient already running.... : NO
Establishing sify broadband connection...Segmentation fault 


pls help me.. thanks in advance[/SIZE]

---

### Post by Chesamo on 2010-06-14
A segmentation fault is a bug in the program that makes it impossible to continue. I would recommend you update to the latest version or, if you are running the latest version, roll back to a previous one.

---

### Post by Prakash Premkumar on 2010-06-14
Thank you chesamo.. for your reply..
But the same program was working well until now. In any case i 'll check with ISP

---


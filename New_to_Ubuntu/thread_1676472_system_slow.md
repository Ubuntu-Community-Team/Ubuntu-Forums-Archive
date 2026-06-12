---
title: "system slow"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-01-27
](*,)   hi,

iam using ubuntu 10.04. at morning system running fine, after  afternoon slightly getting slow and at evening getting dead slow. i have to wait 20 sec to open home folder.
For whole day i will use only firefox browser, notepad and gimp editor.



system config:
Processor=P4
RAM=512MB
Hard Disk=40GB


Kindly guid me to get system speed, you want additional information means, i will provide.......

---

### Post by coffee412 on 2011-01-27
system config:
Processor=P4
RAM=512MB
Hard Disk=40GB


Isnt the minimum requirements for Ubuntu 1GB of ram? 

Open a term window and type in "top" and let it run. Then when system starts to slow down you can see what is causing it to slow down. I would start by adding more ram to the system. To me (shooting from the hip) I would think that running low on ram its doing alot of disk swaping to virtual memory. This will slow it down.

---

### Post by Nickjpost on 2011-01-27
> **coffee412 said:**
> system config:
Processor=P4
RAM=512MB
Hard Disk=40GB
 
 
Isnt the minimum requirements for Ubuntu 1GB of ram? 

 
512MB is fine with Ubuntu. If you want, you can try to edit swappiness and see if that will improve your system performance. I agree that you should invest in more RAM, but until then, changing the swappiness value may help as it will lower the percentage of memory swapping. 
Most Linux systems are set to a value of 60, but you can check yours by
$ cat /proc/sys/vm/swappiness
 
This will return the value that your system is currently set at. *If you want*, you can change this value. Here's how:
 
Using your fav text editor, add *vm.swappiness=*(desired value) to the bottom of the file /etc/sysctl.conf
save the file and reboot, then you *may* notice improvement. I set my swappiness value to 10 and run ubuntu 10.04 with 875MB of RAM on a Toshiba Satellite L25-S1217 and noticed a good improvement.

---

### Post by pmohankumar on 2011-07-19
Thanks For your useful information.

---


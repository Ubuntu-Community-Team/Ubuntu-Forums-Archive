---
title: "system useage"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Wray on 2011-06-16
I am running a fresh, clean install  of 11.04. on a new 1 Tb disk drive
When i check system monitor it indicates that both processors are running at 80-90 % usage
As near as i can determine nothing is running.
Why would the CPU usage report be so high?
Memory usage is practically nothing ~3%

---

### Post by wildmanne39 on 2011-06-16
> **Wray said:**
> I am running a fresh, clean install  of 11.04. on a new 1 Tb disk drive
When i check system monitor it indicates that both processors are running at 80-90 % usage
As near as i can determine nothing is running.
Why would the CPU usage report be so high?
Memory usage is practically nothing ~3%
Hi, use system monitor and see what process is using your cpu, it is a program that is probably malfunctioning.

---

### Post by r-senior on 2011-06-16
If you go to the "Processes" tab in System Monitor, what does it say the top process is? You can sort by clicking on the column headings.

---

### Post by Wray on 2011-06-16
Applet.py

---

### Post by Wray on 2011-06-16
Approximately 50 process are running!
Is it safe to kill any/all of them?
how do i determine if a process is "hung"

---

### Post by wildmanne39 on 2011-06-16
> **Wray said:**
> Approximately 50 process are running!
Is it safe to kill any/all of them?
how do i determine if a process is "hung"
Hi, the only one your are looking for is the one that has a high cpu usage.

---

### Post by Wray on 2011-06-16
no processes have particularly high usage and all together do not equal anywhere near 80%
Practically all processes report poll_schedule_timeout...

---

### Post by Wray on 2011-06-16
Anybody? 
 I have tried killing processes one at a time, but all that has accomplished is hanging up the system several times requiring a forced shutdown (pull the plug) and re boot
I would really like to understand why so much CPU usage...

---

### Post by dFlyer on 2011-06-16
> **Wray said:**
> no processes have particularly high usage and all together do not equal anywhere near 80%
Practically all processes report poll_schedule_timeout...

Try running top for the command line as sudo:

sudo top

check if any processes are excessive.

---

### Post by Wray on 2011-06-16
Thanks gary but i do not completely understand sudo:

Would the command be of this form     sudo:top

as you surely know by now i am a complete and utter  noob!!! 

Briefly what does the command do?    I want to learn...

---

### Post by bkratz on 2011-06-16
While in the terminal type 

man top

for manual information

---

### Post by alphacrucis2 on 2011-06-16
> **Wray said:**
> Thanks gary but i do not completely understand sudo:

Would the command be of this form     sudo:top

as you surely know by now i am a complete and utter  noob!!! 

Briefly what does the command do?    I want to learn...

Enter the command exactly as he typed it:

```
sudo top
```

To exit from top type the letter q

---

### Post by ubudog on 2011-06-16
Hi there!

The top command is similar to the System Monitor Processes tab, though it runs in the terminal.  It shows more information.  The command in a terminal would be:

```
sudo top
```

There, you can see which process is using the most CPU, etc.  Very useful little tool.  :-)

EDIT: Already answered.  ^^ :-)

---

### Post by nzjethro on 2011-06-16
Sudo is short for "Superuser Do". Basically, it logs you in as the root user (like Adminstrative Permissions Required in Windows". Some tasks )installing programmes, running administrative tools like GParted) are not permitted for the user (i.e. you) to do, but are only permitted for the Superuser to do, hence, you type sudo <command>.

> Would the command be of this form sudo:top

In this case, you would type
```
sudo top
```
And it will ask your root password (i.e. your password) so that root can perform the task.

Or alternatively, type
```
sudo
```
to log in as root, then type you commands:
> top

Edit: Wow, we are eager to answer this question! ^^ Hope they put you on the right track.

---

### Post by Wray on 2011-06-16
i did sudo top and the culprit seems to be_** [COLOR=DarkGreen]root[/COLOR]**_ it is at 86%  Command[COLOR=DarkGreen] _**udevd**_[/COLOR]

---

### Post by ubudog on 2011-06-16
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1491332](http://ubuntuforums.org/showthread.php?t=1491332)

---

### Post by Wray on 2011-06-16
so, now what do i do?  I don't want to hose my system and have to reload it!

Thanks for all the help!

---

### Post by Wray on 2011-06-16
I see now that there a lot of roors listed with 1% or therebouts
the one with high usage is pid 396

---

### Post by Wray on 2011-06-16
Thanks ubodog the command suggested by zika on the referenced thread    	 	 	 	 	 	  **[COLOR=Green]sudo service udev sto[/COLOR][COLOR=Green]p[/COLOR]** seems to have fixed the problem, or, maybe to put it more accurately it has gotten me out of it.

 i wonder if it will re appear when i re boot?
Thanks all. Your help is much appreciated...

usage for both processors is now in single digits...

edited for typos

---

### Post by Wray on 2011-06-16
It appears i have a bug referenced by zika in

[https://bugzilla.kernel.org/show_bug.cgi?id=16052](https://bugzilla.kernel.org/show_bug.cgi?id=16052)

I am running kernel  2.6.38-8-generic-pae


The problem does re appear when i re boot.
i guess i can live with it until it gets fixed
since a bug has already been submitted

Again, thanks all

---

### Post by wildmanne39 on 2011-06-16
> **Wray said:**
> It appears i have a bug referenced by zika in

[https://bugzilla.kernel.org/show_bug.cgi?id=16052](https://bugzilla.kernel.org/show_bug.cgi?id=16052)

I am running kernel  2.6.38-8-generic-pae


The problem does re appear when i re boot.
i guess i can live with it until it gets fixed
since a bug has already been submitted

Again, thanks all
Hi, what version of ubuntu are you running? if you look all the way at the bottom of that bug page it was fixed by updating the kernel, so you might want to check into updating your kernel.

---

### Post by Wray on 2011-06-16
that may be too ambitious for me at this point given my total noob condition.  I'm running 11.04

Will not the kernel get updated at some point?

---

### Post by ubudog on 2011-06-16
Cool, glad you got it *temporarily* fixed.  You should regularly check for updates.  (System>Administration>Update Manager)

:-)

---


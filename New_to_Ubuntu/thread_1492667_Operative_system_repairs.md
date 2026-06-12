---
title: "Operative system repairs ?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Innernet on 2010-05-25
Hi.
Is there any way to scan the 10.04 installed version to determine if any files are corrupted ?
If yes, how to repair or reload those found bad without going to a fresh install and repartitioning ?

I suspect my Ubuntu got in trouble somehow, by glitches during installation.

Is there an operative system health/integrity diagnostics ?

---

### Post by Peter09 on 2010-05-25
if you do
 
```
sudo apt-get update
```
 
and
 
```
sudo apt-get upgrade
```
 
it should warn you if any existing packages are corrupt.

---

### Post by inameiname on 2010-05-25
Synaptic Package Manager under the 'custom filter' section will let you know also if you have any 'broken' packages on your system. An alternative to the terminal.

---

### Post by Peter09 on 2010-05-25
Yep - forgot about that one inameiname.

---

### Post by Drenriza on 2010-05-25
I do not believe their is any problems. If the system works as expected.

Shutsdown
Boots
Works

and all those normal things.

---

### Post by oldos2er on 2010-05-25
> **Innernet said:**
> Is there any way to scan the 10.04 installed version to determine if any files are corrupted ?


If you're talking about filesystem corruption, you can run fsck on reboot with ```
sudo touch /forcefsck
```

---

### Post by bodhi.zazen on 2010-05-25
> **Innernet said:**
> Hi.
Is there any way to scan the 10.04 installed version to determine if any files are corrupted ?
If yes, how to repair or reload those found bad without going to a fresh install and repartitioning ?

I suspect my Ubuntu got in trouble somehow, by glitches during installation.

Is there an operative system health/integrity diagnostics ?

I think it is best to start with a description of the problem you are having.

Linux is  not Windows, and corrupt files would be highly unusual, and almost always a result of a hardware problem, ie failing hard drive, or sometimes due to hitting the power button rather then shutting down the computer.

In terms of searching for corrupt or altered file systems, you typically need to start with a known good system for comparison. It is much more difficult after the fact.

You should start by looking at your logs for clues / problem. Again, it helps to familiarize yourself with the logs before you have a problem , otherwise how would you know what is "normal" ?

To reinstall an application you would use the --reinstall option

```
sudo apt-get install --reinstall foo
```

---

### Post by Innernet on 2010-05-25
Thanks for the replies.
Petr09:  Updates and upgrades performed, took about half hour. No improvement.

Drenriza: The system does **not** work as expected.  Font size changes randomly by itself, mouse pointer dissappears after loging-in, returns whenever it wants (if it gets back); and reboots randomly  :confused:

oldos2er: will try that and will report later. Am not at the compfuser site now.

Thanks

---

### Post by Innernet on 2010-05-25
Well, no success on fixing whatever is or was wrong.  Reloaded 10.04 again fresh from _another_ new copy of the LiveCD.
Seems more stable so far, and the mouse pointer has not dissappeared yet.

But... At the first booting, a black screen reported a list of errors.

Goofed, did not take notes.
Is there a log, and how to reach for it, so can be submitted here to the forum ?
Thanks.

---

### Post by Innernet on 2010-05-26
After the new 10.04 reload, later, mouse pointer dissappeared.  Crashed again, rebooting to nowhere every 10 seconds.

Removed the hard drive and placed the same brand and model hard drive with my backup 7.10 and it is smooth charming performance.

My compfuser is allergic to anything newer than 7.10 :(

---

### Post by no2498 on 2010-05-26
why not try 804  i did have 710 also

i tried 910 on this 1 and did not like it so now use 804

also have a dell 6400 put 910 on it and its ok

---


---
title: "Non Admin Account Corrupted W Firefox"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by koolkev on 2009-06-21
I have Jaunty running on a Dell Inspiron 530 using att DSL 

A non-admin user went to a website that appears to have taken over the account. 

I could not log off the account using the admin profile and password. 


There are pictures in the account that should be saved if possible so I didn't delete the account and start over. 

What should I do? Could someone direct me to a good discussion for a fix? 

I have attached two screen shoots:
1. Screenshot-9 shows multiple folders saved on the desktop and lower panel which I tried removing but appeared to make no dent in the number of folders.
2. Screenshot-8 shows the panel that appears when I tried to log off. Even entering my admin user id and password did not work so I did a hard shutdown.

---

### Post by starcraft.man on 2009-06-21
RULE 1: If you suspect a compromised PC from remote attack, pull the internet!!! I hope you did that.

I've never heard of many internet attacks on Ubuntu, I recommend after fixing this problem you go to the security section of the forums and make a report with all details so this can be fixed if this indeed was a remote exploit. Make sure you follow Rule 1 on any subsequent boot ups. 

A quick and dirty solution is simply to insert the live CD into the machine and copy the data you want to save to an external drive, USB key, burn to DVD, etc.... Once in live, you can mount any drive on the machine easily and move it off. Once data is backed up remote, I recommend a complete reinstall of Ubuntu, a compromised system can't be trusted to be secure again. Use the liveCD for a reinstall and ensure when you get to the partitioner you format the root, I'd even format the home directory since your backing all that up. That should be good enough.

---

### Post by cariboo on 2009-06-21
Why not open a terminal, and kill the open Firefox instances? In the terminal type:

```
ps ax | grep Firefox
```

You should get a lot of lines that look something like this:

```
**4589** ?        Sl     3:31 /usr/lib/firefox-3.0.11/firefox
```

to kill the instances of Firefox type:

```
sudo kill <pid> 
```

where <pid> = the program id, I have bolded it in the above example.

---

### Post by starcraft.man on 2009-06-21
> **cariboo907 said:**
> Why not open a terminal, and kill the open Firefox instances? In the terminal type:

A viable solution for the future, but he already did a hard shutdown as indicated in the description of the SS (assumed he left it off). Pursuant to that, I was aiming my solution at restoring a secure system, I assumed some malicious remote exploit and can't know for certain what it did without access or more info. Maybe my solution is overkill, I guess I'm a paranoid security buff (not pro). Seen too many compromised computers in my day.

---

### Post by koolkev on 2009-06-27
Thank you


I tried the commands below in my admin account:

kev@kev-desktop:~$ ps ax | grep Firefox
 4638 pts/0    R+     0:00 grep Firefox
 
kev@kev-desktop:~$ 4638 ?
bash: 4638: command not found

So I don't see anything to end. I have been using my account after changing my password. But the user account is acting weird. If I log on to that account the folders are still there and there is a sound as if more folders are being formed. 

Is there a way for me to kill a process (something I don't want happening when logged on) on an account that is not logged on?

---

### Post by Miljet on 2009-06-27
You did fine in identifying the process number, but the command to kill that process is:
```
sudo kill 4638
```

---

### Post by LewRockwell on 2009-06-27
you can use a live-run distro to go in and rescue the photos

you can put them on another partition on the same drive or put them on another hard drive or thumb drive or even burn them to a CD or DVD

.

---

### Post by koolkev on 2009-06-28
I still don't understand the issue of the problem being in another account. 

If I am logged on as admin and run the grep command without the bad account logged on will I be killing the process that is very nicely bring the ability to communicate with you to me right now but not have done anything to the not so nice process that is bringing irritation to the other account.

Wouldn't I be finding some log or list of programs that is associated with that account and modifying or erasing that?

---

### Post by LewRockwell on 2009-06-28
> **koolkev said:**
> I still don't understand the issue of the problem being in another account. 

If I am logged on as admin and run the grep command without the bad account logged on will I be killing the process that is very nicely bring the ability to communicate with you to me right now but not have done anything to the not so nice process that is bringing irritation to the other account.

Wouldn't I be finding some log or list of programs that is associated with that account and modifying or erasing that?

you've misunderstood several previous posts

reread for clarity


Our advice is still the same as above

liveCD in to rescue your valuables and then smash and rebuild

you'll find the PartedMagic liveCD utility disk to be quite useful
[http://www.partedmagic.com/](http://www.partedmagic.com/)

it has Firefox(so you can still chit-chat with us)
it has Erase Disk(so that you can zero-out your hard drive to get rid of any nasties hiding in the dark)
and it has Gparted(so you can partition/repartition/resize)
and it has Clonezilla(so you can do duplicates/clones/back-ups...so you don't have to start from scratch every time your OS and/or machine crashes)

enjoy!

.

---


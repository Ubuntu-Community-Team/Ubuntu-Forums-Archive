---
title: "Sudoers problem"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by ScottishGirl on 2011-03-01
Hi :)

I am the superuser on my computer - at least I was until today.  What happened was that yesterday I set up a new user account for practice, and today when I tried to update the system I got the message: 'Stephanie is not in the sudoers list.  This will be reported.'  Until today I would login to 'Stephanie' and run any commands by typing sudo[command] then the password for Stephanie.  I have been downgraded to an ordinary user.   Why am I no longer on the sudoers list?

I am running Ubuntu 10.10 

Stephanie

---

### Post by ScottishGirl on 2011-03-01
Here is what I get in the terminal:

> stephanie@Laptop:~$ sudo apt-get update
[sudo] password for stephanie: 
stephanie is not in the sudoers file.  This incident will be reported.
stephanie@Laptop:~$ su
Password: 
root@Laptop:/home/stephanie# 



You see I can access root and run commands from root.  I want to be able to restore Stephanie to superuser status though.

---

### Post by Old *ix Geek on 2011-03-01
Did your **/etc/sudoers** file get changed? Are you still included in it?

---

### Post by matt_symes on 2011-03-01
Hi

Are you still in the sudoers permissions groups ?

What is the output of (at the terminal)

```
groups <your user name>
```

where your user name is, obviously, your user name. Post back here.

Kind regards

---

### Post by jwcalla on 2011-03-01
If you type "groups" is your account included in the admin group?

---

### Post by Old *ix Geek on 2011-03-01
> **ScottishGirl said:**
> You see I can access root and run commands from root.  I want to be able to restore Stephanie to superuser status though.You're making a common mistake--you're confusing **su** and **sudo**. You ALREADY do have superuser status--that's what using **su** does, it gives the normal user root's power and privilege. It essentially makes the normal user root until they terminate the **su** session.

Using **sudo**, on the other hand, simply allows a normal user to run a command that normally needs root's authority.

It CAN be a little confusing, no two ways about that, but there is a difference!

---

### Post by sisco311 on 2011-03-01
never mind

---

### Post by ScottishGirl on 2011-03-01
This is what I get in the terminal:


```
stephanie@Laptop:~$ groups stephanie
stephanie : stephanie
stephanie@Laptop:~$ 

```

```
stephanie@Laptop:~$ id
uid=1000(stephanie) gid=1000(stephanie) groups=1000(stephanie)
stephanie@Laptop:~$ 

```

---

### Post by jwcalla on 2011-03-01
oh snap

In System -> Administration -> Users and Groups can you set your account type to Administrator?

---

### Post by matt_symes on 2011-03-01
Hi

You seem to have lost all your groups. You will have to do this from the recovery console to get root access if you don't have it. You do this from the grub menu.

```
usermod -a -G sudo stephanie
usermod -a -G admin stephanie
usermod -a -G adm stephanie
```

That would be a good start. Then you can add yourself to all the groups you have lost.

These are my groups currently. I don't need to be a member of all of them but i current am.

adm lp dialout cdrom sudo plugdev users fuse lpadmin netdev admin sambashare writefiles

Kind regards

---

### Post by sisco311 on 2011-03-01
> **ScottishGirl said:**
> This is what I get in the terminal:


```
stephanie@Laptop:~$ groups stephanie
stephanie : stephanie
stephanie@Laptop:~$ 

```

```
stephanie@Laptop:~$ id
uid=1000(stephanie) gid=1000(stephanie) groups=1000(stephanie)
stephanie@Laptop:~$ 

```

By default, only users in the admin group are allowed to use sudo. From the info you provided, my guess is that, somehow..., you managed to remove the user from the admin group. So, i think, you have to (re)add stephanie to the admin group. As root, run:
```
gpasswd -a stephanie admin
```

---

### Post by s3a on 2011-03-01
su
visudo
then under
root     ALL=(ALL) ALL
add
*username*     ALL=(ALL) ALL
then do ctrl+o and then ctrl+x.

Don't copy paste what I typed here. Copy paste the line from the terminal because my spacing might be wrong and I'm not sure if it has an effect. It probably doesn't though but just in case.

---

### Post by ScottishGirl on 2011-03-01
Yesterday I typed 'sudo passwd root' and created a root password.  Previous to that whenever I wanted to run an admin command I just entered sudo [command](Stephanie password).  I think that perhaps setting up the root password took me(Stephanie) off the sudoers list.
When I was using 10.04 I had both a root account and a superuser account:Stephanie.  I mostly used Stephanie to apt-get and dpkg etc and only used # to run multiple commands.  So should I just login to # in the terminal and run commands from there?  Ubuntu 10.10 must be different from 10.04 in this respect.

Thank you all for your help :)

Stephanie

---

### Post by sisco311 on 2011-03-01
> **matt_symes said:**
> Hi

You seem to have lost all your groups. You will have to do this from the recovery console to get root access if you don't have it. You do this from the grub menu.

```
usermod -a -G sudo stephanie
usermod -a -G admin stephanie
usermod -a -G adm stephanie
```

That would be a good start. Then you can add yourself to all the groups you have lost.

These are my groups currently. I don't need to be a member of all of them but i current am.

adm lp dialout cdrom sudo plugdev users fuse lpadmin netdev admin sambashare writefiles

Kind regards

users-admin (a.k.a *Users and Groups* from gnome-system-tools), by default, adds admin users to the [I]cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video
[/I] groups.

So, I would run:
```
usermod -aG cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video stephanie
```

---

### Post by Hedgehog1 on 2011-03-01
Hey - I have been getting all these emails that the user 'Stephanie' has been trying to use 'sudo'.

I was wondering where they were coming from!

:lolflag:


(Kidding - really).

---

### Post by matt_symes on 2011-03-01
Hi

If you can login as root do it from there.

Kind regards

---

### Post by sisco311 on 2011-03-01
> **ScottishGirl said:**
> Yesterday I typed 'sudo passwd root' and created a root password.  Previous to that whenever I wanted to run an admin command I just entered sudo [command](Stephanie password).  I think that perhaps setting up the root password took me(Stephanie) off the sudoers list.
When I was using 10.04 I had both a root account and a superuser account:Stephanie.  I mostly used Stephanie to apt-get and dpkg etc and only used # to run multiple commands.  So should I just login to # in the terminal and run commands from there?  Ubuntu 10.10 must be different from 10.04 in this respect.

Thank you all for your help :)

Stephanie

Please check out: [uhelp]community/RootSudo[/uhelp]

Until you fully understand the differences between sudo and su, I would suggest you to restore the default settings: add your user to the admin group and lock the root account password.

---

### Post by Old *ix Geek on 2011-03-01
> **ScottishGirl said:**
> Yesterday I typed 'sudo passwd root' and created a root password.  Previous to that whenever I wanted to run an admin command I just entered sudo [command](Stephanie password).  I think that perhaps setting up the root password took me(Stephanie) off the sudoers list.No. Can't happen. Not without human intervention, anyway.
> When I was using 10.04 I had both a root account and a superuser account:Stephanie.You're still misunderstanding the difference between **su** and **sudo**. On *nix systems, there is only ONE superuser account, and that's root. (Unless you assigned Stephanie the same user ID as root, which I doubt.)
> I mostly used Stephanie to apt-get and dpkg etc and only used # to run multiple commands.Yes, with **sudo**, which did NOT make you the superuser. All that did was give you temporary rights to run commands that normally require root's power.
> So should I just login to # in the terminal and run commands from there?Sure! If you're prepared to fix any IRREVOCABLE damage you do to your system while running as root. :eek: Any misplaced remove command, any badly edited config file, etc., and your system can come to a screeching halt.
> Ubuntu 10.10 must be different from 10.04 in this respect.No. It's all in the understanding of what you're actually doing.

---

### Post by matt_symes on 2011-03-01
Hi

> Until you fully understand the differences between sudo and su, I would suggest you to restore the default settings: add your user to the admin group and lock the root account password.

That's good advice. I would follow it.

Kind regards

---

### Post by ScottishGirl on 2011-03-01
Thanks Sisco311 that has worked as you can see below:

```
stephanie@Laptop:~$ groups stephanie
stephanie : stephanie admin
stephanie@Laptop:~$ 

```


Thanks also to s3a your advice also did the trick:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
stephanie ALL=(ALL)ALL
# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
                  

```


I am really pleased that I got this sorted!  :D

---


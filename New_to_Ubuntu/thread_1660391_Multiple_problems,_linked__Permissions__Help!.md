---
title: "Multiple problems, linked?  Permissions?  Help!"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by Reishtak on 2011-01-05
Hi guys.  Another cry for help from an ubuntu newbie.

I am running ubuntu 10.10 on a netbook.  Most things are going ok with configuring my system etc, and I have been trying various different software packages, as you do!

My most basic problem is that the volume indicator from the notification area in the panel has disappeared (i.e. removed by idiot user somehow).  As a result, the volume buttons on my keyboard no longer work.  Audio is fine, but I can't change the volume!

Now, not being completely new to computer problems, I have been googling, and found a possible solution to my problem.  The code that I have found which I wanted to use to see if it solved my problem was this:

```
gnome-volume-control-applet 
```

So I put the code into the terminal, with sudo before it, and I get the following error:

```
$ sudo gnome-volume-control-applet
Home directory /home/ed not ours.
Home directory /home/ed not ours.
```

So this is my second problem (hopefully the code I am trying to use will solve my first problem!)

I wonder if this problem (is it a permissions problem?) is also causing some other weird errors on my system, such as:

I have installed gimp, which I used in the past on older ubuntu installations.  However, when I run gimp I get the following error in the gimp installation log dialogue box:

```
It appears that you are using GIMP for the first time.  GIMP will now create a folder named '/home/ed/.gimp-2.6' and copy some files to it.

Creating folder '/home/ed/.gimp-2.6'...
Cannot create folder '/home/ed/.gimp-2.6': Permission denied

```

Surely this is the same problem?  I am sure it is a simple problem, but having played about with user permissions etc, I havn't solved it, and I have drawn a blank searching the forums on here and the web in general.

Anyone that has read this far deserves a medal, and if you can offer any help I will be delighted!

Ed

---

### Post by Brandon Williams on 2011-01-05
First, gnome-volume-control-applet should be run with user-level permissions (i.e. not with sudo). I think the messages are indicating this ... the program is running as root but the designated HOME directory is not owned by root.

Are you also running gimp as root? If so, then try running it without sudo. On the other hand, if you are running it as a regular user, then your directory permissions are screwed up. Run this command:```
ls -ld /home/ed /home/ed/.gimp-2.6
``` The output of this command should indicate that both directories are owned by user ed and that both directories have rwx permissions for the owner (i.e. the line will start with "drwx"). If either directory is not owned by user ed, then run ```
sudo chown -R ed:ed /home/ed /home/ed/.gimp-2.6
``` If both directories are owned by user ed but one or both of them is missing the correct permissions, then run ```
chmod u+rwx /home/ed /home/ed/.gimp-2.6
``` If you make a change with one of these commands, try running gimp again afterward before doing anything else.

---

### Post by Reishtak on 2011-01-05
Thanks for the advice - I am trying my best to get through a (just above) beginner tutorial on linux command line operations, so that I have some hope of understanding the commands and being able to help myself!

In the meantime, I tried the list command you have suggested:

```
ls -ld /home/ed /home/ed/.gimp-2.6
```but no joy:

```
ls: cannot access /home/ed/.gimp-2.6: No such file or directory
drwxr-xr-x 41 1016 1016 4096 2010-04-02 17:46 /home/ed

```I am so confused with all this... can't wait until I understand it!!!

Thanks again for the help (so far! :D)

Ed

---

### Post by SuaSwe on 2011-01-05
Correct me if I'm wrong, but won't "chmod u+rwx /home/ed /home/ed/.gimp-2.6" give full read/write/execute access to all of /home/ed? Not everything in the /home dir should have the same level of privileges.

I could be wrong though - not sure what that u beforehand does, for example! :)

---

### Post by SuaSwe on 2011-01-05
> **Reishtak said:**
> 
```
ls: cannot access /home/ed/.gimp-2.6: No such file or directory
drwxr-xr-x 41 1016 1016 4096 2010-04-02 17:46 /home/ed

```

So basically, your home directory is owned by "1016". :D Maybe a typo has caused this along the way?

As per above, the following should sort that, in theory:

```

sudo chown -R ed:ed /home/ed

```

If it will allow you to run it, that is. :)

---

### Post by Reishtak on 2011-01-05
... I think you jinxed it hrhr

```
chown: cannot access `/home/ed/.gvfs': Permission denied

```I am really grateful for your help, but still have little understanding of what is going on.... hopefully I'll get there in the end, but for now:

any ideas? lol

Edit:

Have been going through some of the options on the ls command in the tutorial I'm going through.  Thought I would do ls -l on my home directory.

All the files and folders in the home directory are listed as owned by ed and there is no mention anywhere of the 1016 thing that turned up before.

Also, just did the ls -l on my / directory

All the files and folders in the / directory are owned by "root" and in group "root"

Not sure if this is useful or unnecessary info!?

---

### Post by SuaSwe on 2011-01-05
Yep, that looks to be quite messed up! :D

Do you have sudo (administrative) rights on the box? What happens if you do,

```

sudo -i

```

... then input your regular user password?

---

### Post by SuaSwe on 2011-01-05
Also, can you run:

```

cd /home/ed/
chmod 777 .gvfs

```

?

---

### Post by Reishtak on 2011-01-05
> **SuaSwe said:**
> Yep, that looks to be quite messed up! :grin:

Do you have sudo (administrative) rights on the box? What happens if you do,

```

sudo -i

```... then input your regular user password?

When I type that command in, I get:

```
root@ed-Inspiron-1018:~# 
```

with a cursor at the end (no password input requested etc)

Also, if I run

```
cd /home/ed/
chmod 777 .gvfs
```

it just goes back to the cursor with no change (even when trying the other commands above).

If i type:

```
sudo chmod 777 .gvfs
```

i get 

```
chmod: cannot access `.gvfs': Permission denied
```

I am confused as to what I must have done to get the system this screwed up?

I havn't been doing much fiddling (none with terminal at all really, except to install some software etc) so not sure if it could have happened during some software installation?

I am loathed to wipe my ubuntu and set it up all again, at least before I understand why this problem has occurred and how to avoid it happening again - because it may do just that when I try to set up my system as it is now!

:S

---

### Post by blind2314 on 2011-01-05
> **SuaSwe said:**
> So basically, your home directory is owned by "1016". :D Maybe a typo has caused this along the way?
 
As per above, the following should sort that, in theory:
 
```

sudo chown -R ed:ed /home/ed

```
 
If it will allow you to run it, that is. :)
 
 
This actually means that Ubuntu can't resolve who the directory is owned by, usually by consulting /etc/passwd..instead, it just knows that the UID is 1016.
 
Does ```
sudo cat /etc/passwd | grep 1016
``` return anything? What this does, if you don't know, is display the contents of your passwd file, where ubuntu stores some user information, and searches for that UID (user ID).
 
Forgot one thing. You shouldn't need to chmod things as root in your home directory..because..well, everything that's in there should be owned by you or at the very minimum the group your ID is in. Also, an ```
ls -l
``` of / returning root:root for everything isn't what I would call out of the ordinary either..that is the root of your filesystem, and most of the time the things there should or end up being owned by root.

---

### Post by Reishtak on 2011-01-05
No joy...

```
sudo cat /etc/passwd | grep 1016
```

just dumps me back to the friendly looking but frustrating $ cursor


Glad that the ls -l was normal, really I assumed it was, but just posted it there as I had at last stumbled across something semi-relevant in the learning process.

still don't understand why I lack these permissions...?

---

### Post by blind2314 on 2011-01-05
That's actually helpful, it looks like it just "dumped you back there", but it actually gave you an answer. That proves that the UID 1016 isn't located anywhere on your system, which could be one of the reasons you're having so many permissions problems.
 
Which folders were "owned" by that ID again?
 
Also, unless I misunderstood your response and you already know this, whenever you grep for something and you get nothing back, that means it wasn't found. It doesn't mean that nothing happened at all, or that an error occurred.

---

### Post by Reishtak on 2011-01-05
> **blind2314 said:**
> That's actually helpful, it looks like it just "dumped you back there", but it actually gave you an answer. That proves that the UID 1016 isn't located anywhere on your system, which could be one of the reasons you're having so many permissions problems.
 
Which folders were "owned" by that ID again?

I'm not 100% sure - looking at the replies in this thread, it seemed that my home directory was owned by 1016.  However, another reply suggested that 1016 was an ID assigned by ubuntu as it didn't know the owner!

Again, confused!  Surely if 1016 was just a flag meaning that the owner was unknown, then it would be normal that 1016 wouldn't be found?

> **blind2314 said:**
> Also, unless I misunderstood your response and you already know this,  whenever you grep for something and you get nothing back, that means it  wasn't found. It doesn't mean that nothing happened at all, or that an  error occurred.

No you understand my poor understanding well!  I wasn't sure, but it is good to know that.  I had guessed that unless an error message came, then something had happened (wasn't sure that it meant that there were no results).

Cheers... :)

---

### Post by blind2314 on 2011-01-05
> **Reishtak said:**
> I'm not 100% sure - looking at the replies in this thread, it seemed that my home directory was owned by 1016. However, another reply suggested that 1016 was an ID assigned by ubuntu as it didn't know the owner!
 
Again, confused! Surely if 1016 was just a flag meaning that the owner was unknown, then it would be normal that 1016 wouldn't be found?
 
 
 
No you understand my poor understanding well! I wasn't sure, but it is good to know that. I had guessed that unless an error message came, then something had happened (wasn't sure that it meant that there were no results).
 
Cheers... :)
 
I was the one who suggested that the owner was unknown, because that's what it seemed. Also, 1016 isn't a "flag", it's the ID of the owner/group, it just shows as a number because the OS can't resolve it to a name.
 
Also, someone can correct me if I'm wrong, but .gvfs is a virtual file system of sorts used by Gnome..there's not really any reason to be monkeying with permissions on that directory (that's not meant as an insult to you, not getting down on you). The reason that your previous ```
ls -ld
``` on the gimp directory failed is that gimp never actually got far enough to create that directory. It's not there, hence, ls can't find it. Try to rerun the gimp installation as yourself, not root (don't use sudo).

---

### Post by Reishtak on 2011-01-05
I will try installing gimp again, but the thing is, that I installed it through the ubuntu software centre, so didn't have any option over how it was installed (sudo or not).

I expect, therefore, that it will install it again in the same way.  Maybe if I have the same problem after reinstalling, I should try to install it from the terminal?

This is so weird.  I would have thought that other people must have had similar problems?

:confused:

---

### Post by blind2314 on 2011-01-05
Oh. I either missed that when you said it before, or I'm just stupid. 
 
If you already installed through Software Center then you shouldn't be having the problems you're having now. Nonetheless, try it again, and report back.

---

### Post by Brandon Williams on 2011-01-05
Did you ever run the suggested chown command? ```
sudo chown ed:ed /home/ed
``` Since /home/ed is (or was) only writable by non-existent user 1016, you would not be able to write to your home directory. This would in turn prevent gimp from creating the /home/ed/.gimp-2.6 directory. If you change the ownership of /home/ed/ back to user ed with chown, then gimp should be able to create the directory it wants to create.

Also, since you indicated that everything _in_ /home/ed is owned by user ed, there should be no need to use the -R flag with chown (it tells chown to change ownership on everything in the whole directory tree). However, if running the command without -R doesn't seem to solve your problem, then try it with -R, as in ```
sudo chown -R ed:ed /home/ed
```

---

### Post by Reishtak on 2011-01-06
Thanks for all the help guys.  I am sure we would have got this sorted with some more prodding about, but my laptop decided to screw up big time (windows side).  As a result I took the opportunity to delete the whole windows partition and reinstall ubuntu on the whole disk.

Hopefully I wont need to restart this thread with the same problem (I am going to install the same software, so maybe.... heh)

Anyway, cheers again guys!
Ed

---


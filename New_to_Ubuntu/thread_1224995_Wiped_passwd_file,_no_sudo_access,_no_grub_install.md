---
title: "Wiped passwd file, no sudo access, no grub installed .. what do I do?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by mkormendy on 2009-07-28
:confused:
For some reason when I went to add another user to the passwd file, it ended up wiping my passwd file altogether. Now it is blank and I have lost all of my users for root, sudo, and my server apps and various other programs that required access to certain things (I think, unless they do it differently).

I can't sudo into anything .. and my system won't boot up any more.

I don't have GRUB installed on my system, or at least I cannot seem to boot into GRUB either by pressing escape at any point in time when my system is trying to boot up.

When I try to use the Install CD to go into recovery mode and try to access my initial filesystem .. it says it cant access it .. 

What the hell do I do? What are the right steps to troubleshooting and repairing my passwd file and gaining access to my system again????

---

### Post by mapes12 on 2009-07-28
I'm making a couple of assumptions.

1. You only have Ubu on your machine i.e. no other OS
2. You are just stating out with Ubu and have no critical data on your machine.

If the above is correct then I would simply boot from the installation CD and run a fresh install.

If 1 & 2 are not correct then post back with info about your configuration to see what else we can suggest.

Mark

---

### Post by nothingspecial on 2009-07-28
> **mkormendy said:**
> 

When I try to use the Install CD to go into recovery mode and try to access my initial filesystem .. it says it cant access it .. 



You can try booting from the live cd and typing

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
```

Can you access anything from /ubuntu?

If so you will be able to copy any critical data to some sort of removeable media.

---

### Post by shepherdzw on 2009-07-28
:-)

Did you have any backups ? Man is this true coz your story is not even close to being logical. 

Anyway for record's sake the easiest way out of your small mess is to run a DATA recovery and recover the last good known passwd file.

Next time backup your important files and document your procedures :-)

---

### Post by shepherdzw on 2009-07-28
:-)

Did you have any backups ? Man is this true coz your story is not even close to being logical. 

Anyway for record's sake the easiest way out of your small mess is to run a DATA recovery and recover the last good known passwd file.

Next time backup your important files and document your procedures :-)

---

### Post by mkormendy on 2009-07-28
First off, to all:

1. thanks for your replies, I really appreciate the support community (aka you!)
2. i just remembered that have an ISO backup of my entire system from not too long ago on another drive.

Second off, to individual replies:

Hey Mark,
Yes assumption #1 is correct. Assumption #2 is incorrect, over the course of the past three months I have installed specific apps, and also compiled some programs and drivers specific to setup and there's been a number of changes system wide that I would really not like to re-do - I've spent a lot of time working on this machine to get it just the way it is.
I have two drives one is my system drive and the other is just a volume drive for files, each have some partitions, and the volume drive contains the backup.

Hey "nothingspecial",
I will try that, but I think what I am going to try and do is extract my entire backup to my other drive under a directory and copy over the passwd file onto the main system.

Hey "shepherdzw",
Yes, I have backups dude, I ain't completely new!
And yes man, this is true. Logical or not, it happened nonetheless and now I am in this predicament.

Lastly in this reply,

Will I have problems trying to copy a file (passwd file in particular) from my ISO extraction back to my system drive with the Live CD?
I do not have any sort of encryption on the filesystems themselves (I THINK!) but if I did, would it cause a problem, and if I didn't would it cause a problem.
Either way, would it cause a problem, and what is the best way to go about this?

Thanks,
// mike

> Yes, I know exactly what I was doing with Linux, but I am disappointed with the results ... 

---

### Post by aesis05401 on 2009-07-28
Hello, 

I am still somewhat new to Ubuntu, but I think the most important file is the shadow file.  Group & passwd files can be recreated very easily if I understand correctly. 

Try this:
1. Boot live cd
2. Mount drive
3. Create passwd file in /etc folder
4. ```
echo "root:x:0:0:root:/root:/bin/bash" >  /etc/passwd
```
5. reboot

I do not know too much about Ubuntu boot sequence, but on some other distros this will get you booted off local drive into root acct.  I do not know for sure, but you should be able to add any other user names you remember with 'x' in the password position to indicate use shadow file for passwords.

Looking now at my Ubunut passwd file I see similar entries for bin, sys, etc... so you may want to look at Ubuntu wiki for list of default system logins that your passwd file needs.

Does this help or can someone correct my advice?

---

### Post by mkormendy on 2009-07-30
All fixed, thankfully my backup had a recent enough passwd file that I just copied over to the empty one on my main ubuntu filesystem.

Thanks for all of your help.

(someone please mark this as resolved)

---

### Post by Zill on 2009-07-30
mkormendy:  Sounds like this is related to [bug #240437]("https://bugs.launchpad.net/ubuntu/+source/liboobs/+bug/240437").

Glad you found a backup and got it working again. :-)

ps.  You will have to mark the thread as "Solved" yourself - only the OP can do this.  Just click the "Edit" button below your first post and then click the "Go Advanced" button in the editor.  Then just add "Solved" to the title and save.

---


---
title: "what have i done by entering 'sudo chown -R $USER: /' ?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-01-21
Ok, i think this could be serious - i just entered 

sudo chown -R $USER: /

i meant to type in a location, but hit enter by mistake - then a list of permissions being changed appeared.

I exited pretty fast, but it's done something - what?

---

### Post by theozzlives on 2009-01-21
having $USER owner of all the files could be a problem.

---

### Post by lykwydchykyn on 2009-01-21
Is there a chance you can scroll back up the terminal window and copy the list of files it changed?

---

### Post by phantomjoker on 2009-01-21
no - i exited the terminal

---

### Post by phantomjoker on 2009-01-21
can someone tell me what the command actually does? i dont even know - just following instructions from another post?

---

### Post by snova on 2009-01-21
You've transferred ownership of every file in your system to yourself. Most people who do this don't even have a functioning system at the end...

But, because this is chown and not chmod, there may well be a way to fix it this time! :D

```
chown root: / -R
```

This will also mess up your home directory, however, so following:

```
sudo chown $USER: /home/$USER -R
```

It might not work, but we can always try.

---

### Post by taurus on 2009-01-21
You change the ownership of all files starting from the root filesystem, /, to $USER.  Some system files need to be owned by root or bin for them to function properly.  This is just as bad as the other command that has the r and the m in it.

---

### Post by phantomjoker on 2009-01-21
but i closed the terminal after like 2 seconds so i canceled the command right? tell me it canceled the command!

---

### Post by Michael.Godawski on 2009-01-21
> **taurus said:**
> This is just as bad as the other command that has the r and the m in it.

Nicely put. I remember the times when I delete my whole system with this command. Was fun to watch aaaalllll the files being deleted in real time in the terminal... I gladly remember the early times...

phantomjoker I guess we had all some sort of disaster on our linux machines... don't give up, it makes you stronger; and perhaps you can fix it.

A good way to cancel a command is Ctrl + C.

Please post - if you are still able to use the terminal - the output of:

```
ls -l
```
```
ls -l /
```

---

### Post by phantomjoker on 2009-01-21
but im still using the machine so its ok... right?!

---

### Post by taurus on 2009-01-21
> **phantomjoker said:**
> but i closed the terminal after like 2 seconds so i canceled the command right? tell me it canceled the command!

Yes, you did cancel the command _but_ 2 seconds too late.  Some files have already changed so now you need to go in and see which ones.

---

### Post by Michael.Godawski on 2009-01-21
> **phantomjoker said:**
> but im still using the machine so its ok... right?!
It is a good sign :)
check the permissions with the commands posted above.

---

### Post by lykwydchykyn on 2009-01-21
> **phantomjoker said:**
> but i closed the terminal after like 2 seconds so i canceled the command right? tell me it canceled the command!

It would have canceled the command, but whatever files it got to are changed.  I would suspect it would start with /bin, so you might want to check the files in /bin (all of which should be owned by root).

DO NOT do what was suggested about and change all files ownership to root.  You'll be unable to log in as yourself, and since there's no way to directly log in as root on Ubuntu, you'll be locked out of the system.

Just go through the top level directories in alphabetical order and change ownership back to root, until you stop seeing files being owned by your user.

everything under /bin and /boot should be owned by root. /dev is automatically repopulated at boot time, so it's ok.  I doubt it got further than that in 2 seconds.

---

### Post by lykwydchykyn on 2009-01-21
> **snova said:**
> You've transferred ownership of every file in your system to yourself. Most people who do this don't even have a functioning system at the end...

But, because this is chown and not chmod, there may well be a way to fix it this time! :D

```
chown root: / -R
```

This will also mess up your home directory, however, so following:

```
sudo chown $USER: /home/$USER -R
```

It might not work, but we can always try.

For emphasis, I quote and repeat:  DO NOT DO THIS.

no offense, snova, but that will cause more problems than it will fix.

---

### Post by phantomjoker on 2009-01-21
THANKYOU LYKWYDCHYKYN! Someones talking sense to me! (by the way - your name is way to complicated to type more than once - so i will refure to you as lyk in the future)

Ok, i can tell you that i read the words 'graphics' - so i think it changed the graphics permissions - maybe

---

### Post by phantomjoker on 2009-01-21
ok, i have followed lyks instructions by looking in bin - and all executables are permissioned to me... you said they should not be - but then i only saw about 6 differant files appear being changed - so could it be that they're meant to be to me (the say permission - mckenzie (that being me).

---

### Post by donkyhotay on 2009-01-21
The system may run, but changing the file permissions like that is pretty bad. It takes out a good chunk of your security by giving the user the ability to make changes he should have to do. As mentioned before try to go through the files and change them back. Theoretically though if you were to let the command run to the end then your computer would have the security and stability of windows.

---

### Post by drs305 on 2009-01-21
I posted this on the original thread but here is a command to see which main folders were changed to yourself:
```

sudo find / -maxdepth 2 -user 1000 | grep -v "proc"

```

---

### Post by phantomjoker on 2009-01-21
got the message

> sudo: must be setuid root

---

### Post by lykwydchykyn on 2009-01-21
> **phantomjoker said:**
> ok, i have followed lyks instructions by looking in bin - and all executables are permissioned to me... you said they should not be - but then i only saw about 6 differant files appear being changed - so could it be that they're meant to be to me (the say permission - mckenzie (that being me).

Nothing under /bin should be owned by you.  Nothing.  It should all belong to root.  Same with /boot.

Apart from your home directory and some files in tmp, it's unlikely that anything should be owned by you.

/var has files owned by a variety of system users (not root nor you either), and I'm not entirely sure about /usr (though I think it should all be owned by root; certainly none of it owned by you).

---

### Post by lykwydchykyn on 2009-01-21
> **phantomjoker said:**
> got the message

Erm... that's bad.  You are probably going to have to fix this from the liveCD, or recovery mode.

---

### Post by phantomjoker on 2009-01-21
[IMG]http://i44.tinypic.com/2chs11e.png[/IMG]

---

### Post by phantomjoker on 2009-01-21
hey hey - its ok folks, im a moment of genious i have backed up this entire partition on another partition, so in therory i can wack it back up asap! 

But for now... this is very serious! that will be my last resort

---

### Post by lykwydchykyn on 2009-01-21
Do you have a liveCD handy?

---

### Post by phantomjoker on 2009-01-21
yes i do have a live CD, but although i am very determined to get this sorted out as much as possible - i do also register its 10pm here and i have exams in the morning 

(everyone just got uninterested as they realised this is only a student typing away)

But seriously - i can tell this may take quite a bit of work - as im used to with ubuntu, so can i recommend if anyone has any long winded suggestions - _PLEASE_ post them - as anything can help, but i may not carry them out right now - as i will have to exit this place soon'ish!

---

### Post by phantomjoker on 2009-01-21
oh, and what are peoples thought on the screen shot? look bad?

i have no idea...

---

### Post by jakupl on 2009-01-21
Well lyk said:

> **lykwydchykyn said:**
> Nothing under /bin should be owned by you.  Nothing.  It should all belong to root.  Same with /boot.


So you do have some tidying up to do.

---

### Post by lykwydchykyn on 2009-01-21
Ok.
 -boot to the liveCD
 -mount the / partition
 -change ownership of /bin /boot /usr and /lib to root, recursively. Assuming your / partition is sda1 and mounted to /media/sda1, you can do this in nautilus or at the command line with:
```

cd /media/sda1
sudo chown -R root:root bin boot usr lib

```
 - reboot, and hopefully things are happy.

The "find" command specified earlier will help locate improperly permissioned files as well, though you can ignore anything in tmp or your home directory.

I know some of that is not specific, but it's hard to give exact commands without knowing more about your system.

---

### Post by Bölvaður on 2009-01-21
> **lykwydchykyn said:**
> 
 -boot to the liveCD

I dont really think you need to use the livecd for this. as you still seem to be able to use the computer now and the command doesnt break anything even though you are on it.

---

### Post by drs305 on 2009-01-21
The OP is actually running 2 threads. On the other he stated he can't run sudo. Thus the need to use the LiveCD.

I'd recommend all further posts on this subject be made here, since the other deals with the original problem, which, as sometimes happens, is minor compared to this.  :(

---

### Post by snova on 2009-01-21
> **lykwydchykyn said:**
> For emphasis, I quote and repeat:  DO NOT DO THIS.

no offense, snova, but that will cause more problems than it will fix.

Thank you for pointing that out, though I do not quite understand why...

Given the size of /lib, and the time it takes merely to find all the files within it, two seconds is probably not long enough to get past this (assuming alphabetical order, which it appears to do). However, /etc comes before that, so I suggest also making sure to get this directory.

Or, better yet, check...

```
cd /media/<mountpoint>
ls -l
```

---

### Post by phantomjoker on 2009-01-21
Well i can tell you anything you need to know - if it will help.

Also - i found these commands in another post - 

> ls -l usr/bin/sudo
chwon root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

apparently they get sudo back - sound like what i need?

---

### Post by lykwydchykyn on 2009-01-21
> **snova said:**
> Thank you for pointing that out, though I do not quite understand why...


 - Your command would make all home directories owned by root
 - If you can't write to your home directory (which you couldn't if root owned all files), you cannot log in.  Try it: create a user, change the ownership of the home directory (recursively) to root, and try to log in as that user.
 - Since you cannot log in as root directly on Ubuntu, there is no way to log in and change ownership back.  Unless you boot to liveCD or recovery console.

I could be wrong, but off the cuff I'm fairly certain that's the case.  Also, there are a variety of permissions under /var and a lot of services would get broken if they were messed with.

@phantomjoker:  double check those commands.  There is no "s" command that I'm aware of.  If root doesn't own sudo, it won't work and you pretty much can't do anything to fix this unless it does.

---

### Post by snova on 2009-01-21
No, I don't think that will work.

If you chown and then chmod, the second command will fail (it's no longer your file), and you'll be stuck with half a sudo.

If you chmod and then chown, the sticky bit (which is what makes sudo work) will be lost, and you'll again have half a sudo. :P

If you're still on your system, post

```
ls -l /
```

And then we'll be sure of what files need to be fixed, and which don't.

That, and /usr is so large, and close to the end of the alphabet, sudo may not have been affected. Check and post:

```
ls -l /usr/bin/sudo
```

---

### Post by phantomjoker on 2009-01-21
Very fair point Drs305.

I thought i mentioned the lack of sudo function above - did i not?

---

### Post by stchman on 2009-01-21
Could the user just enter the following:

```

sudo chown -R root:root /

```

This should transfer all files on the system to root.

Then do this to get his home directory under his control:

```
sudo chown -R $USER:$USER /home/$USER
```

I think this could work.

---

### Post by phantomjoker on 2009-01-21
> ls -l /
total 80
drwxr-xr-x   2 mckenzie mckenzie  4096 2008-12-28 12:21 bin
drwxr-xr-x   3 mckenzie mckenzie  4096 2008-12-28 12:27 boot
lrwxrwxrwx   1 mckenzie mckenzie    11 2008-12-28 12:01 cdrom -> media/cdrom
drwxr-xr-x  15 mckenzie mckenzie 14000 2009-01-21 20:53 dev
drwxr-xr-x 136 mckenzie mckenzie 12288 2009-01-21 21:03 etc
drwxr-xr-x   4 mckenzie mckenzie  4096 2008-10-20 13:27 home
lrwxrwxrwx   1 mckenzie mckenzie    32 2008-12-28 12:26 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 mckenzie mckenzie    32 2008-12-28 12:08 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 mckenzie mckenzie  4096 2009-01-06 17:13 lib
drwx------   2 mckenzie mckenzie 16384 2008-12-28 12:01 lost+found
drwxr-xr-x   5 mckenzie mckenzie  4096 2009-01-21 21:03 media
drwxr-xr-x   2 mckenzie mckenzie  4096 2008-10-20 13:27 mnt
drwxr-xr-x   2 mckenzie mckenzie  4096 2008-10-29 22:53 opt
dr-xr-xr-x 145 mckenzie mckenzie     0 2009-01-21 20:53 proc
drwxr-xr-x  15 mckenzie mckenzie  4096 2009-01-21 20:21 root
drwxr-xr-x   2 mckenzie mckenzie  4096 2008-12-28 12:21 sbin
drwxr-xr-x   2 mckenzie mckenzie  4096 2008-10-29 22:53 srv
drwxr-xr-x  12 mckenzie mckenzie     0 2009-01-21 20:53 sys
drwxrwxrwt  17 mckenzie mckenzie  4096 2009-01-21 21:50 tmp
drwxr-xr-x  12 mckenzie mckenzie  4096 2008-12-29 17:57 usr
drwxr-xr-x  15 mckenzie mckenzie  4096 2008-10-29 23:12 var
lrwxrwxrwx   1 mckenzie mckenzie    29 2008-12-28 12:26 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 mckenzie mckenzie    29 2008-12-28 12:08 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic


and

> ls -l /usr/bin/sudo
-rwxr-xr-x 1 mckenzie mckenzie 115136 2008-09-01 14:17 /usr/bin/sudo
mckenzie@mckenzie-home:~$ 



---

### Post by lykwydchykyn on 2009-01-21
Oh... that looks bad.  Maybe it only got the top level directories?  Add /etc, /sbin, /root, /opt, /srv, /mnt, and /media to the list I gave you above.

/sys /proc and /dev should sort themselves out on reboot, you shouldn't have to mess with them.

---

### Post by phantomjoker on 2009-01-21
oh i see...

---

### Post by shecky on 2009-01-21
You can try reinstalling base files, which will reset their original permissions.
```
sudo apt-get --reinstall install ubuntu-standard
```

The ubuntu-standard package might restore a big chunk of /bin.

You can also use:
```
dpkg -S *filename*
```
to find out what package owns a specific file that has a frigged up owner permission, then just reinstall it.

---

### Post by lykwydchykyn on 2009-01-21
It looks bad because so far I'm seeing just about everything is owned by you.

When I said to add those directories to the list, I meant the list I gave you above of directories to chown from the liveCD.

Guys, nothing is going to work here until sudo is fixed. As far as I can see, that can only be done from the liveCD. 

The only tricky permissions really are /var.  Everything else should be fairly straightforward, unless you've installed something special.

---

### Post by snova on 2009-01-21
The fact that it went deep.

lykwydchykyn was probably hoping that it didn't recurse very far down the directory tree, but it looks like it did a very thorough job.

What about **/usr** and **/var**? Those are the biggest trees, after all, we can hope they weren't affected... at least not entirely.

```
ls -l /usr /var
```

---

### Post by snova on 2009-01-21
> **shecky said:**
> You can try reinstalling base files, which will reset their original permissions.
```
sudo apt-get --reinstall install ubuntu-standard
```

The ubuntu-standard package might restore a big chunk of /bin.

You can also use:
```
dpkg -S *filename*
```
to find out what package owns a specific file that has a frigged up owner permission, then just reinstall it.

Interesting... but I don't think we have sudo!

---

### Post by phantomjoker on 2009-01-21
in reply to snova -

every single god dam file Mckenzie Mckenzie!

ARGH! i thought this would be like a 'oh just do this' - kind of mistake - looks like i have instead rewritten the history books with the biggest c***up besides a command involving r or m!

---

### Post by phantomjoker on 2009-01-21
somehow i think exiting the terminal did _nothing_

my root was on a mission - and i couldnt stop it!

---

### Post by albinootje on 2009-01-21
> **phantomjoker said:**
>  ARGH! i thought this would be like a 'oh just do this' - kind of mistake - looks like i have instead rewritten the history books with the biggest c***up besides a command involving r or m!

The best *and* easiest thing to do is back up your /home data, and reinstall.

Because the problem of :
```

chown -R root /

```
is that files with setuid and/or setgid flags will lose those.
And that means trouble with several important applications like e.g. sudo.

Make sure you back up your /home properly, which means :
1) on a Linux file system like ext2 or ext3 on an usb disk, or on DVDs or cdroms
2) or in case of FAT32 (remember about the 4 Gb file size limit of FAT32) or NTFS, use archiving like tar or zip to prevent messed up permissions of your files and directories.

---

### Post by phantomjoker on 2009-01-21
i have a backup already of my home partition - thank GOD!

i did a data dump using another partition - that i was assured would work - would i be right?

---

### Post by drs305 on 2009-01-21
Given the depth of the changes it would seem that a restoration would be in order and could be accomplished much quicker than the time it took to generate these responses. 

I'm not who will determine that of course - that's up to phantomjoker. At least there has been a good discussion and valuable lessons about troubleshooting.

---

### Post by shecky on 2009-01-21
> **snova said:**
> Interesting... but I don't think we have sudo!
Ahhh, then recovery console would be in order.

Taking the idea a step further, you can get a full list of packages to reinstall with this command:
```
for i in $(find / -user 1000 | grep -v "proc\|home"); do dpkg -S `basename $i`|cut -d":" -f1; done|cut -d"," -f1|sort|uniq >~/filelist.txt
```

Then go make a sandwich, because it might take a while. Personally, I'd go for a fresh install. ;)

---

### Post by phantomjoker on 2009-01-21
dude - i need sudo for that command - i dont have sudo...

i just get permission denied

---

### Post by phantomjoker on 2009-01-21
anyway - its 11.30pm n im going to bed

cheers for all your help - all of you! 

i will pick up were i left off tomorrow - with a reply of my plan of action. Until then - my computer has to stay on!

---

### Post by shecky on 2009-01-21
> **phantomjoker said:**
> dude - i need sudo for that command - i dont have sudo...

i just get permission denied

Reboot into single user mode, you'll be root. No sudo needed.

---

### Post by phantomjoker on 2009-01-21
um, when i boot - it automatically loads into mckenzie - i don't know how to change that - and also - i think if i reboot, the system won't work when it turns on so...

---

### Post by albinootje on 2009-01-21
> **phantomjoker said:**
> dude - i need sudo for that command - i dont have sudo...

i just get permission denied

You really should go for the reinstall.
Fixing the permissions on your files after your "chmod -R $USER /" is a bit difficult to say the least.

If you really want to try, then fix sudo first as following :
1) boot in the recovery mode, choose "drop to root shell prompt"
2) do :
```

chmod 4755 /usr/bin/sudo*
telinit 2

```

---

### Post by albinootje on 2009-01-21
Hit <escape> when a short message about Grub boot menu is available.
After that choose "recovery mode". etc.

---

### Post by niteshifter on 2009-01-21
Hi,

A couple of folks have mentioned using the find command with the -user switch. As in:

```
sudo find / -maxdepth 2 -user 1000 | grep -v "proc"
```
or
```

for i in $(find / -user 1000 | grep -v "proc\|home"); do dpkg -S `basename $i`|cut -d":" -f1; done|cut -d"," -f1|sort|uniq >~/filelist.txt
```

There's potential for complicating things here: What if they aren't the first user assigned post install?

Check the id first!
```
id -u username
```
and use the number that the above returns as the argument with -user. Assuming it to be 1000 is risky.

---

### Post by drs305 on 2009-01-21
> **niteshifter said:**
> Hi,

A couple of folks have mentioned using the find command with the -user switch. As in:

```
sudo find / -maxdepth 2 -user 1000 | grep -v "proc"
```
or
```

for i in $(find / -user 1000 | grep -v "proc\|home"); do dpkg -S `basename $i`|cut -d":" -f1; done|cut -d"," -f1|sort|uniq >~/filelist.txt
```

There's potential for complicating things here: What if they aren't the first user assigned post install?

Check the id first!
```
id -u username
```
and use the number that the above returns as the argument with -user. Assuming it to be 1000 is risky.

It was discussed in another post or PM, but point made. The command can also be run with the *username* instead of uid.

---

### Post by S0m3th1ngw13rd on 2009-01-21
> **drs305 said:**
> I'm not who will determine that of course - that's up to phantomjoker. At least there has been a good discussion and valuable lessons about troubleshooting.

Not only troubleshooting, but also the power of the -r and -m parameters. Being new to Linux myself, I did not realize this until now.

---

### Post by crjackson on 2009-01-21
> **phantomjoker said:**
> um, when i boot - it automatically loads into mckenzie - i don't know how to change that - and also - i think if i reboot, the system won't work when it turns on so...

I feel your pain man! I pretty much did the same thing a long time ago. It can be fixed a piece at a time, but it's really not worth it, except for the learning.

You really should listen to some of the guys that directed you to re-install.

Easy way... Boot into recovery mode, find your home directory, make a FRESH backup of your precious files, emails, etc...

Do a clean install, get updates, copy the backed up files back to the home folder.

Done, call it a day.  I would guess 45 mins. tops...

---

### Post by phantomjoker on 2009-01-23
ok guys - thanks for all you help, and those of you just wishing me luck. I have defenatly learnt my lesson in bad commands and as Michael.G said - i have grown stronger!

Well eventually i restored my computer using a dd file i had on another hdd (thank god) and so i am back on and working - feels nice to have sudo back - missed that guy!

Anyway, sorry i didnt try many of your suggestions, but i thought i could do more damage than good, so just restored. 

Thanks again guys and girls! (oh - and i wasn't too tired for my exams [reference to message #25])

---


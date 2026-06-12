---
title: "Admin privileges"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Gotaro on 2009-01-28
I'm very tired of typing in my password to 'sudo'.  I heard it's taboo to run as root, so could I give myself admin privileges or something?  Or just run as root?  Lol.  My main concerns are the password screens for EVERY dang thing I want to do, and my designated "Storage" drive not mounting (or whatever) until I open Dolphin and try to open it, and.. surprise! I need my password to sudo it..  The list really does go on..

--Edit--
What I really want is to not be required to have admin privileges to do anything (in contrast to just not needing a password to sudo or having privileges to sudo without typing root's password).  For clarification, an example: I have a background stored on the "Storage" partition, that for some reason requires me to sudo to open/mount.  When I start Kubuntu, I want the background to show up without me having to manually sudo the drive and refresh the background.

---

### Post by emarkd on 2009-01-28
Well, here it is if you really want it.  In your terminal session, run

```

sudo su

```

You'll become root in that shell.  This is really bad practice though because Linux will happily let you screw up terribly and won't even warn you that bad things are about to happen, so I don't recommend it.

What all are you doing that requires root access anyway?  I almost never have to type my password.

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> My main concerns are the password screens for EVERY dang thing I want to do, and my designated "Storage" drive not mounting (or whatever) until I open Dolphin and try to open it, and.. surprise! I need my password to sudo it..  The list really does go on..I have been using Linux as my primary OS for 8 years, and almost NEVER need administrative privileges except for installing/removing software and the very occasional administrative task.  I can't imagine what it is you're doing on a regular basis that would require administrative privileges for "EVERY dang thing."  If you've set up your "Storage" drive in /etc/fstab properly, you should be able to access it as a regular user.  If it is an external "USB" or "Firewire" drive, it should mount with regular user privileges when you plug it in.

Perhaps you should break things down into specific tasks that are causing you issues so that we can help you get this configure properly rather than trying to get around the safeguards that are built into Linux to keep things safe and secure.

---

### Post by Gotaro on 2009-01-28
> **emarkd said:**
> Well, here it is if you really want it.  In your terminal session, run

```

sudo su

```

You'll become root in that shell.  This is really bad practice though because Linux will happily let you screw up terribly and won't even warn you that bad things are about to happen, so I don't recommend it.

What all are you doing that requires root access anyway?  I almost never have to type my password.
Editing things in System Settings->Advanced, adding/editing anything in the root folder (sudo dolphin is NOT a good answer and doesn't work like it should), "activating" the Storage partition at every login, opening Adept..  Hm..  It's hard to come up with this stuff off the top of my head lol.  But I type the password probably 20+ times a day!  Maybe once your personal configuration is mature you don't have to type it often, but in the beginning weeks (or months), for me at least, I'm constantly setting things up, changing things, installing packages, exploring the system, etc.

From what you said, it sounds like I do NOT want to be root!  Lol!  Is there a way to unrequire admin privileges for specific things?

---

### Post by Gotaro on 2009-01-28
> **HotShotDJ said:**
> I have been using Linux as my primary OS for 8 years, and almost NEVER need administrative privileges except for installing/removing software and the very occasional administrative task.  I can't imagine what it is you're doing on a regular basis that would require administrative privileges for "EVERY dang thing."  If you've set up your "Storage" drive in /etc/fstab properly, you should be able to access it as a regular user.  If it is an external "USB" or "Firewire" drive, it should mount with regular user privileges when you plug it in.

Perhaps you should break things down into specific tasks that are causing you issues so that we can help you get this configure properly rather than trying to get around the safeguards that are built into Linux to keep things safe and secure.
Sorry, didn't get my reply done in time!  To your post, addressing what wasn't said in my last reply: the "Storage" drive is actually a FAT32 partition I share between Linux and Windows.  I use it as a little safety buffer so I don't lose my files if I screw up my Kubuntu (it's happened twice so far lol..  lucky I was thinking ahead!).

---

### Post by emarkd on 2009-01-28
Well, yeah, you've gotta enter it to change system settings, but do you really do that so often.  And I've never touched the root folder.  Other than a few places, like /var/www if you maintain a web server, most of what you do should be under your home folder anyway where you already have all the permissions you need.

But no, you can't unrequire admin privileges.  Linux is built from the ground up for security and there's no real way to circumvent it.

---

### Post by fugaki on 2009-01-28
sometimes the best way to learn is by having the power to screw things up, and doing it.
I remember when I first started using linux I ran everything as root, and one day I got the bright idea to chmod 777 everything on my filesystem, and then when everything started failing, I tried to set it back, only to make everything unreadable to anyone.
Moral of the story: be careful what you do in root, or you will be reinstalling.

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> To your post, addressing what wasn't said in my last reply: the "Storage" drive is actually a FAT32 partition I share between Linux and Windows.  I use it as a little safety buffer so I don't lose my files if I screw up my Kubuntu (it's happened twice so far lol..  lucky I was thinking ahead!).Having that partition is a VERY good idea... you got that right. :)  Lets have a look at your fstab -- I'm sure we can easily get it so that it mounts at boot time with the proper permissions.  From a terminal, type the following command and post the output (notice, no "sudo" :))```
cat /etc/fstab
```

---

### Post by JKyleOKC on 2009-01-28
If your machine is physically secure, so that nobody else is likely to be using it, you can disable the password request for sudo quite easily. Go into Terminal, and at the prompt type "sudo visudo" to go into sudo's configuration editor. You'll have to type your password, but it will be the last time. 

Toward the bottom of the file you'll see a commented-out line that contains "NOPASSWD" and that line is the key. Remove the comment character and replace "%sudo" with your login user ID, then save the edited file. If you're not familiar with the "vi" editor, read up on it first; it's not very complicated and comes in handy for things like this.

Once you're back at the terminal prompt, hit ctrl-D to exit the terminal program. Now when you use "sudo" it won't ask you for the password.

Doing it this way retains the safety factor of requiring that you explicitly request admin privilege for dangerous commands, but eliminates the need to keep typing the password. The down side is that if you leave your system running and logged in, anyone can do anything they like to the system! To keep it secure you'll have to log out whenever you go away from the keyboard...

Oops! The procedure didn't work the second time I tried it, so I'm going back to the drawing board to see where it went wrong. It does work on other distributions, so it's possible that our "sudo" has been modified to ignore this option...

Final (?) fix: The modified line has to come AFTER the last line of the file rather than before. I simply scrolled to the end of the file, hit "i" to go into "insert mode," and copied the modified line exactly to be the last line in the file. I then hit "escape" to exit from insert mode, and then "ZZ" (upper case) and Enter to write out the file and exit the visudo program. I then let it sit overnight and tested this morning. No password prompt!

---

### Post by Gotaro on 2009-01-28
> **emarkd said:**
> Well, yeah, you've gotta enter it to change system settings, but do you really do that so often.  And I've never touched the root folder.  Other than a few places, like /var/www if you maintain a web server, most of what you do should be under your home folder anyway where you already have all the permissions you need.

But no, you can't unrequire admin privileges.  Linux is built from the ground up for security and there's no real way to circumvent it.
/sigh..  I suppose it's for the better.  And I go into the root folder to add Gtk themes, because they are NOT in my home folder, like so many tutorials and support posts I've read say they are..
> **fugaki said:**
> sometimes the best way to learn is by having the power to screw things up, and doing it.
I remember when I first started using linux I ran everything as root, and one day I got the bright idea to chmod 777 everything on my filesystem, and then when everything started failing, I tried to set it back, only to make everything unreadable to anyone.
Moral of the story: be careful what you do in root, or you will be reinstalling.
Hey, I like the way that sounds!  I've reinstalled like 3 or 4 times already anyway lol.  (Compiz (not my fault at ALL :P) screwed KDE up twice, I messed some things up with plasmoids and it also refused to restart for some reason, and most recently, because I wanted a fresh, clean install for KDE 4.2!)
> **HotShotDJ said:**
> Having that partition is a VERY good idea... you got that right. :)  Lets have a look at your fstab -- I'm sure we can easily get it so that it mounts at boot time with the proper permissions.  From a terminal, type the following command and post the output (notice, no "sudo" :))```
cat /etc/fstab
```
Haha..  Made me laugh with the "notice, no 'sudo'"! :P
```
gotaro@gotaro-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d339bca4-afd6-4105-9d89-2c7adfb97245 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5c724a3a-d4d5-4302-99a0-d6fd11e8ddc2 none            swap    sw  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Thanks a lot, guys, for being so patient and helpful!  And FAST!  No disrespect to the few appreciated helpers, but OC and KDE forums are NOT the best places for quick, newbie answers.

---

### Post by cardinals_fan on 2009-01-28
I personally use su to start a root shell, handle all my administration, and exit out.  This is not insecure provided that you only run tasks that **must** be run as root and think before you act.  Most of your daily tasks should be performed as a normal user.

If you want to use su, you need to set the root password.  It's against forum policy to reveal how, and I'll respect that.  If you're interested, Google is your friend ;)

---

### Post by Gotaro on 2009-01-28
> **JKyleOKC said:**
> If your machine is physically secure, so that nobody else is likely to be using it, you can disable the password request for sudo quite easily. Go into Terminal, and at the prompt type "sudo visudo" to go into sudo's configuration editor. You'll have to type your password, but it will be the last time. 

Toward the bottom of the file you'll see a commented-out line that contains "NOPASSWD" and that line is the key. Remove the comment character and replace "%sudo" with your login user ID, then save the edited file. If you're not familiar with the "vi" editor, read up on it first; it's not very complicated and comes in handy for things like this.

Once you're back at the terminal prompt, hit ctrl-D to exit the terminal program. Now when you use "sudo" it won't ask you for the password.

Doing it this way retains the safety factor of requiring that you explicitly request admin privilege for dangerous commands, but eliminates the need to keep typing the password. The down side is that if you leave your system running and logged in, anyone can do anything they like to the system! To keep it secure you'll have to log out whenever you go away from the keyboard...
Man..  I can't keep up with the responses!  You guys are amazing!
JKyle, the line now reads:
gotaro ALL=NOPASSWD: ALL
Is that correct?

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> Haha..  Made me laugh with the "notice, no 'sudo'"! :P
```
gotaro@gotaro-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d339bca4-afd6-4105-9d89-2c7adfb97245 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5c724a3a-d4d5-4302-99a0-d6fd11e8ddc2 none            swap    sw  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Ok.. we can fix this up.  You don't have your "Storage" partition listed at all.  That is why you need to be "root" in order to mount it.  First, we need to find out which partition is the "Storage" partition, and then we'll need to edit your /etc/fstab file so that it will automatically mount it to /media/Storage in a manner that will allow users to read and write to it.  NOW, we'll need to use "sudo" --  Please post the output of the following command (and point out which partition is your "Storage" partition, if you know):```
sudo fdisk -l
```I'm going to bed soon, so I won't be able to help again until tomorrow evening.  But armed with the above information, I'm sure somebody else will be able to help you edit your /etc/fstab file.  It really is a simple matter.

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> JKyle, the line now reads:
gotaro ALL=NOPASSWD: ALL
Is that correct?Please.  Don't do that.  It is a VERY bad idea.  Yes, it will work.  But it is also a VERY bad idea.  Did I mention that it is a BAD IDEA to do this?

---

### Post by Gotaro on 2009-01-28
> **cardinals_fan said:**
> I personally use su to start a root shell, handle all my administration, and exit out.  This is not insecure provided that you only run tasks that **must** be run as root and think before you act.  Most of your daily tasks should be performed as a normal user.

If you want to use su, you need to set the root password.  It's against forum policy to reveal how, and I'll respect that.  If you're interested, Google is your friend ;)
That sounds like a good lead..  I'll poke around :).  But I don't really understand why it's against policy, if I understand what the consequences could be?..  :confused:
> **HotShotDJ said:**
> Ok.. we can fix this up.  You don't have your "Storage" partition listed at all.  That is why you need to be "root" in order to mount it.  First, we need to find out which partition is the "Storage" partition, and then we'll need to edit your /etc/fstab file so that it will automatically mount it to /media/Storage in a manner that will allow users to read and write to it.  NOW, we'll need to use "sudo" --  Please post the output of the following command (and point out which partition is your "Storage" partition, if you know):```
sudo fdisk -l
```I'm going to bed soon, so I won't be able to help again until tomorrow evening.  But armed with the above information, I'm sure somebody else will be able to help you edit your /etc/fstab file.  It really is a simple matter.
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8af7208f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9689    77826861   83  Linux
/dev/sda2            9690       15778    48909892+   b  W95 FAT32
/dev/sda3   *       15779       29164   107523045    7  HPFS/NTFS
/dev/sda4           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

```
On that list, it's /dev/sda2; AKA (hd0,1)
> **HotShotDJ said:**
> Please.  Don't do that.  It is a VERY bad idea.  Yes, it will work.  But it is also a VERY bad idea.  Did I mention that it is a BAD IDEA to do this?
Hahaha..  Well, he said it didn't work in his post, and it didn't work for me, either.  I'll change it back.

---

### Post by jimmy the saint on 2009-01-28
Please refrain from giving out instructions as to how to login as root or enable the SU.  It is expressly against the forum rules and inappropriate for the beginning forums.

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> That sounds like a good lead..  I'll poke around :).  But I don't really understand why it's against policy, if I understand what the consequences could be?..  :confused:Nah.. don't poke around.  It is against policy because it bypasses an important security feature of your OS.  Don't do it. (I'm beginning to sound like my mother!!!!)> **Gotaro said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8af7208f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9689    77826861   83  Linux
/dev/sda2            9690       15778    48909892+   b  W95 FAT32
/dev/sda3   *       15779       29164   107523045    7  HPFS/NTFS
/dev/sda4           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

```
On that list, it's /dev/sda2; AKA (hd0,1)Ok... open a terminal and run the following:```
sudo mkdir /media/Storage
```Next, you need to edit your fstab:```
kdesudo kate /etc/fstab
```Add the following lines to the end of that file:```
# Shared FAT32 Partition
/dev/sda2 /media/Storage vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```Save the file and close the editor.  You probably don't need to do the next step, but lets do it anyway just to be sure.  Run the following command:```
sudo mount -a
```Now, you should be able to mount that partition as a regular user, either through Dolphin, Konqueror, or at the command line with:```
mount /media/Storage
```(no sudo needed)

---

### Post by Gotaro on 2009-01-28
> **jimmy the saint said:**
> Please refrain from giving out instructions as to how to login as root or enable the SU.  It is expressly against the forum rules and inappropriate for the beginning forums.
jimmy, the link in your signature explaining the policy made me feel like a 9 year old kid.  :P  Basically, I'm not old enough to know what I'm doing, and to keep me from hurting myself as well as induce learning..  I'm not allowed to know :P.  But VERY good advice with the kdesu!  I was using sudo dolphin from a terminal, but alt+f2 kdesu dolphin works like a charm!

---

### Post by Gotaro on 2009-01-28
> **HotShotDJ said:**
> Nah.. don't poke around.  It is against policy because it bypasses an important security feature of your OS.  Don't do it. (I'm beginning to sound like my mother!!!!)Ok... open a terminal and run the following:```
sudo mkdir /media/Storage
```Next, you need to edit your fstab:```
gksudo gedit /etc/fstab
```Add the following lines to the end of that file:```
# Shared FAT32 Partition
/dev/sda2 /media/Storage vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```Save the file and close the editor.  You probably don't need to do the next step, but lets do it anyway just to be sure.  Run the following command:```
sudo mount -a
```Now, you should be able to mount that partition as a regular user, either through Dolphin, Konqueror, or at the command line with:```
mount /media/Storage
```(no sudo needed)
Okay..  For some reason, "gksudo gedit /etc/fstab" doesn't open anything up.  It just loads in the background for a few seconds, then goes to the next line.

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> Okay..  For some reason, "gksudo gedit /etc/fstab" doesn't open anything up.  It just loads in the background for a few seconds, then goes to the next line.Yes... I forgot that you use KDE.  I've edited my post to fix that... replace gksudo gedit with kdesudo kate

---

### Post by Gotaro on 2009-01-28
> **HotShotDJ said:**
> Yes... I forgot that you use KDE.  I've edited my post to fix that... replace gksudo gedit with kdesu kate
In a terminal, I get:
bash: kdesu: command not found
If I alt+f2, kdesu works.  /shrug

Okay, all edited and ready to go!  I'm going to restart now and see what happens.  You can go to bed!  Thanks for staying up :)

P.S.: Long live IPU!

--Edit--
Success!  It mounts perfectly!  I'm not sure what all of those parameters were that you had me put in..  But I guess it's not important.  How often am I really going to be--  Nevermind.  As soon as I say it, I'm going to break Kubuntu again and have to repeat these steps.  >_>;

So that issue is resolved..  And I'm not allowed to know how to run everything as root.  I think that covers everything!  Thanks to everyone who helped!  I'm sure you'll be seeing me around..

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> In a terminal, I get:
bash: kdesu: command not found
If I alt+f2, kdesu works.  /shrug

Okay, all edited and ready to go!  I'm going to restart now and see what happens.  You can go to bed!  Thanks for staying up :)Its been awhile since I've used KDE... maybe you need to use kdesudo rather than kdesu.  I'm not sure.  In any case, you don't need to reboot/restart.  Thats a Windows thing.

> **Gotaro said:**
> P.S.: Long live IPU!May Her hooves never be shod!

---

### Post by HotShotDJ on 2009-01-28
> **Gotaro said:**
> I'm not sure what all of those parameters were that you had me put in..  But I guess it's not important.  How often am I really going to be--  Nevermind.  As soon as I say it, I'm going to break Kubuntu again and have to repeat these steps.  >_>;LOL.... actually, its not a bad idea for you to know what we did... let me break it down for you:

_/dev/sda2_ = the partition we want to mount

_/media/Storage_ = the mount point... in other words, where on the file system it will be placed

_vfat_ = the filesystem (FAT32 is vfat in Linux)

_defaults_ = these are the default parameters (rw, suid, dev, exec, auto, nouser, async)... we start with that, then modify them as appropriate.

_user_ = Permit any user to mount the file system (and implies noexec, nosuid,nodev unless modified after, as we do next)

_exec_ = Permit execution of binaries for this file system (needed because "user" defaults to noexec -- you may remove this if you don't want to allow the execution of binaries from this partition)

_uid=1000_ = User ID set to 1000, which should be the first user set up when you installed Ubuntu -- in other words, YOU. :)

_gid=100_ = Group ID set to 100, which is "users"

_umask=000_ = gives read/write/execute privileges to all users, and is required with directories shared with windows because Windows does not deal well with Linux permissions.

_0_ = The Dump bit.  Dump is rarely used.  0 is the default.

_0_ = Sets the order that the file system is checked (fsck).  0 disables checking, which is what we want with this FAT32 partition.  If it were a native Linux file system that we mount at boot time, we would probably set this to 2 (1 is reserved for the / partition)

---

### Post by JKyleOKC on 2009-01-28
I've edited the original post now to add the detail that makes it work.

As for being a "very bad idea" I disagree strongly. The whole point of Linux is to let YOU, rather than some remote developer, have full control of your system. This solution answers one of your original questions, and I did point out the very real dangers involved. If you're in a dorm room or office and leave the system running under your log-in, then yes, it's a bad idea. If you take proper security precautions, then it removes what you see as an annoyance.

It appears that forum management finds the idea acceptable, per message #2 at [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) which tells specifically how to use visudo to reconfigure...

---

### Post by Gotaro on 2009-01-28
> **HotShotDJ said:**
> Its been awhile since I've used KDE... maybe you need to use kdesudo rather than kdesu.
Yes, kdesudo worked from a terminal.  Not sure when to use kdesudo vs sudo, though.
> **HotShotDJ said:**
> LOL.... actually, its not a bad idea for you to know what we did... let me break it down for you:
Hey, thanks!  That was useful.  The most helpful thing I took out of it was that Linux isn't compatible with Windows permissions (and vis versa).
> **JKyleOKC said:**
> I've edited the original post now to add the detail that makes it work.

As for being a "very bad idea" I disagree strongly. The whole point of Linux is to let YOU, rather than some remote developer, have full control of your system. This solution answers one of your original questions, and I did point out the very real dangers involved. If you're in a dorm room or office and leave the system running under your log-in, then yes, it's a bad idea. If you take proper security precautions, then it removes what you see as an annoyance.

It appears that forum management finds the idea acceptable, per message #2 at [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) which tells specifically how to use visudo to reconfigure...
All right, I've edited sudoers and it seems to be working properly!  Two things: it could just be that I didn't notice before, but when I open Adept, two taskbar buttons form, and when I close, only one goes away immediately; The other takes some time.  And also, I now realize that there is a distinction between needing to be root to do something and needing administrative privileges.  For instance, I still have to type in a password to gain admin privileges to apply changes to GRUB Editor in System Settings->Advanced.

---

### Post by HotShotDJ on 2009-01-28
> **JKyleOKC said:**
> It appears that forum management finds the idea acceptable, per message #2 at [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) which tells specifically how to use visudo to reconfigure...Not really.  Its just the better of two evils.  You left out this part from that very same post:> I STRONGLY advise against weakening your overall security. Keep in mind, if you are connected to the internet you are not the only potential user (as any network monitoring application will show in short order).In any case, I find the idea of counseling relatively new users, who may be unfamiliar with the security model of Ubuntu, to override that model repugnant.  By following your advise, he has potentially opened up a security hole that you can drive a truck through.  You don't need physical access to exploit a passwordless sudo.  All it will take is one malicious script run from his browser or downloaded from the net to turn his system to crap.  Sure, its better than running as root, but not much.

It is much better to show them how to make that model work for them, rather than against them.  Of course, it takes more time to educate than to simply acquiesce to their innocently asked, but inappropriate, requests.  For example, show him (as I did) how to properly configure his system so that he won't need to use his password as often for routine tasks.

---

### Post by egalvan on 2009-01-29
> **HotShotDJ said:**
> LOL.... actually, its not a bad idea for you to know what we did... let me break it down for you:
n)

Many thanks for this concise explanation.
It's what is lacking in so many HOW-TO's out there...

They explain the HOW, but leave out the WHY and WHAT. :)

Again, THANKS!

---


---
title: "I cannot login to Ubuntu through any means. Need help!"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by silent contender on 2009-03-07
I have a Ubuntu 8.10 install and use KDE 4.1 and KDM.  Since the updating it, I have not been able to login through KDM or the shell.  When I use KDM to login, the screen goes blank after I login and kicks me to the shell login.  The shell login does not work either!  I log in and it kick me back out instantly without an error message.

I have checked the Xorg, auth, and kdm log without avail.  The auth log does show me attempting to login unless I type the wrong login.  The Xorg only note a bad driver (which I uninstalled) and nothing happens.  The kdm log only mentions that it cannot resolve system encoding.

Any help would be greatly appreciated.  I'll post whatever's need.

Thanks.

---

### Post by taurus on 2009-03-07
You didn't max out your / (root filesystem), 100%?

```
df -h
```

---

### Post by mordoc on 2009-03-07
> **silent contender said:**
> I have a Ubuntu 8.10 install and use KDE 4.1 and KDM.  Since the updating it, I have not been able to login through KDM or the shell.  When I use KDM to login, the screen goes blank after I login and kicks me to the shell login.  The shell login does not work either!  I log in and it kick me back out instantly without an error message.

I have checked the Xorg, auth, and kdm log without avail.  The auth log does show me attempting to login unless I type the wrong login.  The Xorg only note a bad driver (which I uninstalled) and nothing happens.  The kdm log only mentions that it cannot resolve system encoding.

Any help would be greatly appreciated.  I'll post whatever's need.

Thanks.

When you boot your machine, hit ESC as you see the brief flash of GRUB...If you catch it in time you should get to a menu of kernels on the screen.  Choose the most recent version with the words "Recovery" by it.  That will boot you into a mode that I think you should be able to reset the passwords from by going to shell mode there and using "passwd username"

Hope this helps!

---

### Post by silent contender on 2009-03-07
My HDD is quite empty: 19GB used, 43GB.

On a side note: I only can use the root shell in the recovery console.

I created a new account and I can change the password for that, but my old account won't change.  When I use

passwd <old username>

I get: Segmentation fault

---

### Post by silent contender on 2009-03-07
When I try logging in my auth.log does NOT log anything unless I type in an invalid username/password.

I have no clue how to go on.  Any ideas are welcomed.

---

### Post by taurus on 2009-03-07
Boot your machine into recovery mode (from GRUB menu) and get into root shell.  Then, post the output of this command here.

```
df -h
```
You can also change your password from the prompt too.

```
passwd your_login_name
```

---

### Post by silent contender on 2009-03-07
I've tried that and neither helps.  I'm positive that I know and have type my account info correctly (I've even made a new one to check, it didn't help)

```
df -h
```
/dev/sda1 Size: 65G Used: 18G Avail: 44G Use%: 30% Mounted on: /

My daemon.log has this:
init: tty1 main process (5755) killed by SEGV signal

What is a SEGV (segmentation fault?)?

---

### Post by taurus on 2009-03-07
How about

```
fdisk -l
cat /etc/fstab
```

---

### Post by silent contender on 2009-03-07
```

Device    Boot   Start     End     Blocks   Id  System
/dev/sda1  *      1        9042  68357488+  83  Linux

```

```

cat /etc/fstab
/dev/sda1 UUD=03a......812d  /  ext3 relatime,errors=remount-ro 0   1

```

Sorry about the poor truncating, the outputs lengthy (and it on, obviously a different computer).

Taurus: Please look at my last post (I added some stuff about a SEGV signal)

---

### Post by taurus on 2009-03-07
Can you post your /etc/apt/sources.list?  (It's probably a long list though.)

```
cat /etc/apt/sources.list
```

p.s.  By the way, if you use UUID to mount / in /etc/fstab, you do not need to include /dev/sda1 in front.  I assume that is just a typo here.

```

**[COLOR="Red"]/dev/sda1[/COLOR]** UUD=03a......812d  /  ext3 relatime,errors=remount-ro 0   1
```

---

### Post by silent contender on 2009-03-07
cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
....
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://security](http://security).......
...
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

---

### Post by T.J. on 2009-03-07
Sounds like a permissions problem with KDE files in your /home directory, or that your login entry in the shadow, or passwd files has been damaged though mishap. Not to imply anything, but you haven't tried editing them by hand, have you?

As a test, can you log into the recovery console, start a shell, and create a new user account?

adduser <new name>
passwd <new name>

Then reboot as normal and see if you can log in using the new account.  If that works, we can fix things.  After you check that, we can go through the rest step by step.

---

### Post by QuaxEros on 2009-03-08
Hi Guys,
Joining you since i have the exact same problem.

From the recovery console:
adduser ;works fine
passwd new_user ;works fine
passwd old_user ;gives error: segmentation fault

Neither of the accounts give access though.
The F7 (graphical) screen is gone after the first login attempt. The tty1 login prompt gives no error about password and will popup again and again. If a false password is given the prompt does return an error!

think this is what silent contender already stated, hope he agrees.

---

### Post by silent contender on 2009-03-08
QuaxEros, that's EXACTLY the problem I have too!  The segmentation fault and everything!  I've narrowed it down to one process that has the SEGV signal.  Trying to figure out the process name (have process IDs).

Can someone point us in the right direction.

QuaxEros, can you lookup your daemon.log?  Use
```
nano /var/log/daemon.log -v
```
Or if you've tried to log in recently today
```
tail /var/log/daemon.log
```
and see if you can find something like this:
```

Mar  7 22:39:39 nothing init: tty1 main process (5755) killed by SEGV signal
Mar  7 22:39:39 nothing init: tty1 main process ended, respawning

```
Your log will differ by a little ("nothing" should be replaced by you computer name, etc)

---

### Post by T.J. on 2009-03-08
Can you login into the new account successfully on the command line?  If so, this may indicate a permissions problem or bug in the KDM package.

I'm assuming you are using the Kubuntu packages from the normal repositories?  I'll install them, test KDM and get back to you.  If you are using packages from external sources or test packages from Launchpad, you might be getting a beta package with serious flaws. I'd remove those immediately, unless you know what you are getting into.


T.J.

UPDATE: I tested the standard packages from the normal repository not the PPA, and they work, I can log in.  I noticed that a previous post lists the PPA packages:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

I'd strongly suggest that you purge them temporarily, only to see if they have a bug that has damaged your installation.

---

### Post by silent contender on 2009-03-08
Just purge the repo and no luck.  I can't login using the new account in anyway either.

Any idea how to get a process name from a process ID?

---

### Post by silent contender on 2009-03-08
I just narrowed down the problem to getty.  Somehow getty is having segmentation faults and crashing my login (kudos to genii in IRC).

---

### Post by silent contender on 2009-03-09
I've tried reinstalling getty, login, and ubuntu-minimal several times, it doesn't seem to help.

Please help.

Thanks in advance.

---

### Post by QuaxEros on 2009-03-16
> **T.J. said:**
> Then reboot as normal and see if you can log in using the new account. If that works, we can fix things. After you check that, we can go through the rest step by step.

Does this mean you're still helping us? I'm still stuck.

---


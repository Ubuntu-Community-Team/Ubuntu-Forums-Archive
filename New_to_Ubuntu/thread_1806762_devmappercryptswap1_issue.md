---
title: "/dev/mapper/cryptswap1 issue"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by kalimojo on 2011-07-18
on Ubuntu 11.04
every fourth or fifth boot i get the following message 



The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
 Continue to wait; or Press S to skip mounting or M for manual recovery


the system then boots normally


any ideas ?

---

### Post by fractalman on 2011-07-18
I have the same error message on booting, it only started a few days ago after installing the nvidia xdriver.  plymouth is disconnected as well,  it doesn't seem to be causing any problems though other than a huge ubuntu logo on shutdown.

---

### Post by alex_sko on 2011-10-14
Hi, I also have the exact same message on boot:

The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
 Continue to wait; or Press S to skip mounting or M for manual recovery

I have a freshly installed Ubuntu 11.04. After I wait a few secs, all is fine and i boot normally. I don't know if this matters, but i have checked with yes the encryption of my home folder during installation and also, Ubuntu is not the only OS on my computer (would be happy if i can fix this without affecting other partitions)

Thanks a lot for your help!!! :)

---

### Post by mech-e on 2011-12-25
Looks like this is a pretty common problem if you have an encrypted home folder, lots of bug reports on it, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086).

Looks like OS is trying to mount this encrypted partition at boot, when should defer mounting until user logs on

In the absence of a bug fix, I believe two possible ways to workaround:
(1) edit the fstab entry for cryptswap1 to include the option 'noauto', for instance via terminal
```
sudo gedit /etc/fstab
```
then change the line that looks like
```
/dev/mapper/cryptswap1  none  swap  sw 0  0
```
to 
```
/dev/mapper/cryptswap1 none swap sw,noauto 0  0
```
Note that the swap partition never gets mounted automatically this way, however (which is probably non-ideal).

(2) remove encryption from home folder. There are posts on how to do this, but it is fairly complex and the enemy of good is better...

---

### Post by arjunrj405 on 2011-12-25
how to post a new thread...
I am completely new and i dunno how to post threads

---

### Post by Ravenworks on 2012-03-21
Thank you for the info,I am one of those that never get around to fixing his own things until tonight.I have been living with this for almost a year now and a few clicks and a cut and paste all is well.
Thank you again.

---


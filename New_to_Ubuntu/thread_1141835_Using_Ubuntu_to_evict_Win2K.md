---
title: "Using Ubuntu to evict Win2K"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-04-28
First, thanks to all you guys for your input on installing my driver from the terminal, and the assistance on picking out a printer/4-in-1. Second I have a duel boot WD 160GB. Win2K is taking up 100GB of space; it also craped out on me several months ago. What can I do either in the desktop environment or from the terminal to give Ubuntu all the disk?

---

### Post by ymra on 2009-04-28
You will need to boot off of the live cd and use gparted.  That will allow you to delete the windows 2000 install and resize the ubuntu partion to fill the empty space.

---

### Post by egalvan on 2009-04-28
> **Howard Roark said:**
> I have a duel boot WD 160GB. Win2K is taking up 100GB of space; it craped out several months ago. What can I do either in the desktop environment or from the terminal to give Ubuntu all the disk?

Since Win2K is not using any *nix filesystems,
Ubuntu **should not** be dependant on that partition....

So, you should be able to fire up Gparted,
right-click the W2k partition,
pick "un-mount",
apply the operation if needed...
delete that partition,
then apply.

Create another partition, and format as desired (ext2, ext3, ext4, etc)
just remember to "apply" your changes, or you will lose them.
Ask me how I know :)

If gparted does not allow un-mounting the partition,
then something is using it,
and you are better off using a LiveCD environment.

And if you want to merge the un-used space with an existing Linux partition, you need a LiveCD environment anyway...

So it may just be easier to use a LiveCD from the start :)

And yes, I have deleted **Windows** partitions from a running system.

---

### Post by sneeks on 2009-05-03
as above,but would it not be easier to just do a new install,iv'e found jaunty to be quite good,but xubuntu 9.04 is the best one yet for older systems,runs real quick and all the old problems that were there are now gone.kids love it too..

---

### Post by fritzm48 on 2009-05-03
> **sneeks said:**
> as above,but would it not be easier to just do a new install,iv'e found jaunty to be quite good,but xubuntu 9.04 is the best one yet for older systems,runs real quick and all the old problems that were there are now gone.kids love it too..
I have xubuntu 8.10 installed and received an update that 9.04 is available. I attempted the upgrade but the system crashed and pc would not reboot. I had to download xubuntu 8.10 all over again. Maybe I should then have tried 9.04 as a fresh install. Do you think it is safe to try the upgrade again or should I just settle for 8.10? My pc is Pentium 3, 800 mgz, 256k ram.

---

### Post by sneeks on 2009-05-03
> **fritzm48 said:**
> I have xubuntu 8.10 installed and received an update that 9.04 is available. I attempted the upgrade but the system crashed and pc would not reboot. I had to download xubuntu 8.10 all over again. Maybe I should then have tried 9.04 as a fresh install. Do you think it is safe to try the upgrade again or should I just settle for 8.10? My pc is Pentium 3, 800 mgz, 256k ram.

no my friend,go for the fresh install,worked for me and a few more,i know your supposed to be able to upgrade but sometimes it just don't work.
your pc is fine for it too,but to help a bit more try the alternate cd for a text based install,it is easy so don't worry,it just asks you the same questions really that gui does but is better for an older system.

---


---
title: "NFS Networking"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by hasanilingi on 2006-12-23
hi guys i have problem share my Ubuntu Edgy with NFS. The sharing that i want to do is in this diagram. As you see i have 11 PC installed ubuntu. i want to do make the most effective sharing with NFS.i made one of them as a master server and the others as slave servers.Then i create directory for each slave host (slave-1, slave-2,....) under master host's /home/master/Desktop/share/ directory. The master server will mount others(10 slave machines) /home/slave-X/Desktop directories to it's /home/master/Desktop/share/slave-X directories as a client, and the other slaves will mount the master's /home/master/Desktop/share directory to their /home/slave-X/Desktop/share . Because i assume that if i can achieve this networking, i will be able to see all slaves Desktop directory under all slaves share directory.so my network traffic will decrease.&#304; am triying to do this networking.But i am getting problem with it. The problem is The master host can mount the slaves Desktop, but when i try to mount the Master host's Desktop from one of slaves, the slave is freezing.
any help will be wellcome.

here is my network diagram.

[[IMG]http://img356.imageshack.us/img356/6452/diagram1ua3.th.jpg[/IMG]](http://img356.imageshack.us/my.php?image=diagram1ua3.jpg)

---

### Post by djRobbieF on 2006-12-23
Are you dead-set on NFS?  Because I just wrote a tutorial for SSH that could be used to accomplish the same thing.

If you're interested in at least trying to see if this would suit you, take a look at [http://ubuntuforums.org/showthread.php?t=324254](http://ubuntuforums.org/showthread.php?t=324254)

I've not used NFS, so can't help you there; but if SSH works for you, maybe my tutorial will help you along.

Cheers.

---

### Post by mulligan.can on 2006-12-24
I could be completely wrong but it looks like the slave will end up remounting its own nfs share. I'm guessing but perhaps thats the reason the slave is freezing up? might be getting into an endless loop with its nfs share...

---

### Post by hasanilingi on 2006-12-25
> **djRobbieF said:**
> Are you dead-set on NFS?  Because I just wrote a tutorial for SSH that could be used to accomplish the same thing.

If you're interested in at least trying to see if this would suit you, take a look at [http://ubuntuforums.org/showthread.php?t=324254](http://ubuntuforums.org/showthread.php?t=324254)

I've not used NFS, so can't help you there; but if SSH works for you, maybe my tutorial will help you along.

Cheers.

Thanks for your offer, but i think NFS is faster adn it fits my needs (this is only my idea). so i want to use NFS,But i am not able to achieve mount all PC as in my diagram, using sshfs instead NFS

---

### Post by jdusablon on 2006-12-29
mulligan.can is right.

You can't have two machines mount each other's NFS shares when they're nested (one within the other.)

Also why are you sharing BOTH ways??

---


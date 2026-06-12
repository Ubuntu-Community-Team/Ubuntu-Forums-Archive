---
title: "Kernel Panic: VFS: Unable to mount root fs on unknown wn-block"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by atifqayyum on 2009-10-08
I could not find the solution of the problem for following message:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block(0,0)
Can anyone help for the solution.
I have tried the previous version of Kernel also. At present my CD drive is not detecting auto boot. so cannot boot from Ubuntu 9.04, Live CD
                                                                   Thanks,
 
                                                                                                      <Atif>

---

### Post by InfectedWithDrew on 2009-10-08
> **atifqayyum said:**
> I could not find the solution of the problem for following message:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block(0,0)
Can anyone help for the solution.
I have tried the previous version of Kernel also. At present my CD drive is not detecting auto boot. so cannot boot from Ubuntu 9.04, Live CD
                                                                   Thanks,
 
                                                                                                      <Atif>

I'm not an expert with that kernel stuff but you can usually hit DEL or a F key to choose boot order so you can boot from CD.

---

### Post by ost2life on 2009-10-10
I'm also having this problem, same situation. Just updated everything. What actually happened to me was that the update finished then the sound and video cut out. I hit the reset button then I got the warning about mounting root fs. I would really rather not reinstall ubuntu as I have finally got the set up juat the way I want it, so I hopw that someone will be able to help us. 

Thankyou in advance.

---

### Post by RichardLinx on 2009-10-10
The infamous Ubuntu kernel panic strikes again. I don't know much about fixing it, but reinserting/changing your RAM might fix it. Why? I have no idea, I just know that it does.

---

### Post by powel212 on 2009-10-10
First go into the bios, (hit del on statup).

check that CD or DVD is the first boot device in order to boot from CD

if you boot from the hard drive and you get to the command prompt try running

```
fsck
```

It will find and repair errors in the system and then you can restart.

I hope that helps

Powel

---

### Post by Zoot7 on 2009-10-10
I take it that it's Jaunty with kernel 2.6.28-15? I myself got a few kernel panics with that. What sorted it for me was upgrading to 2.6.31, which works fine on my machine.
**[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")**

---

### Post by TimMedcalf on 2009-11-10
Just had this in karmic, but the situation was different - machine kept locking up in gnome and after several hard power-offs this message appeared.

i managed to boot into my old jaunty partition and ran a disk check through GPartEd which resolved it.

Hope that helps. If you don't have another partition to boot to, try a live cd and run the check from that.

---


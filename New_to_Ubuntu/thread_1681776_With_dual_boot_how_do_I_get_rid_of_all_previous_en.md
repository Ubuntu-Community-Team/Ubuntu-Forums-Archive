---
title: "With dual boot how do I get rid of all previous entries at boot up"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by bobmac on 2011-02-04
Folks,

I've got a dual boot machine which at boot up new has many entries of the o/s or kernel or whatever.

Is there any way of getting rid of at least some of them?

Regards,

Bob

---

### Post by quadproc on 2011-02-04
> **bobmac said:**
> 
I've got a dual boot machine which at boot up new has many entries of the o/s or kernel or whatever.

Is there any way of getting rid of at least some of them?

Yes, you have at least two choices: you can remove the unwanted entries by using Synaptic or apt-get, or you can change the permissions on the unwanted kernels so that they are not executable.  Whichever method you choose, you then need to run update-grub so that a new grub.cfg file is created.

There is a good writeup on grub at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
See especially the section on Configuring GRUB 2.

quadproc

---

### Post by Darkness Des on 2011-02-04
I suggest installing [Ubuntu Tweak]("http://ubuntu-tweak.com/"), as it has a feature built in where it will remove old kernels if you tell it to.

---

### Post by baldy4eva on 2011-02-04
> **Darkness Des said:**
> I suggest installing [Ubuntu Tweak]("http://ubuntu-tweak.com/")....

I'd agree with Des on this one... works a treat, saves all the terminal bashing

---

### Post by Dutch70 on 2011-02-04
Ubuntu Tweak will get rid of all old kernels except for one. You should keep at least two, in case problems arise with your kernel.

I recommend going to synaptic, do a search for "image-2" without the quotation marks and delete the ones you don't want. it's very simple. Just make sure you don't delete your current version.

Don't forget to run _update-grub_ with root permissions.

---

### Post by bobmac on 2011-02-05
Many thanks to Des and yourself for putting me on to ubuntu tweek - what a great app

Regards,

Bob

---


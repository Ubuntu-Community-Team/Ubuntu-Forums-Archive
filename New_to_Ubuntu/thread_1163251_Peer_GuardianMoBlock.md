---
title: "Peer Guardian/MoBlock"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by khaos28 on 2009-05-18
So i went to the DL page for Peer Guardian and got and installed the PG .DEB version ([http://sourceforge.net/project/downl...deb&a=90811190]("http://sourceforge.net/project/downloading.php?group_id=131687&filename=peerguardnf-1.5beta.i386.deb&a=90811190")) and I'm not really sure where to go from there...is there a GUI i can interact with? update the IP lists? i'm kind of new to this, so any help would be greatly appreciated. 

Also if MoBlock is better then PG in your opinion please explain why?

Thanks.
Jake

Edit: Like how do i use it and get it to open?

Is there a sudo code that i can add into my terminal to make it Dl and Install better? when i Dl'ed the original time, i had some pre-installed app come up and do it for me, but idk what that all did.

---

### Post by which ones pink on 2009-05-18
```
sudo apt-get install blockcontrol mobloquer
```

Blockcontrol is MoBlock, and mobloquer is the GUI for it.  I use Moblock, and it uses the same type of blocklists as PG, so it's probably just as good.  I didn't even know there was a PG for Linux.

---

### Post by khaos28 on 2009-05-18
> **which ones pink said:**
> ```
sudo apt-get install blockcontrol mobloquer
```Blockcontrol is MoBlock, and mobloquer is the GUI for it.  I use Moblock, and it uses the same type of blocklists as PG, so it's probably just as good.  I didn't even know there was a PG for Linux.


So, it uses the same list blockers as PG then? which is pretty much all i care about :)

I did get this when i put it into my terminal...

khaos28@Jake:~$ sudo apt-get install blockcontrol mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package blockcontrol


it said it couldn't find the package for blockcontrol?

---

### Post by which ones pink on 2009-05-18
Oops, I forgot you have to add some repos.  Here's how [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by khaos28 on 2009-05-18
Thanks!

i'll give it a look and see what i can do.

---

### Post by lovinglinux on 2009-05-18
Peerguardian is not supported anymore and shouldn't be used. I have it installed just for merging local blocklists, but I don't think it works anymore for what is designed to do.  

Uninstall Peerguardian and install [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/). These links also provide instructions on how to install and use them.

I personally prefer moblock, but both works great.

---


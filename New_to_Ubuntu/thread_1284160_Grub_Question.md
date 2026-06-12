---
title: "Grub Question"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by poliltimmy on 2009-10-06
I want to try 9.10. I dual boot with XP. How do I edit Grub to have my working perfectly 9.04 as the default OS after I install the triple boot with 9.10. Also will I have any problems using Kubuntu as I would like to check out KDE?  Thanks in advance for any help!!!

---

### Post by QIII on 2009-10-06
Karmic installs with GRUB2, which may kill GRUB, so you won't be able to modify menu.lst and have it work as in the old days.  GRUB2 uses grub.cfg.

Wait until someone else chimes in before you go with this, but here is what I would do -- bear in mind that I haven't muddled with grub.cfg under GRUB2.

You may not get Jaunty as the default, but you can make sure that GRUB2 is able to see all of your OSs by using os-prober and updating GRUB2.  You would probably have to edit grub.cfg, but like I say I haven't played around with that yet.

Install Karmic on the partition of your choice, then...

```
sudo apt-get install os-prober
```You will probably get a message that you have the newest version.  Just move on.

```
sudo os-prober
``````
sudo update-grub2
```I'll do some looking around for how (and whether you should) update grub.cfg in this case.  You can certainly do it, but I'm not comfortable suggesting it until I have a chance to investigate and break one of my systems three times to know the pitfalls.

---

### Post by poliltimmy on 2009-10-06
Thanks! I guess I better put it off. I think this issue is important. This is the way I have tried and upgraded since 7.10. I get the new figured out and working and use GParted and Super Grub Fixer to delete the old. I don't think I'm the only one that does it this way. It keeps a working Ubuntu while I fiddle. Can Grub2 be installed in Jaunty therefore negating my concerns?

---

### Post by QIII on 2009-10-06
I updated Jaunty to ext4 and GRUB2 some time ago on my "production" machines.  Those are fairly painless operations (BUT -- if you find a tutorial, remember that you do the update to ext4 from the LiveCD, since you shouldn't try to change the file system on a mounted drive.  I have read a lot of horror stories.)

I usually just completely wipe my Ubuntu drives on my "test" machines and reinstall fresh for testing.  Both of them have Windows, but on separate physical hard drives, so that is not an issue.

I have never had the nightmares doing updates to new versions without complete reinstalls, but that doesn't mean others don't have them.  I'm waffling on whether to do an update to Karmic on my production machines or do a fresh install.

---


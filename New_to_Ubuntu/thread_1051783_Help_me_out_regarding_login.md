---
title: "Help me out regarding login"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by mani1840 on 2009-01-27
Hi all,

      I just solve problems by going th prev threads, but couldn't find a sol. for this one :(

      I accidentally deleted cache folder in filesystem/var/cache.

Later on when I get to the login screen after booting, I just can't type my user name as I can't move my mouse or it doesn't take any input. Tried recovery mode but no luck. Help me out.

I m using Ubuntu 8.10 Intrepid Ibex. Thanks  a lot.

---

### Post by ajgreeny on 2009-01-27
Firstly, are you sure it's **home/var** and not just **/var,** as there is no home/var folder in my ubuntu and never has been a home/var in any linux I've run, as far as I can remember?

Secondly, if it was /var, how did you manage to "accidentally" delete the folder?  It is owned by root and would need sudo to remove it.  It shows how careful you must be when doing things to your system that you don't fully understand.

Unfortunately, if it really was /var, I don't know how to get your system back.  Others with more knowledge of the linux file system may be able to help.

---

### Post by Temposs on 2009-01-27
I think ajgreeny is right. If you deleted /var, deleting that entire directory probably means you need to reinstall, unless you've got a backup of /var. You should probably backup your personal data in /home to another partition/drive and reinstall.

But wait for a couple others to confirm...

---

### Post by mani1840 on 2009-01-27
> **ajgreeny said:**
> Firstly, are you sure it's **home/var** and not just **/var,** as there is no home/var folder in my ubuntu and never has been a home/var in any linux I've run, as far as I can remember?

Secondly, if it was /var, how did you manage to "accidentally" delete the folder?  It is owned by root and would need sudo to remove it.  It shows how careful you must be when doing things to your system that you don't fully understand.

Unfortunately, if it really was /var, I don't know how to get your system back.  Others with more knowledge of the linux file system may be able to help.

my mistake....it was filesystem/var/cache.

actually cache got deleted...

Well I was playing around with Nautilus to delete a file in cache.

Its my fault  n mistake do happen :(

---

### Post by mani1840 on 2009-01-27
> **Temposs said:**
> I think ajgreeny is right. If you deleted /var, deleting that entire directory probably means you need to reinstall, unless you've got a backup of /var. You should probably backup your personal data in /home to another partition/drive and reinstall.

But wait for a couple others to confirm...


well it was cache tht got deleted not var.. :)

---

### Post by talsemgeest on 2009-01-27
> **mani1840 said:**
> my mistake....it was filesystem/var/cache.

actually cache got deleted...

Well I was playing around with Nautilus to delete a file in cache.

Its my fault  n mistake do happen :(
You deleted it using nautilus? I guess you were using sudo nautilus, or gksudo nautilus. Unless you ran permenant delete (shift+delete), then your files *might* still be in the root trash. Take a look in /root/.trash (I think that is it, but I might be wrong) and see if your files are in there.

---

### Post by mani1840 on 2009-01-27
> **talsemgeest said:**
> You deleted it using nautilus? I guess you were using sudo nautilus, or gksudo nautilus. Unless you ran permenant delete (shift+delete), then your files *might* still be in the root trash. Take a look in /root/.trash (I think that is it, but I might be wrong) and see if your files are in there.


Yep ...live CD did a trick.

Got there and got my files.


Thanks GUyz....hppy ending :D

---

### Post by talsemgeest on 2009-01-27
> **mani1840 said:**
> Yep ...live CD did a trick.

Got there and got my files.


Thanks GUyz....hppy ending :D
Awesome, glad you got it working! :)

---


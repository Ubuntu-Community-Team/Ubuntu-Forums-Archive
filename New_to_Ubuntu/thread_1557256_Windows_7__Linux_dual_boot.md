---
title: "Windows 7 / Linux dual boot"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by 2uk_ on 2010-08-20
Hi
I've been running Ubuntu for a while now and I decided to dual boot,
so i partitioned the HD and installed Windows 7 in the new partition and it works fine,
 
But when I boot up it just goes straight to Windows 7 and I can't work out how to get into the Linux partition.. 
Can anyone help? :)

---

### Post by LowSky on 2010-08-20
You will need to reinstall GRUB. You will need the Latest Live CD

see this for more details
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 2uk_ on 2010-08-20
Awwww man all this for age of empires :'(

---

### Post by Rubi1200 on 2010-08-20
If you are looking for a slightly easier method, try this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You will still need to do this from the LiveCD.

If you have any questions, feel free to ask.

---

### Post by TheStroj on 2010-08-20
Windows rewrote GRUB and used it's own loader and ofcourse it can't find your Ubuntu partition because it's not FAT/NTFS. Reinstalling grub will fix it :)

---

### Post by 2uk_ on 2010-08-20
Alright I've just gone and deleted the Windows partition, 
and now the computer wont boot...
It says 'Operating System Not Found'

I'm on the live CD right now...
Is there a way to repair whats already there? Because it does show up on the partition tool thing..

I dont fancy doing a clean install

---

### Post by Rubi1200 on 2010-08-20
> **2uk_ said:**
> Alright I've just gone and deleted the Windows partition, 
and now the computer wont boot...
It says 'Operating System Not Found'

I'm on the live CD right now...
Is there a way to repair whats already there? Because it does show up on the partition tool thing..

I dont fancy doing a clean install
I don't understand why you deleted Windows (unless you have changed your mind and don't want it now)?

The method I linked to would have allowed you to have **both** operating systems!

As long as you did not make any changes to the Ubuntu partition, you are STILL going to have to use the method I gave you.

But, before you proceed, take a screenshot of the partitions in GParted (System > Administration > GParted) and post it here; just to make sure.

:-)

---

### Post by 2uk_ on 2010-08-20
Yeah I basically decided it was more hassel than it's worth
Now i've given myself even more hassel :')

How stupid of me

---

### Post by Rubi1200 on 2010-08-20
> **2uk_ said:**
> Yeah I basically decided it was more hassel than it's worth
Now i've given myself even more hassel :')

How stupid of me
We all make mistakes and that is how we learn. Hopefully, you won't make the same mistake again.

To reassure you, the method I linked to is not complicated. Just follow the instructions and you will be fine.

:-)

---

### Post by bcbc on 2010-08-20
If you just deleted the windows partition, and didn't reuse it, you can probably get it back with 'testdisk'.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can install testdisk while running the live CD with:

```
sudo apt-get install testdisk
```

and run it with 

```
sudo testdisk
```

---

### Post by theozzlives on 2010-08-20
People tell you how to fix your MBR and instead you delete Windows?! Re-install Windows and follow the instructions given you. It's not hard and you'll have the best of both worlds. Microsoft just looks at Linux as a threat and therefore don't recognize it.

---

### Post by 2uk_ on 2010-08-20
> **Rubi1200 said:**
> We all make mistakes and that is how we learn. Hopefully, you won't make the same mistake again.

To reassure you, the method I linked to is not complicated. Just follow the instructions and you will be fine.

:-)

Thanks, your link solved it pretty much

The most simple code on the page too as it turns out :')
'
'grub-install -v'
At least I think thats what solved it :')

Im gonna try partitioning again tomorow

---

### Post by 2uk_ on 2010-08-21
Sorry for keeping this going...
But i've redone everything, now i have a windows partition and a linux partition
I've reinstalled grub and everything

Now it just boots straight to the linux partition >.<
Any help pleaaase?

---

### Post by 2uk_ on 2010-08-21
It's working :D
If anyone has this problem in the future and finds this thread, the codes were ;;

```
sudo os-prober

sudo update-grub
```

---


---
title: "question about specifying location of /home directory during install from live CD"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-06-26
Hi Ubuntu Community:

When installing Ubuntu from a live CD, is there a way of indicating that the /home directory should be on another partition or hard disk?

I forgot. Thanks for your help.

Phil Smith
Duluth, GA

---

### Post by jtarin on 2011-06-26
When it comes to the partitioning part select Manual or Custom (I can't remember what it's called) and just specify what partition your /home is and to mount it as /home. Then specify your / and swap partitions accordingly. You do want to check the Format box for / and /home if you're doing a **_new_** install though.

---

### Post by nick_goodfate on 2011-06-26
> **jtarin said:**
> You do want to check the Format box for / and /home if you're doing a fresh install though.

I think formating the /home partition isn't necessary. After all that's the reason you make a separate home partition, so you don't have to lose your settings after a fresh install.

---

### Post by jtarin on 2011-06-26
I should have noted...this was on a "new" ,never been installed, (fresh) install....as I thought that was what the OP's question was. If you never formatted the partition then I would suggest to do so at this time.

---

### Post by 73ckn797 on 2011-06-26
> **nick_goodfate said:**
> I think formating the /home partition isn't necessary. After all that's the reason you make a separate home partition, so you don't have to lose your settings after a fresh install.
Formatting the already existing /home will wipe out any data in the partition. On a fresh install where you do not have any pre-existing /home, formatting will, in a sense, freshen the partition to receive data. Any later update to another release and you would not format the /home partition but still designate it again as /home without formatting.

---

### Post by nick_goodfate on 2011-06-26
> **jtarin said:**
> I should have noted...this was on a "new" ,never been installed, (fresh) install....as I thought that was what the OP's question was. If you never formatted the partition then I would suggest to do so at this time.

of course, my mistake. Ignore me OP... :)

---

### Post by Old Jimma on 2011-06-26
Thanks for your replies from Greece and Vladivostok!

I've got 2 drives: at 250GB drive where I want the OS and swap, and a 500GB drive where I want home.

I'll do a custom install and specify where / will be and swap on the 250 GB drive.

Also, I'll specify the logical device (ie the 500GB drive) where I want /home to be.

Since it is a brand new install I'll check Format for both.

When I upgrade, I will format the partition where / will be... but will not format where /home is.

Is this correct?

Thanks!
Phil de Duluthistan, GA

---

### Post by nzjethro on 2011-06-26
That is correct. Although how are you planning to upgrade? If it will be a "clean install" (i.e. you will download the latest .iso and install it) then yes, you will format /. Otherwile, you can just upgrade overtop, without formatting /.

---

### Post by 73ckn797 on 2011-06-26
> **nzjethro said:**
> That is correct. Although how are you planning to upgrade? If it will be a "clean install" (i.e. you will download the latest .iso and install it) then yes, you will format /. Otherwile, you can just upgrade overtop, without formatting /.
As any browsing of the forums will reveal, an upgrade can be problematic, though that is not always the case. I prefer a fresh install. The re-installation of the added programs you may have added after the last install is really not a consuming task. The /home partition will still be there to make the changes go smoothly. For example, when restarting Firefox or Libre Office, all of your previous settings, bookmarks, passwords and other stuff will automatically be there and you can continue on without a hitch.

BTW: Hello Duluth. I am in Newnan.

---

### Post by jtarin on 2011-06-26
> **73ckn797 said:**
> 
BTW: Hello Duluth. I am in Newnan.Heck! We got the whole state of Georgia on Ubuntu!:P

---

### Post by nzjethro on 2011-06-27
> **73ckn797 said:**
> As any browsing of the forums will reveal, an upgrade can be problematic, though that is not always the case. I prefer a fresh install.

I agree, and I encourage others to do the same. Easier to avoid issues, and you get a nice clean system! :)

---

### Post by Old Jimma on 2011-06-27
Many thanks to all who contributed to this important thread! I feel that it will benefit many Ubuntu users now and in the future.

Sincerely,
Phil Smith de Duluthistan, GA


ps. Georgia's motto is "Non sibi sed alis." This means: "Not for ourselves but others." I feel that our motto fits in well with the Ubuntu's community. I will marked this thread as solved so as to alert other forum seekers to this solution.

:P

---

### Post by 73ckn797 on 2011-06-27
> **jtarin said:**
> Heck! We got the whole state of Georgia on Ubuntu!:P
Gaining ground one person at a time.

---


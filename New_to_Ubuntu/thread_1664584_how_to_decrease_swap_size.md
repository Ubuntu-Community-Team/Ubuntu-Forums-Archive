---
title: "how to decrease swap size?"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by adeee on 2011-01-11
hay guys i am using ubuntu in wubi.
yesterday i increase the swap size via this thread.  [http://ubuntuforums.org/showthread.php?t=89782](http://ubuntuforums.org/showthread.php?t=89782)

before increasing its size 256 mb.
unfortunately i increase it to 3 gb. i want to increase it only 1gb..
my wubi  size is only 10 gb. now i have low space,..
tell me how to decrease it to one gb. 
i currently work only 256mb.
if i put this line in this file 
/etc/fstab 

/swap_file       none            swap    sw              0       0
then my swap file size go 3 gb. help me to reduse it only 1 gb. plzz:(

---

### Post by adeee on 2011-01-11
guys reply.

---

### Post by Paqman on 2011-01-11
Just to get this straight: you created a swap file using the instructions in post #3 on that thread?

If so, just repeat the instructions with the correct size of the file you want to create.

> **adeee said:**
> guys reply.

People here are happy to help, but we are just volunteers. Bumping your thread after only one hour is considered a little pushy.

---

### Post by bcbc on 2011-01-11
You created the swap file within the wubi virtual disk. So you're using your loop device as swap. This is not efficient. You should follow the wubi guide and create a swap file outside of the virtual disk.

Just "rm" the /swap_file you created to free up space. (first "sudo swapoff -a")

Then use the instructions from the [wubiguide]("https://wiki.ubuntu.com/WubiGuide#How do I increase my swap space?")

You'll need to change your /etc/fstab back to what it was afterwards as well:
> /host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by adeee on 2011-01-11
thank you bcbc. i follow your instructions. 
its works well done. i

---


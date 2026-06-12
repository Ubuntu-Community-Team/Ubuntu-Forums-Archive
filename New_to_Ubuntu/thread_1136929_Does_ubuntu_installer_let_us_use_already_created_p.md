---
title: "Does ubuntu installer let us use already created partition for /home and /opt?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by legolas_w on 2009-04-25
Hi
Thank you for reading my post.
I have a partition which contains a folder named *legolas* and I want to install new version of ubuntu and then use that partition as my /home to ensure that all my settings are reserved.

Does ubuntu 9.04 installer allows me to determine which partitions I want to mount as /home and /opt?

If it allows, Now that a directory named legolas exists in the /home path, does new installation allows me to create legolas and use those settings automatically or not?

Thanks

---

### Post by llamabr on 2009-04-25
You are able to mount any directory to any partition you like.

The installer comes with a custom partition editor, which is where you'll do this.

---

### Post by legolas_w on 2009-04-25
Hi, 
Thanks for the reply.

What about already created folders in /home mount point?
I have a user folder in that partition, does it allows me to use that folder for my newly created user or it will overwrite that folder or...?

Thanks.

---

### Post by legolas_w on 2009-04-26
> **legolas_w said:**
> Hi, 
Thanks for the reply.

What about already created folders in /home mount point?
I have a user folder in that partition, does it allows me to use that folder for my newly created user or it will overwrite that folder or...?

Thanks.

Comments are welcome.

---

### Post by adult swim on 2009-04-26
whenever you are installing, choose the manual option in the paritioning section and that will bring up a screen where you can select how you want your partitions set up.  go to the ones for /home and /opt and double click them.  then make the mountpoints /home and /opt.  make sure that you dont check the box for them to be formatted as you will lose  your data.  youll also have to choose the partition for / and one for swap since you are going the manual method.

---

### Post by legolas_w on 2009-04-26
Hi
My biggest concern is whether ubuntu will use my current user directory which exists in the home partition or not. If yes, how I can tell ubuntu installer that when I create a user named legolas I want it to use my old /home/legolas directory as its home directory.

thanks.

---


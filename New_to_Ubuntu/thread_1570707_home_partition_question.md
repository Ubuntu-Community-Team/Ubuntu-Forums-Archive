---
title: "/home partition question"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Kaperww on 2010-09-08
[B]Hello.

[/B]I've currently installed Fedora and Ubuntu on my laptop, and I was wondering if it was possible to mount my /home partition that I've got in Fedora in my /home in ubuntu?
If so, should I just mark the partition within the install as a /home partition, or should I do something else?

Thanks in advance

Kasper

---

### Post by andrewthomas on 2010-09-08
Not a good idea

---

### Post by JKyleOKC on 2010-09-08
To elaborate on why it's not a good idea:

Linux file systems identify file owners not by name but by the user ID number (UID) corresponding to the name. The number can be stored in just two bytes while names need more and the number needed would vary with the name. "Rumplestiltskin" would need lots more space than "me" for instance. Most distributions use low numbers for system users such as "root" and have some cutoff number where regular user UIDs start. For all of the *ubuntu versions the users start at UID 1000, while most Red Hat descendants (and Fedora is one) start at 500. If you tried to make your home directory from one of them work with the other, you could be the owner in only one of them, and the other would then simply not work properly!

I actually ran into this while migrating from a very old version of Mandriva to Xubuntu several years ago. I backed up my home directory on CD and then tried to re-use parts of it by copying them over. Until I used "sudo chown" to change ownership of the files from the CD, I could not use them. They were still owned by UID 500, which did not exist on the Xubuntu system.

---

### Post by marshmallow1304 on 2010-09-08
This can be done if you use a different username on each distribution so that the /home/<user>s are not mixed.

---

### Post by cotcot on 2010-09-08
Keep the home partition separate. The home partition contains configuration files of your applications. The applications might be different versions for different distros. This could lead to surprises.

---

### Post by bodhi.zazen on 2010-09-08
> **marshmallow1304 said:**
> This can be done if you use a different username on each distribution so that the /home/<user>s are not mixed.

This ^^

I advise you keep a /data partition.

If you use a /home partition I advise you use a unique user name for each installation / distro.

---

### Post by CaptainMark on 2010-09-08
if you wanted just to share your files and folders and like most people you have about 5 or 6 main folders in your home folder then you could just symbolic link the folders from one home folder to the other,  this way the distros have seperate home folders but your files would be the same when you boot into either.

---

### Post by bodhi.zazen on 2010-09-08
> **CaptainMark said:**
> if you wanted just to share your files and folders and like most people you have about 5 or 6 main folders in your home folder then you could just symbolic link the folders from one home folder to the other,  this way the distros have seperate home folders but your files would be the same when you boot into either.

ln -s /data/Documents $HOME/Documents

=)

---

### Post by Kaperww on 2010-09-09
Thanks alot for the responses.

I'll just stick with the /data partition.

---


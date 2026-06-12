---
title: "How do I backup from live CD"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by fishman78 on 2009-02-02
Hi There,

   I found out my Linux install is completely messed up.  So I need to re-install.  I am trying to backup all my file to an ext HDD but I keep getting permission errors.  Is there a command where I can just copy everything to an external HDD and then restore what I need on the new install without the permission problems.  I am most concerned with my VirtualBox Image.  Thanks!!

fishman78

---

### Post by handydan918 on 2009-02-02
might help if you posted the commands you're trying with the errors you're getting in return....

---

### Post by evildragon2 on 2009-02-02
First tell us where the hard drive is and where the files you want to copy are. Do

```
mount
```

And tell us the result. 

As for the command to copy, its structure is like this:

```
sudo cp /where/files/are /where/external/hdd/is
```

---


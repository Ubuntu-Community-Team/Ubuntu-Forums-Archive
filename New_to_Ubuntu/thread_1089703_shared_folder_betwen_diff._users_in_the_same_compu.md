---
title: "shared folder betwen diff. users in the same computer?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by nmtservice on 2009-03-07
Is there any easy way to create a common file repository (as a local folder in the local filesystem) allowing different users to write and read on it?

---

### Post by albandy on 2009-03-07
Yes, simply create the folder and set the right permisions, for example:

sudo mkdir /usr/local/sharedfolder
sudo chmod 777 /usr/local/sharedfolder

Now all users can write, execute and read in sharedfolder

or add users to a special group:
sudo groupadd sharedfolders
sudo adduser user1 sharedfolders
sudo adduser user2 sharedfolders
sudo adduser user3 sharedfolders

sudo chown root.sharedfolders /usr/local/sharedfolder
sudo chmod 775 /usr/local/sharedfolder

now all users of sharedfolders group can do anything in sharedfolder and the rest only can read and execute

---

### Post by arsenic23 on 2009-03-07
I normally just make a new folder in the /home/ directory with full access rights for everyone and then symlink it into their home directories.

---

### Post by nmtservice on 2009-03-07
Thanks a lot, guys!
I've take Albandy aproach (using a group), and it worked nicely. ¡Gracias!

---


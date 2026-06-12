---
title: "password protection for folders"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by albert s on 2010-01-23
Hi, is there an easy way to password protect some of my folders.?
I want to ensure some of my folders are not just click and see, nothing sinister in them, but need to make sure no one goes into them and messes about with my files.
tax returns , invoices etc for work and I need to keep them reasonably secure, as my nephew uses this PC on occasion if he is over visiting.
thanks.

---

### Post by Paddy Landau on 2010-01-23
If you use Karmic, you can take advantage of encrypted folders. Easy to set up when you first install, but really complicated to add it on later.

Otherwise, take a look at the superb [TrueCrypt]("http://www.truecrypt.org/"). You can create a file that becomes a virtual hard drive, or you can encrypt an entire partition.

Just be sure to take proper backups! If something goes wrong, then without backups your data is unrecoverable!

---

### Post by mcduck on 2010-01-23
The easiest way to set up encrypted directories in Gnome (apart from enabling the encrypted home during install) is to install Cryptkeeper. It's *really* simple & easy way to create and manage encrypted directories. And of course you'll find it in the repositories... :)

---

### Post by nothingspecial on 2010-01-23
Make a guest account with no admin rights for your nephew, then change the permissions on your private files to 600 

```
chmod 600 vat_return.txt
```

Only your account will then be able to see it, change it, delete it etc.

---

### Post by albert s on 2010-01-23
> **nothingspecial said:**
> Make a guest account with no admin rights for your nephew, then change the permissions on your private files to 600 

```
chmod 600 vat_return.txt
```Only your account will then be able to see it, change it, delete it etc.


excellent, I knew there had to be a simple way,
just create another user account and deny access to whatever files I need to keep safe.
thanks a bunch guys,   :D

---

### Post by PenguinInside on 2010-01-24
For setting permissions, you can also right click on a folder in Nautilus to get to Properties > Permissions > Others. Set to None.

Be sure to click "Apply Permissions to Enclosed Files".

---

### Post by J V on 2010-01-24
> **albert s said:**
> excellent, I knew there had to be a simple way,
just create another user account and deny access to whatever files I need to keep safe.
thanks a bunch guys,   :DDon't get your hopes up, that won't stop anyone with a live disc accessing your data...

Install ecryptfs-utils or encrypt your home if you want a really secure folder (I suppose you could also compress with a password if you wanted and didn't need to edit too often)

---


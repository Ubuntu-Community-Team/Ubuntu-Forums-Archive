---
title: "HELP...Please...Need to Recover Files From Corrupt Install"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by pv74 on 2010-08-01
Hello, 

I was running Ubuntu 9.x, and then it became corrupted and I cannot get it to boot properly. 

I am using a Ubuntu 10.04 CD running in live mode to recover my files onto a compact flash drive. 

The only problem I have is the file permissions on the hard drive that I am trying to recover my files from...I cannot change them so that I can view them or even copy them to the flash drive. I can see them, but that's it....can't view or copy them...

How do I go about doing this?

Thanks, 

Phill

---

### Post by hansdown on 2010-08-01
Welcome to the forum, pv74.

Running the live CD, click applications> accessories> terminal.

Enter

```
gksudo nautilus
```

Hit enter.

You should be able to drag and drop your files to a USB thumb drive.

If not, right click a file, and click properties> permissions.

You can change the permissions to "read and write".

---

### Post by pv74 on 2010-08-01
> **hansdown said:**
> Welcome to the forum, pv74.

Running the live CD, click applications> accessories> terminal.

Enter

```
gksudo nautilus
```Hit enter.

You should be able to drag and drop your files to a USB thumb drive.

If not, right click a file, and click properties> permissions.

You can change the permissions to "read and write".


Thanks!

Worked like a charm!!!

---

### Post by hansdown on 2010-08-01
Glad you fixed it, pv74.

---


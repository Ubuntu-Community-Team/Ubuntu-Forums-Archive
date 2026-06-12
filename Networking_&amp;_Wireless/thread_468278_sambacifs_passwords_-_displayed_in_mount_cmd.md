---
title: "samba/cifs passwords - displayed in mount cmd"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by crisponions on 2007-06-08
I have a little script I run to mount my various windows shares to my feisty box, and everything works great.

Today I was adding a new partition and entered the mount command to do some checking and noticed that my password I pass in to 'mount - t cifs' is shown in clear text in the mount listing.  Is this normal??

the command I use to mount is:

mount -t cifs -o username=user,password=pass //server/share /ubuntu/dir

---

### Post by dmizer on 2007-06-08
to prevent your password from being sent in clear text, you have to use a credentials file.  check the second link in my sig for information on how to create and use one.

---


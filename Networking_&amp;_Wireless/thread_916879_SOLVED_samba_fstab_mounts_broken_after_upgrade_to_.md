---
title: "SOLVED: samba fstab mounts broken after upgrade to Hardy"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by sabhain on 2008-09-11
Hello all,

I recently upgraded a system from Gutsy to Hardy and it went smoothly.  One persistent problem that I was having was a samba share in /etc/fstab was not being mounted at boot.

When I attempted to "mount /media/SHARE/" I got the following error:

[B][I]mount error 22 = Invalid argument
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/I][/B]

Now if I used mount with arguments and all the test methods found here and elsewhere .. it mounted fine.  But no matter what I did, I could not mount using the arguments specified in /etc/fstab.  I have had the same fstab for a long time & even with some small changes in options to reflect the move from smbfs to cifs, it would not work.

Today I tracked it down.  I'm using a credentials file for the authorizations so that the username & password are not contained in fstab.

Apparently, the mount.cifs app looks for a slightly different structure in the credentials file than previously with smbmount  (or whatever it was in Gutsy & before):

My initial file from older installations (even back to Mandrake(iva)) had the following format:

```

username = <user>
domain =
password = <password>

```

In order for the upgraded system to work, I had to make this file look like this:

```

user = <user>
password = <password>

```

It's a very subtle change, but it was enough to prevent mounting if it hadn't been made.

I still haven't found this in documentation or explanations on the samba to cifs move .. but it sure was a pain in the tail.  For all I know the credentials file format shifted a long time ago & the old style still worked until the last upgrade.

I hope this helps anyone else having the issue.

---

### Post by lacis_alfredo on 2008-12-26
moved to new post

---


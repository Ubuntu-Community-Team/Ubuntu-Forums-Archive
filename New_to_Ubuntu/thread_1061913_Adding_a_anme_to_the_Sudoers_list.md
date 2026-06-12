---
title: "Adding a anme to the Sudoers list"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Chris62 on 2009-02-06
Hi,

I have just installed Fedora version 10 into a USB memory stick so that when I am using someone else's computer I can boot into Fedora using the memory stick.

I want to edit a file that is used by Firefox and when I started a terminal and typed 'sudo gedit' I got a message saying that my user name is not on the sudoers list. How can I put my name on the sudoers list?

When I first booted using the memory stick it booted automatically as 'LiveUser' and I have (almost certainly) made the mistake of deleting 'LiveUser' and putting my own user name in its place; 'LiveUser' may have had administrator rights.

Can anyone help with this, please?

---

### Post by superprash2003 on 2009-02-06
you just need to use your root password!! there is a default root account like an administrator account in windows..

---

### Post by Hospadar on 2009-02-06
Typically (at least in ubuntu, I really know nothing of fedora on this matter) individual users arn't added to the sudo list, but rather added to the "admin" group, which in turn is actually on the sudo list.

If you look at ubuntu, you'll find in the sudoers file that only the admin group is listed in the file, not any individual users.

It's a little easier and more secure this way

---

### Post by Chris62 on 2009-02-06
Thanks to both of you. Unfortunately I do not know enough about Linux, Hospadar, to know how to get at the sudoers file.

The only password that I have,superprash2003,is my user password and that isn't my root password. When I set up the memory stick I wasn't asked for a password as one is when setting up on a hard drive.

It seems that I am in some sort of loop; I can't give my username Admin privileges because I need to be an admin to do it and there doesn't appear to be an admin on the memory stick.

---


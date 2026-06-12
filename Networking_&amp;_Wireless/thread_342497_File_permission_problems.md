---
title: "File permission problems"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by wro on 2007-01-20
I am trying to get the file permissions set up on a Buffalo 320GB Linkstation Pro.

I have typed the following in terminal:

sudo smbmount //ipaddress/buffalo /media/buffalo -o fmask=0744,dmask=0775,uid=mylinuxusername,gid=buffalo

where uid is the name I log onto ubuntu

gid, called "buffalo" has two users in it, me included.

I thought that the above fmask and dmask commands should give me rwx to everything - which they do.

Anyone in gid to be able to create, delete directories etc, but to only have read only permissions to files.

When I log in as the other user in gid, I can go into a file, change it, and re-save it!  Even though if I look at the permissions it says Group - read only.

Also, if I go in as "other", someone who isn't in the group, they can view directories , but can't create or delete - as i would expect, BUT they too can go in and change and re-save a file!

What am I doing wrong? 

Any ideas, please?

---


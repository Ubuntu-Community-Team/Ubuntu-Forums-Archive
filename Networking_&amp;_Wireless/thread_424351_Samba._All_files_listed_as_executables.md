---
title: "Samba. All files listed as executables"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by ralphz on 2007-04-26
HI

I successfully configured samba shares but i have problem with permissions and line breaks.

If i mount the samba share on my other Linux system using:

mount -t smbfs //192.168.11.1/www /mnt/www -o username=xxx,password=xxx,uid=xxx,gid=xxx

all the files have executable permission set up on them. How can I change this except changing the permissions with chmod (all the files are created by user on Windows machine)?

The other problem is all the files have Windows line breaks.  What is the best way to solve line breaks keeping in mind that both Linux and windows machines will be using those shares?

Ralph
Thank You

---


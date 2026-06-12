---
title: "Unable to write to /mnt/lv1"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by technopagan on 2011-05-29
Hello,
I have a lvm that's been created in /mnt/lv1 that was setup with a friends help and earlier today wrote fine (via Samba over the network from my Windows box as well.)
After he helped me finish setting some things up I changed the userid's password.
I then also changed smbpassword to match. 
Then rebooted.

I'm unable to write now over the network, and I'm also unable to write to the directory /mnt/lv1 unless I sudo (and I'm not sure if this is correct.)

```
$ ls -l /mnt/
total 0
drwxr-xr-x 2 root root 16 2011-05-29 00:58 lv1

```Can anyone offer any insight as to what i might be doing wrong? Thank you.

---

### Post by yeats on 2011-05-30
Can you paste in the output of:

```
mount
```?

It's probably mounted read only.

---


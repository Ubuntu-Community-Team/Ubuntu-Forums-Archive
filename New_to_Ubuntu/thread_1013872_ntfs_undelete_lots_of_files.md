---
title: "ntfs undelete lots of files"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ylelkes on 2008-12-17
I understand how to undelete a single file at a time from a partition, but what is the command to undelete, lets say, thousands of files from one partititon to another?

thanks!

---

### Post by taurus on 2008-12-17
> **ylelkes said:**
> I understand how to undelete a single file at a time from a partition, **but what is the command to undelete, lets say, thousands of files from one partititon to another**?

thanks!

What do you mean undelete files from one partition to another?  Do you mean move a bunch of files from one partition to another?

---

### Post by ylelkes on 2008-12-17
> **taurus said:**
> What do you mean undelete files from one partition to another?  Do you mean move a bunch of files from one partition to another?

I mean a function such as: ntfsundelete /dev/sda1 -d ~

---

### Post by Hospadar on 2008-12-17
you could write yourself a bash script with all the filenames,
or try a wildcard - ntfsundelete /media/windows/*

---


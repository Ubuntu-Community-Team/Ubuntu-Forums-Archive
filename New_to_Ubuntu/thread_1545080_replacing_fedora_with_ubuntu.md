---
title: "replacing fedora with ubuntu?"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by grobar87 on 2010-08-03
Hi,
I have ubuntu lucid on my laptop,and fedora 13 on pc with separate home partiton.I want to know is ti possible to install ubuntu on my pc without formatting all hard disk,just to format /root partition with fedora on it?Home partiton will work on ubuntu?The file system is ext4.I ask this becouse i don't have external hard disk for my files and i want ubuntu on my pc. 
Thanks.

---

### Post by snowpine on 2010-08-03
Hi Grobar, if I understand your question correctly, you are asking if it is a good idea to install Ubuntu without backing up your data first? The answer of course is "no" and I strongly recommend buying/borrowing some kind of external media to back up your data.

Once you have a solid backup, yes, you should be able to install Ubuntu using the manual partitioning options to mount the existing partition as /home without formatting it. You should of course use a different username so that you are creating a new account, that way your Fedora config files won't mess with your Ubuntu settings. :)

---

### Post by grobar87 on 2010-08-03
Thanks snowpine.I will find a way to buckup my data first...:)
So if i understand correctly all linux distros can use same /home partiton,but with same file system?
For example if i want to install opensuse 11.3 on ubuntu lucid partiton (formating just /root partion)...everything will works fine...home partiton,swap partiton?

---

### Post by snowpine on 2010-08-03
> **grobar87 said:**
> Thanks snowpine.I will find a way to buckup my data first...:)
So if i understand correctly all linux distros can use same /home partiton,but with same file system?
For example if i want to install opensuse 11.3 on ubuntu lucid partiton (formating just /root partion)...everything will works fine...home partiton,swap partiton?

Yes, you can share the same /home partition between several distros, so long as you use different usernames for each (so the files are separate).

Another option is to use a separate partition that's just for data, then it never gets touched if you install/reinstall the operating system.

---

### Post by grobar87 on 2010-08-03
> **snowpine said:**
> Yes, you can share the same /home partition between several distros, so long as you use different usernames for each (so the files are separate).

Another option is to use a separate partition that's just for data, then it never gets touched if you install/reinstall the operating system.
Yes i like your opinion for separate partition just for data.
Thanks...things are much clearer for me now...and sorry for my bad english :p

---


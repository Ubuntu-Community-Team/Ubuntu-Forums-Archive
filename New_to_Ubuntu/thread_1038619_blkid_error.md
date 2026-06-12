---
title: "blkid error?????"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by alienexplorers on 2009-01-13
Why am I getting a "SEC_TYPE" command listed under /dev/sdb2:

> terminator@terminator-desktop:~$ sudo blkid
[sudo] password for terminator: 
/dev/sda1: LABEL="WINDOWS" UUID="4CA7-E543" TYPE="vfat" 
/dev/sdb1: UUID="f117c6ed-5497-4cfe-8333-7a531d64b98b" TYPE="ext3" 
[COLOR="Red"]/dev/sdb2: UUID="2d15cb8a-cdb2-42db-8a9d-c467fb2f36a6" TYPE="ext3" SEC_TYPE="ext2"[/COLOR] 
/dev/sdb3: TYPE="swap" UUID="0442cde4-9687-4f59-a6fb-cbf55812a724" 

---

### Post by drs305 on 2009-01-13
The 'SEC_TYPE="ext2" is a normal description. I've read it stands for 'Secondary Type' but can't confirm it. What I can say is that an ext3 filesystem can be mounted as ext2 without journaling. 

The only consistency I see on my machines is that if it's the first partition (sdX1) ext3 does not have the SEC_TYPE tag, while any subsequent partitions do.

It is an interesting point but not an error.

---

### Post by drs305 on 2009-01-13
With today's server problems I don't seem to be able to edit my previous post. I wanted to change the second paragraph to:

I haven't been able to find any consistency as to when the SEC_TYPE is listed in the blkid results (system/nonsystem, primary/logical, etc) but there must be some logic behind the blkid results.

It's still not an error in any case.

---

### Post by alienexplorers on 2009-01-14
drs305
Thanks for your help.  I just wanted to make sure my machine was not going to die on me because of some stupid message.  I will just ignore it.

Donald

---


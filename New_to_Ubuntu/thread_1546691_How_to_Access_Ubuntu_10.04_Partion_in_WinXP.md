---
title: "How to Access Ubuntu 10.04 Partion in WinXP?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by tanktan38 on 2010-08-05
How do I access my 10.04 partion in Windows XP? I have tried ext2fsd and ext2ifs, but when I try to open the drive in both, it tells me that I need to format them. And, if I go into properties, it says the there is 0 bytes free and 0 bytes used and that the filesystem is "RAW". Any suggestions?

---

### Post by pharcycle on 2010-08-05
What is the filesystem of the ubuntu partition you're trying to see in windows?

---

### Post by tanktan38 on 2010-08-05
> **pharcycle said:**
> What is the filesystem of the ubuntu partition you're trying to see in windows?
Maybe ext4, but i'm not sure.

---

### Post by RJ12 on 2010-08-05
> **tanktan38 said:**
> Maybe ext4, but i'm not sure.

I think that is the problem, I don't think those programs support EXT4

---

### Post by sandyd on 2010-08-05
by default, ubuntu 10.04 installs with a  ext4 filesystem, which is not supported in windows.

---

### Post by tanktan38 on 2010-08-05
So there's no possible way to? I heard on the websites of the programs that ext4 was supported, but only the features of ext2 are accessible.

---

### Post by Ocxic on 2010-08-05
there was a driver you could get that would allow you to read ext2/3 but it is not compatible with ext4 and in my experience sketchy at best.

---

### Post by Mi11z on 2010-08-05
> **carlee said:**
> by default, ubuntu 10.04 installs with a  ext4 filesystem, which is not supported in windows.

It's true unfortunately you will always be able to read your windows partition in linux but not vice-versa.

---


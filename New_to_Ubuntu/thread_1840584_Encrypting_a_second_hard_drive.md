---
title: "Encrypting a second hard drive"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by PreciousBodilyFluids on 2011-09-07
I've been using Ubuntu (I'm on 11.04) for a while with the encrypted home directory, and I'm happy with it. Now I've installed a second hard drive, and I'd like to encrypt it as well, but I'm having trouble figuring out how to do it. I've done some searching, but the suggestions I find all try to point me towards truecrypt - which I'm sure is a great program, but I want something as simple and transparently usable as possible, which I'm thinking will probably mean using ecryptfs like I already am for my home folder.

I've managed to format the drive as ext4 and assign ownership to my user. Can someone tell me what the simplest and lowest-maintenance way would be to encrypt this hard drive?

Thanks in advance!

---

### Post by bodhi.zazen on 2011-09-07
> **PreciousBodilyFluids said:**
> I've been using Ubuntu (I'm on 11.04) for a while with the encrypted home directory, and I'm happy with it. Now I've installed a second hard drive, and I'd like to encrypt it as well, but I'm having trouble figuring out how to do it. I've done some searching, but the suggestions I find all try to point me towards truecrypt - which I'm sure is a great program, but I want something as simple and transparently usable as possible, which I'm thinking will probably mean using ecryptfs like I already am for my home folder.

I've managed to format the drive as ext4 and assign ownership to my user. Can someone tell me what the simplest and lowest-maintenance way would be to encrypt this hard drive?

Thanks in advance!

I would use LUKS =)

[http://www.marclewis.com/2011/04/02/luks-encrypted-disks-under-ubuntu-1010/](http://www.marclewis.com/2011/04/02/luks-encrypted-disks-under-ubuntu-1010/)

---

### Post by terrykiwi83 on 2011-09-07
Truecrypt is pretty straight forward and has an easy to understand GUI. IMO its the best out there.

---


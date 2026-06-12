---
title: "Format hangs with TrueCrypt"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-27
Running Lucid 10.04...

I have a partition on an external USB drive that was formatted as ext3 under TrueCrypt.

Wanting to update to ext4, I thought that I'd follow the instructions given by several sites, such as [Config Blog]("http://www.configblog.com/2009/06/truecrypt-and-ext4/") and a [cryptography]("http://randomcryptography.blogspot.com/2009/03/truecrypt-and-ext4-full-disk-on-ubuntu.html") site.

However, I hit a problem. When I get to the format part:
```
sudo mkfs.ext4 -j -O extent -L 'Backups' /dev/mapper/truecrypt1
```The formatting starts, and within seconds gets to:
```
Writing inode tables:   60/2829
```Then the entire machine hangs. I have to do a hard power-down, as nothing responds.

I thought that it might be because I was running 64-bit, so I booted off a 32-bit Live CD, installed 32-bit TrueCrypt, and tried again, but with the same problem.

I have a workaround: I ran this on a different 32-bit computer, and it worked! :confused:

Any ideas how to diagnose and solve the problem on my machine?

---


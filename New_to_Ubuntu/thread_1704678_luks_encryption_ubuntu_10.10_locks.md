---
title: "luks encryption ubuntu 10.10 locks"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by kwalls8732 on 2011-03-11
I am not new to ubuntu, but I am not the most experienced person either.  I just recently rented a dedicated server and had Ubuntu 10.10 64bit version running.  I am trying to create a 100gb container using LUKS encryption.  I have ran this command (dd if=/dev/urandom of=container1 bs=1024 count=100000000) 3 times and each time it has locked my machine up.  It happens after about 20-30 minutes of the process running.

Machine specs:
Intel Quad Core 4x 2.4 GHz
4gb ram
1TB hard drive

there are 3 partitions 500m for /boot and 932GB for general use. and another small amount for something I can't rememeber.

Any suggestions or comments would be greatly appreciated on why this cause my server to freeze everytime.

---


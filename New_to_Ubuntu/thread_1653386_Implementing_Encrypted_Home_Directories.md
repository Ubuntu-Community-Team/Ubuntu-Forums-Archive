---
title: "Implementing Encrypted Home Directories"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-12-26
[http://www.linuxjournal.com/article/6481?page=0,0](http://www.linuxjournal.com/article/6481?page=0,0)

lance@bermudezl:~$ dd if=/dev/urandom of=ciphertext.img bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 288.519 s, 3.7 MB/s
lance@bermudezl:~$ losetup -e aes /dev/loop0 ciphertext.img
/dev/loop0: Permission denied
lance@bermudezl:~$ sudo losetup -e aes /dev/loop0 ciphertext.img
[sudo] password for lance: 
Password: 
ioctl: LOOP_SET_STATUS: Invalid argument
lance@bermudezl:~$ 

what did i do wrong? To get the ioctl: LOOP_SET_STATUS: Invalid argument?

---

### Post by lance bermudez on 2010-12-26
modprobe cryptoloop

---


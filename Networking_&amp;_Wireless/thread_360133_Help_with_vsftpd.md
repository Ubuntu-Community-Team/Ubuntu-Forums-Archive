---
title: "Help with vsftpd"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Edzio on 2007-02-12
This is my first post and I am a complete beginner with Linux and Ubuntu. I was able to set up vsftpd with a little help from my father-in-law, but I would like to customize it a little more for security purposes. I tried to access the vsftpd.conf.5 file for more options, but it doesn't seem to exist. I would like to limit users to see only their directory and not the entire system. Any help will be greatly appreciated.

---

### Post by Edzio on 2007-02-14
I found the answer to my problem. It was a matter of uncommenting the chroot_user_enable=YES line in the vsftpd.conf file. Pretty simple.

---


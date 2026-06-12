---
title: "available folder space"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by bs_one on 2010-08-09
Hi

I'm currently trying to set up Samba on my Ubuntu Server and I want to find out if the slow connection is because my externel harddrive (mounted at /myshare/extern) is connected via usb or because my lan connection is slow. So I mounted /dev/sda6 at /myshare/intern. It should be 6,5 GB big but on my Windows PC I can't see the size of the folder, but I can with /myshare/extern. So my question is: How can I find out the size of the folder /myshare/intern? I already tried "du" but that only shows me the used space, but I also want to know the free space.

Thanks in advance :)

---

### Post by jtarin on 2010-08-09
[use "df"]("http://en.wikipedia.org/wiki/Df_(Unix)")

---

### Post by bs_one on 2010-08-09
Thanks for the quick answer :)

I did that already. That's where I got the 6,5 GB from but I still can't understand why I can't see the size of the folder on my Windows machine :/

---

### Post by jtarin on 2010-08-09
Can you see the folder at all? Maybe you should repost with the topic heading of something like "Can't see Samba shared folder in Windows".

---


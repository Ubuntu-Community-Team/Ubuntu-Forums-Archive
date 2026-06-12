---
title: "Update manager error notice"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by hocvol1 on 2009-09-13
For the past two days I have been trying to do a manual update with the update manager and receive the following error message:

W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

What do I need to do to fix this?

Thanks!

---

### Post by NoaHall on 2009-09-13
You need to download and get the GPG key - as far as I can remember, if you use the deb to install Opera, I think it will install the GPG for you.

---

### Post by drs305 on 2009-09-13
Run this code to import the key. You can use the entire alphanumeric code in the error message or just the last 8 characters. I've used just the last 8.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9D1A0061
```

---

### Post by hocvol1 on 2009-09-13
Thanks for the quick reply and I will do as suggested.

Peace.

---

### Post by MelDJ on 2009-09-14
here's a video which shows how to install gpg keys in ubuntu: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)
hope it helps

---


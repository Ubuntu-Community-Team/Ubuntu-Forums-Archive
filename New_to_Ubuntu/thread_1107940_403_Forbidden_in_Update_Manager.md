---
title: "403 Forbidden in Update Manager"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by bamend on 2009-03-27
These packages won't update and I get the following message:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.1-1ubuntu5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.1-1ubuntu5_amd64.deb)
  403 Forbidden [IP:  80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.1-1ubuntu5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.1-1ubuntu5_amd64.deb)
  403 Forbidden [IP:  80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.1-1ubuntu5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.1-1ubuntu5_amd64.deb)
  403 Forbidden [IP:  80]

Any Help?

---

### Post by balaknair on 2009-03-27
Don't worry about it.
The most likely cause is that the Ubuntu devs have blocked the packages because they have discovered some error in it(maybe the updates are causing some machines to malfunction, and this was discovered soon after the updates were released). As soon as the problem is fixed, things will be back to normal.

---


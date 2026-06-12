---
title: "problem checking MD5 sum of diskimage"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by mlsmith45 on 2009-01-18
Hi I'm on a Mac OSX computer.  I am following the instructions on the help page.  it says to use disk utility and then open the "image" menu and then select check sum.  Then it instructs to choose MD5.  The only option I get is CRC-32 image checksum.  Have I downloaded the wrong version?  Or any other thoughts? 

thanks so much in advance

---

### Post by NewJack on 2009-01-18
You can try this automator action available for free: [http://www.apple.com/downloads/macosx/automator/md5checksum.html](http://www.apple.com/downloads/macosx/automator/md5checksum.html)

or 

1. Open a Terminal
2. Type: openssl md5 [nameofyourfile]

---


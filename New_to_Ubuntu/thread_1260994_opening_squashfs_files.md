---
title: "opening squashfs files"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by ave2 on 2009-09-08
I have a squashfs file, and from what I can gather it sounds like those are for some kind of compression... how do I open that up and view what it contains- I mean does it work like .rar or winzip files where you can just open it and take what you need?

---

### Post by uljanow on 2009-09-08
Checkout the file header (magic number). if it's a squashfs file, try mounting it as a loop device.

---

### Post by ave2 on 2009-09-08
thanks for the help, just for anyone else who may come across this, I used [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

and 

[http://tldp.org/HOWTO/SquashFS-HOWTO/creatingandusing.html#sqwrite](http://tldp.org/HOWTO/SquashFS-HOWTO/creatingandusing.html#sqwrite)

for info on how to do this

---


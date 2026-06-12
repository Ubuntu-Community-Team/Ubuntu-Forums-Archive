---
title: "dpkg error message"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by jtsc on 2009-01-28
Hello, I'm trying to install Open Office 3.0. I don't really understand what I'm doing. I executed the command

:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS$ sudo dpkg -i *.deb

which returned the error message 

dpkg: status database area is locked by another process

Is there something not working? I can't figure out what other process could be accessing that area.

---

### Post by brsmits on 2009-01-28
Do you have Add/Remove programs or Synaptic Package Manager running?
I think you have to turn those off.

---

### Post by jtsc on 2009-01-28
Thank you! That was it.

---

### Post by brsmits on 2009-01-28
took me about 6 days to figure that one out when I first switch to Ubuntu.

;)

---


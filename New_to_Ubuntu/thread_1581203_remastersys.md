---
title: "remastersys"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by ajaykumar.b on 2010-09-24
I would like to take the back up of my current installation.
when i use 'sudo remastersys backup custom.iso' it is trying to create including my /home partion data.
Can anyone help to make an iso without /home partion data.

Thanks in advance
Ajay

---

### Post by bodhi.zazen on 2010-09-24
use the "dist" option

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

I highly advise you read the documentation on remastersys. It works well, but if you do not understand the options you can get unexpected results and data loss.

I also advise you back up your data in /home as (in the past) remastersys would delete your user from your system, and then make an iso.

Bottom line, make backups of your data and do a little reading.

---


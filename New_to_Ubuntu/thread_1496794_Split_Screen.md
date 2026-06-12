---
title: "Split Screen"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Gavinthechop on 2010-05-29
Hi all

I have Linux Ubuntu installed on one of my laptops and Xubuntu on another and I'm loving it. My mate has a HP DV6000 AMD 64bit and I installed Ubuntu 9.10 32 bit on it. Everything was okay except that the wireless wouldn't function. We have since tried installing other distros yet they all result in display issues ie. the screen splits with repeated desktop options. An upgrade to the latest Ubuntu was attempted yet this has the same result! Seems that the only version to work is 9.10 but without wireless. Any ideas? Thanks.

---

### Post by Groodles on 2010-05-29
9.10 works, but 10.04 doesn't?

---

### Post by anewguy on 2010-05-29
Boot up using the LiveCD, then open a terminal window and post back the output of the following:

lspci 

lsusb

That way we can hopefully see both your video adapter and the wireless adapter so we can give you guidance (for example, your wireless probably just needs a driver installed - possibly the same for your video).

Dave ;)

---

### Post by Gavinthechop on 2010-05-30
Thanks. I'll get onto finding out what hardware it as. And... Yup, 9.10 works but not 10.04! Xubuntu also results in the same screen issues.

---


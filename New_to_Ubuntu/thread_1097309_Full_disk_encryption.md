---
title: "Full disk encryption"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by SteelCore on 2009-03-15
Does Ubuntu have a full disk encryption feature similar the [Bitlocker] technology in vista

---

### Post by blastus on 2009-03-15
Absolutely :) The Alternate CD (as opposed to the Desktop CD) enables you to setup full hard drive encryption using what's called dm-crypt. 

The significant difference is that dm-crypt doesn't use the TPM (Trusted Platform Module) chip like BitLocker so dm-crypt is portable (i.e. you can take an encrypted drive out of one machine and put it into another.)

I've used encryption in Ubuntu for a long time now and it works great. I use it on my entire system, additional hard drives, external hard drives, and USB keys. There's lots of tutorials on this. Here's one right here... [Installing Ubuntu 8.04 with full disk encryption](http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

---


---
title: "Hibernate in hardy"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by sumeshgupta on 2009-09-17
How can I make my PC hibernate in Ubuntu? Are there any additional packages required or the functionality is inbuilt in the kernel?
Any suggestions would be appreciable.
Thanx in advance.

---

### Post by seshomaru samma on 2009-09-17
Go thru [this]("http://ubuntuforums.org/showthread.php?p=2875529") thread - you will find the answer

---

### Post by mikechant on 2009-09-17
The thread referenced above might tell you more than you want to know. Basically, while 'suspend' can be problematic, 'hibernate' should work on all setups with no additional packages.
The only thing you need is a swap partition which is at least as big as your RAM.
If you're not sure about the size of your swap, run the Gparted utility and it should be obvious. Or open a terminal with ALT+F2 and run 'fdisk -l' 
(that's letter l not number 1!)

---


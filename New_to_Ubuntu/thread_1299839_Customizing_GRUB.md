---
title: "Customizing GRUB"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by cambunctious on 2009-10-24
I have my laptop setup to dual-boot Ubuntu and Windows XP.  When my computer starts, there are about six entries for Ubuntu with XP on the bottom.  Most of them say Ubuntu with a version and then a copy of it that says (recovery version).  Then one that says memtest.  Then Windows XP.  I only use the first one and XP.

Can someone explain what all of these entries are?  Can I remove some?  Rearrange them?  Make XP the default?

Thanks!

---

### Post by sisco311 on 2009-10-24
You can use startupmanager to set the default OS and change the number of kernels displayed.

Click [here]("apt://startupmanager") to install it. (apturl link)

---

### Post by cambunctious on 2009-10-24
> **sisco311 said:**
> You can use startupmanager to set the default OS and change the number of kernels displayed.

Click [here]("apt://startupmanager") to install it. (apturl link)
Thanks for the quick reply.  Great program!  I do have some questions still.  Can I and would it be safe to uninstall old kernels?  I have Ubuntu on a small partition.  Also, what is recovery mode and memtest?

---

### Post by sisco311 on 2009-10-24
> **cambunctious said:**
> Can I and would it be safe to uninstall old kernels?  

Yes it's safe to remove the **old** kernels. 

It's recommended to keep at least two working kernels, just in case an update breaks one.

> **cambunctious said:**
> 
Also, what is recovery mode and memtest?

Recovery Mode (a.k.a. Single User Mode) boots the computer in command line mode (root shell). 

[uwiki]RecoveryMode[/uwiki]

Memtest performs many different tests on your ram.

---

### Post by cambunctious on 2009-10-24
Cool.  That frees a lot of hd space!

---


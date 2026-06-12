---
title: "Tu remove and reinstall Kubuntu"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by Jsilva1254 on 2011-07-09
I need to remove and reinstall ubuntu. The HD is already partitioned. How do I remove the old ubuntu an reinstall a new one?

Thanks

---

### Post by Neoxhadowespio on 2011-07-09
For what reason do you wish to do that? Its just that maybe we can go through a lot less trouble if we know why it is.

---

### Post by Anders H on 2011-07-09
It depends on if you have just Kubuntu on the HD or Kubuntu and another Operating system. 

If its just Kubuntu then stick the live CD in and run the installer over the enter disk; done. 

However in a dual boot environment you will have to do things a little differently. 

The most pain free way of doing this is by using the installer on the live CD and select 
"manual partition" or some thing to that effect. (Sorry its been a bit since my last install) 
You are going to most likely be looking for the partition 

"hda5" and mark that as the install location using "hda6" as swap space. 

you can get your partition list by running 

```
fdisk -l
```in the terminal. 

Or if you are in a dual boot environment (windows 7 and Kubuntu on the same machine) you can delete the Kubuntu partition from the other operating system, but you will need to restore the MBR (master boot record) before you do any thing else, because GRUB is in the Kubuntu partition and without it your system can't boot properly. You will need a windows or Mac recovery CD and the steps are different for both.  

Hope this helped.

---


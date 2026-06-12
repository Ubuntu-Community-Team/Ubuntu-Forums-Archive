---
title: "Vista boot loader defualt boot loader"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-02
When I switch on my computer GRUB loads. How can I make Vista Boot Loader the default Boot Loader?

---

### Post by handydan918 on 2009-01-02
Why? 
While it is probably possible to make vista load another O/S, what would make you want to? Especially since grub is working!

Now, making Vista the default is different. That's easy. Is that all you want?

---

### Post by looi76 on 2009-01-02
I Triple Boot Vista, XP and Ubuntu. I want to have one boot screen and I think I can boot Ubuntu through Vista Boot Loader using EasyBCD. So, how can I make Vista Boot Loader the default boot loader?

---

### Post by handydan918 on 2009-01-02
> **looi76 said:**
> I Triple Boot Vista, XP and Ubuntu. I want to have one boot screen and I think I can boot Ubuntu through Vista Boot Loader using EasyBCD. So, how can I make Vista Boot Loader the default boot loader?
I guess you'd overwrite grub with ntloader and consult your EasyBCD documentation.

EDIT: That still doesn't explain the need to use the vista boot loader. Grub is quite capable of loading about any O/S ever built, and in huge quantities. I have multi-booted over a dozen O/S's on two different disks, and I know of installations of over 100 -all booted by grub. 

So again, why?

---

### Post by gn2 on 2009-01-02
You could probably do it with a [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

---

### Post by jamesrfla on 2009-01-02
The windows boot loader can't pick up Ubuntu. Only Microsoft operating systems unless you installed using Wubi.

---

### Post by looi76 on 2009-01-03
I can't Boot Windows XP from GRUB. So, when I switch on my computer first GRUB loads then I choose Vista Boot Loader then I can choose XP. Can I boot XP from GRUB? because I tired doing that by editing /boot/grub/menu.lst and that didn't work :(

---

### Post by Jay_Bee on 2009-01-03
Here is what I did, but I did it during the installation.
I had Vista installed and then I installed Ubuntu to it's own partition and placed GRUB _on that same partition_ (there is an advanced button in the installer that lets you set the partition.
I booted Vista and added Ubuntu using EasyBCD...
Now Vista's bootloader is the default one!
Then I set the delay on grub to 0, and that was it...

Maybe you could try something like that by overwriting GRUB with Vista bootloader and then reinstalling GRUB to Ubuntu's partition and add it to the list using EasyBCD. Just be very carefull because this could be tricky.

Check this out: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by egalvan on 2009-01-03
> **looi76 said:**
> Can I boot XP from GRUB? because I tired doing that by editing /boot/grub/menu.lst and that didn't work :(

Please post the contents of /boot/grub/menu.lst

We can go from there.

ErmestG

---


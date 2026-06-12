---
title: "adding Windows 7 to Grub menu"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by robotz421 on 2011-08-03
Hi everybody,

I have just installed Ubuntu 10.04 on a laptop intending it to dual boot with Windows 7.  The live CD I used came from a company that is bundling Ubuntu with their software.  After I ran the CD I discovered that there was no menu entry for Windows 7 when Grub ran.  I reinstalled several times trying to fix the problem but no luck.  I have read some of the Grub documentation and think I know approximately what to do but I want to know if I am right before I do it.  I know the Windows partitions are still on the HD.

As far as I can tell I need to add some text to the end of /etc/grub.d/40_custom that looks like this:

```


menuentry "Windows 7 (loader) (on /dev/sda2)" {    
    insmod ntfs    
    set root='(hd0,2)'    search --no-floppy --fs-uuid --set 6040b5fb40b5d7cc    
    chainloader +1 
}


```I copied this from my grub.cfg on a different machine.  I take it the long hex number there is a uuid so I think I need a different one for the laptop but I don't know much about uuid's.  Do I just make one up?

After changing 40_custom I would just run:

```
grub-mkconfig -o /boot/grub/grub.cfg

```Will this work or do I need to do something else instead?

---

### Post by jtarin on 2011-08-03
You just need to boot to the Ubuntu desktop open a terminal and enter ```
update-grub
```you should see the Window entry detected in the terminal. Reboot and it should be in the menu.
If this does not work see the link in my signature for Boot Script. Download and follow the instructions then post results here.

---

### Post by robotz421 on 2011-08-03
Woot!  That works.  Thank you very much.

---

### Post by jtarin on 2011-08-03
Mark the thread as solved if you would....it will help others in searches.

---


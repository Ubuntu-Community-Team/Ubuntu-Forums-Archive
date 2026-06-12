---
title: "Smoth Upgrade but why do I still &quot;load&quot; Intrepid"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Andavane on 2009-06-26
I was hugely impressed with the smooth upgrade path moving fro Intrepid to Jaunty, and thanks to all who do the work on this.

My only question is that at the grub stage I expected to see the 9.10, but I still selected 8.10, and it loaded as Jaunty.

I can explain that my main Ubuntu is Hardy, which I keep as it can be a bit fiddly installing the printer which I need for my work (which isn't computers), and there is another hard drive in the CD bay on which I have several Ubuntu's installed.

Regards

John

Typo; smoth = smooth

---

### Post by t0p on 2009-06-26
> **Andavane said:**
> I was hugely impressed with the smooth upgrade path moving fro Intrepid to Jaunty, and thanks to all who do the work on this.

My only question is that at the grub stage I expected to see the 9.10, but I still selected 8.10, and it loaded as Jaunty.


I guess you need to edit the grub menu by hand.  Odd, I would have expected the upgrade to do it for you...

---

### Post by Cheesemill on 2009-06-26
Try doing a:
```
 
sudo update-grub

```This may fix it.

---

### Post by Andavane on 2009-06-27
> **Cheesemill said:**
> Try doing a:
```
 
sudo update-grub

```This may fix it.
 Negative.
Grub is updated but still in the boot menu I only get the options to boot from 8.10, not 9.04, although the program ends up as Jaunty.

Incidentally I am getting the same result with the appropriate upgrade for my EeePC.

I am beginning to feel that this is what you get if you upgrade, as it's happened on two separate machines.

Regards

John

---

### Post by Faither on 2009-06-27
Hi there!

If you want adjust your Grub you'll have to edit your grub's > menu.lst file.

```
gksudo gedit /boot/grub/menu.lst
```

or 

```
kdesudo kate /boot/grub/menu.lst
```
(if you are using kde)

Scroll to the end of the file and edit the lines starting with > **title** to whatever you want to see next time you boot your system.

```
**title		Kubuntu 9.04**
uuid		UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx
kernel		/vmlinuz root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx ro quiet splash 
initrd		/initrd.img
quiet

```


Save the file and reboot to view your results ^^

Cheers Stefan

---


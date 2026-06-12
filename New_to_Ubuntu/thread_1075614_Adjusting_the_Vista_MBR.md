---
title: "Adjusting the Vista MBR"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Robert98374 on 2009-02-20
How would i go about adjusting the Vista MBR so i would be able to boot into my Ubuntu partition?

---

### Post by gn2 on 2009-02-20
When you install Ubuntu, Grub should be installed to the MBR and needs no modification.

---

### Post by Robert98374 on 2009-02-20
XP was having issues with getting my on board sound working so i went back to Vista but i am unsure how to adjust the boot loader there so it would include Ubuntu in the boot menu.

---

### Post by caljohnsmith on 2009-02-20
Is there any reason you don't want to use Grub in the MBR to boot all your OSes? That is usually easier than adding Grub to your Vista boot manager. If you want specific help, it would be good to get a clearer picture of your setup first, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by farsight on 2009-02-20
If you'd like to add ubuntu as an option during start up you could always install it via wubi if you do not wish to use GRUB. Alternatively you may find Supergrub a useful tool (see:[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)).

Regards,
Farsight:D

---

### Post by Robert98374 on 2009-02-21
I check that stuff out. Reading up on the super grub as i write this

---

### Post by Robert98374 on 2009-02-21
> **caljohnsmith said:**
> Is there any reason you don't want to use Grub in the MBR to boot all your OSes?

Its not that i dont want Grub to handle the booting, i am just not able to access my linux partition on windows at all. I tried the 
download from [http://www.fs-driver.org/](http://www.fs-driver.org/) but it doesn't seem to work.

---

### Post by caljohnsmith on 2009-02-21
I don't think that ext2ifs can handle the newer ext3 partitions, because Intrepid formats its ext3 partitions to now use a 256 byte inode size instead of 128 bytes which previous versions of Ubuntu used. So instead of using ext2ifs in Vista, I would give "ext2fsd" and try:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Let me know if that works OK or not.

---

### Post by Robert98374 on 2009-02-22
I am able to see the partition and able to see the individual files. So i assume that means that works :D

So now that i am able to see/adjust my ubuntu system from Vista would i be able to mess with the grub?

---


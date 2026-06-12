---
title: "boot XP with grub?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by erjoalgo on 2010-07-16
After repartitioning my drive, I have a windows XP partition that is not recognized by grub. I seem to have messed up the windows bootloader. At boot, grub only shows ubuntu as an option on the menu. However, when I plug in other hard drives, grub does recognize windows installations in those.
How can I fix the windows bootloader?
I have 3 partitions, ext3 (ubuntu), linux swap, then NTFS. 

I am wondering what components grub looks for in order to recognize a windows installation. There is a boot.ini file at the root of the NTFS partition, but that doesnt seem to be enough. Any ideas appreciated.

---

### Post by oldfred on 2010-07-16
Did that windows boot on its own? Windows combines all boots into one windows and you boot all versions of windows from that. Grub will only then work on booting windows from that one.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by erjoalgo on 2010-07-17
> **oldfred said:**
> Did that windows boot on its own? Windows combines all boots into one windows and you boot all versions of windows from that. Grub will only then work on booting windows from that one.
I think that is the problem, because that windows partition did not boot on its own. Although the windows installation files were there, I think grub "pointed" to another NTFS partition, which then pointed to the actual windows installation. 
The other NTFS partition was deleted.
I will try your links and I will try to use boot from a Windows XP CD to "repair" the boot loader, then I might have to reinstall grub to the MBR.
Thanks

---


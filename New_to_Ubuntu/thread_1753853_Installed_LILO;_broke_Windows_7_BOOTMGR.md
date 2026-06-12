---
title: "Installed LILO; broke Windows 7 BOOTMGR"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Redmage913 on 2011-05-09
Hey there,
 
I have a rather complicated problem with a probably simple solution.  I  used to have a tri-boot machine - my first primary partition was WinXP  Pro, second was a Xubuntu installation with swap on an extended  partition, and finally a Windows 7 Pro primary partition.
 
I deleted WinXP Pro and Xubuntu to create my very first Gentoo Linux  installation. While that went well, I accidentally broke my Windows 7  startup.  It's listed just fine under LILO (unless I listed it  improperly) but Windows 7's BOOTMGR is now missing.  I'm assuming the  BOOTMGR might have been part of the WinXP installation.
 
I went to this guide: [Bootmgr is missing - Fix]("http://www.sevenforums.com/tutorials/104341-bootmgr-missing-fix.html")
 
However, I don't want to replace the MBR and break LILO/Gentoo. I just want to reinstall the  BOOTMGR onto the Windows 7 Pro partition so I can boot both Gentoo and  Windows 7 properly.  Of course, I might be misinterpreting where the  BOOTMGR is normally located.
 
Any suggestions?
 
Thanks much,
--Red

---

### Post by jtarin on 2011-05-09
Look to my signature and investigate EasyBCD.

---

### Post by oldfred on 2011-05-09
So we can be sure what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Windows moves the boot files from the main install to the first install with the boot flag. Lilo also uses boot flag, but has its boot code in the partition boot sector. We often use the Lilo boot loader to repair windows booting but only install the boot loader. To repair the windows you will have to move boot flag to windows partition then move it back.
You may have to reinstall lilo's boot code, but that is also easy to fix, if windows overwrites it.

Do you have win7 repairCD?

Also this is Vista but 7 is the same and explains how windows (and all MBR partitioning schemes) boot.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Redmage913 on 2011-05-09
I'll give it a shot. Thanks!

---

### Post by Redmage913 on 2011-05-09
Came up with a different solution - I deleted my Gentoo installation cause I was having too many problems, installed a new Win7 in that space, copied over my files, then deleted the old Win7 and am now installing Lubuntu. From the live disc, it looks like fun!

Thanks for your input, though.

--Red

---


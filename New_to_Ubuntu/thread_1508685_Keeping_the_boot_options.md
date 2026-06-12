---
title: "Keeping the boot options"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-13
Hi, I have two hard drives in my computer, the first has Ubuntu lucid, the second drive also has Lucid and it's the second that I want to keep. The first drive has all the boot options on it. Now I want to install Windows on the first drive whilst not losing the boot option to boot into Lucid on the secondary drive.
Is it possible to keep the boot option in the first drive so it's not overwritten?

Hope that makes sense.

---

### Post by Diabolis on 2010-06-13
Install Windows in the first drive, it will overwrite the MBR, thats from where the options to boot many partitions/drives are found.

Then use a live cd to reinstall Grub and set again the menu that will allow you to choose from which drive you want to boot.

---

### Post by Primus1 on 2010-06-13
Thanks, the live CD is the Image I burnt when I downloaded Lucid right?  That will give me the option to just install this Grub and it will know where to go (MBR)?

---

### Post by Diabolis on 2010-06-13
Yes, thats the livecd and when you reinstall Grub it will know how to write to the MBR.

Reinstalling Grub can be a little tricky, but the web is full of step by step instructions, just read them thoroughly.

One of many guides: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Primus1 on 2010-06-13
Great, it will know that there is a Ubuntu on the secondary disk or I will need to input that information? I guess that is some of the hard part.

It's on:    /dev/sdb5
Hope that will be enough for Grub to make a link to it. Will check the link given, thanks.

Do you know if I have Grub2 on the live disk (Lucid)

---


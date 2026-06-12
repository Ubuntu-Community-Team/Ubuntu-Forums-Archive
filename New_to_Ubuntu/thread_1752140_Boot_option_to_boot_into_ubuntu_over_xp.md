---
title: "Boot option to boot into ubuntu over xp"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by derek13 on 2011-05-07
i have both xp and ubuntu installed on my hard drive.  i used to be given a dual boot option to select which os i would boot into.  now, after using xp for a day attempting to remove viruses, i do not get that option anymore.  windows appears to be default and ignores ubuntu.  

The question is, how can i get get that dual boot screen back so i can boot linux ubuntu again?

---

### Post by TeoBigusGeekus on 2011-05-07
You need to reinstall grub2. Here's a guide:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

---

### Post by rx007 on 2011-05-07
your antivirus software might have revert your mbr with windows xp bootloader. you can restore your ubuntu grub loader with this :)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by derek13 on 2011-05-07
Thanks for the quick reply.  I apologize, I'm a bit of a n00b, but i downloaded grub4dos and copied the file grldr.  Now it gives me teh directory of my hard drive for where i can copy it to.  How can I copy it to c:\.edit boot.ini?

---

### Post by oldfred on 2011-05-07
Were you using grub2dos? Most have grub2 now, a few have grub legacy left over from upgrades of old versions. And you may have wubi which boots with windows but needs a valid entry in XP's boot.ini.

If you are not sure post this so we can see exactly what you have. Use a liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---


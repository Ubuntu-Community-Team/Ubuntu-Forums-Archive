---
title: "Dual Boot - Need to Re-Install WinXP"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-10
Hi,

I've set up my hard drive so that I can Dual Boot.  WindowsXP is in the first partition and ubuntu in the 2nd.

If I Re-install WindowsXP into the First partition, is that going to affect my Linux installation?
Is the Dual Boot menu still going to be there?

thx

---

### Post by howefield on 2009-02-10
If you reinstall windows, the master boot record will be over written and you will only be able to boot windows, you will need to restore grub to get the choice of windows/ubuntu, pretty easy to do with the Live cd.

There are numerous threads in the forums on how to do this, do a search or do a search in your favourite search engine..

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by HermanAB on 2009-02-10
Dual booting is really old fashioned.  The 21st century way to run Windows is in VMware or Virtualbox.
;)

Cheers,

Herman

---

### Post by Gulyan on 2009-02-10
> **hermanab said:**
> dual booting is really old fashioned.  The 21st century way to run windows is in vmware or virtualbox.
;)

cheers,

herman

[-x[-x[-x

---

### Post by howefield on 2009-02-10
> **HermanAB said:**
> Dual booting is really old fashioned.  The 21st century way to run Windows is in VMware or Virtualbox.
;)

Cheers,

Herman

A great option, but not for everyone, :P

At least not until running windows as a vm is the same as running it as a "real" install. So for some, dual booting is very much a 21st century solution.

---

### Post by OffAxis on 2009-02-10
that first link provided
([http://www.howtogeek.com/howto/ubunt...-wipes-it-out/](http://www.howtogeek.com/howto/ubunt...-wipes-it-out/))
references the wrong partition for your setup.

Make sure you follow that second link
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

in particular the 

```
find /boot/grub/stage1
```

command to properly locate your stage 1.

---

### Post by prometheus1981 on 2009-02-10
> **howefield said:**
> If you reinstall windows, the master boot record will be over written and you will only be able to boot windows, you will need to restore grub to get the choice of windows/ubuntu, pretty easy to do with the Live cd.

There are numerous threads in the forums on how to do this, do a search or do a search in your favourite search engine..

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good point, however you can install XP first. All you have to do is modify the partition in the XP setup wizard, if you don't you will delete both partitions and install XP in your whole hard drive. I would also recommend you to do this using the Ubuntu installation since it's easier to use than XP.

---


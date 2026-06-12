---
title: "NeoSmart Bad Boot File"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by jobishia on 2009-07-22
I recently installed Ubuntu onto my computer, which already had Vista.  Everything is working swimmingly except that I want Vista to be the first boot option instead of Ubuntu.  A guide advised me to use the NeoSmart EasyBCD tool for this.  I was able to get everything configured, except I think I made an error in the menu.lst file.  When I try to load Ubuntu, it tells me that there is an incorrect file or directory.  I have to repair the original grub loader to get ubuntu to start again.  Here are the commands I currently have in place:

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ce4d51de-1884-47ee-9820-b0c265338158 ro quiet
splash
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

The original file that I copied from Ubuntu used a UUID in the root line.  I had to find the (hd0,4) manually.  I'm fairly confident that the problem is in the kernel line.  If someone could help me out, that would be splendid!

---

### Post by okey666 on 2009-07-22
I am not that experienced, but in the kernel line you have used a uuid. Shouldn't you use:
```
root=/dev/sda2
```
Or
```
root=/dev/hda2
```
Or an updated uuid.
I don't really know but that would be my guess as the uuid would be out of date

Also, this may just be the way it is formatted, but shouldn't splash be on the same line as quiet?

---

### Post by cariboo on 2009-07-22
If you made a backup of /boot/grub/menu.lst, before doing any editing, use it, then use [apt://startupmanager](apt://startupmanager) to set the boot order.

If you don't have the original menu.lst, use [this]("http://ubuntuforums.org/showthread.php?t=224351") howto to repair grub. Then use Startup-Manager to set the boot order.

---

### Post by Mark Phelps on 2009-07-22
Not an expert on easyBCD, but I believe that is used to manage the entries for the Vista Boot Loader, not for GRUB.  NeoSmart does have something called NeoGRUB, which may be GRUB after all, but it looks like you're mixing two boot loaders.  

The problem may be that NeoGRUB uses a different convention of identifying the drives and partitions than does GRUB, so changes made with one tool most probably won't work with the other loader.

---

### Post by jobishia on 2009-07-23
Thank you!  The non-canon Startup-Manager in Ubuntu was much simpler to use than manipulating neogrub from Vista, and my computer boots like I want it to now.  I just had to find and install the Startup-Manager first.

---


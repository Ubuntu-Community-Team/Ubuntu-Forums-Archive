---
title: "Booting's options"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by packpunk on 2010-05-31
Hi,
I'm PackPunk and I'm new here.
I got a problem here, I installed Ubuntu 10.04 (UNE) on my netbook, Lenovo S10-3 (This my first time to use Linux 8)).
I did a dual boot (Windows 7 and Ubuntu).
After I did some "upgraded" on Ubuntu now the options on booting became more than 4 options boot. Here is the screenshoot:
[IMG]http://img404.imageshack.us/img404/6500/rokr0043.jpg[/IMG]
You can see that there are "same" Linux's boot there.
- Ubuntu, with Linux 2.6...
- Ubuntu, with Linux 2.6... (recovery mode)
- Ubuntu, with Linux 2.6...
- Ubuntu, with Linux 2.6... (recovery mode)

I want to "remove" these double boot options? Any idea sir?
Or if there are some "configurations" I want to make the boot options only two:
- Ubuntu, with Linux 2.6...
- Windows 7 (loader)...

Thanks.

---

### Post by ajgreeny on 2010-05-31
From the grub2 wiki- [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
> **Removing Entries from Grub 2**

 Entries  should be removed by editing or removing files in the */etc/grub.d  folder*. The */boot/grub/grub.cfg* file is read-only and  should not normally be edited directly. 

[LIST]
[*]Automatically.  
[LIST]
[*]Kernels  removed by Synaptic will automatically update *grub.cfg* and no  user action is required.  
[*]Other operating systems which have been removed from  the computer will also be removed from the menu once "update-grub" is run as *root*. 
[/LIST]
[*]Manually. 
[LIST]
[*]To prevent a file in */etc/grub.d* from adding  items to the menu, remove the *executable* bit or remove the  applicable file. 
[*]***memtest86+***: If you don't want  to have *memtest86+* displayed in your menu, run sudo chmod -x /etc/grub.d/20_memtest86+. The file  will remain but will not be acted upon by *update-grub*.  
[*]***Recovery  mode:*** If you don't want *Recovery mode* entries  for your linux kernels, edit */etc/default/grub* and add this  line: 

[LIST]
[*]GRUB_DISABLE_LINUX_RECOVERY=true
[/LIST]
[*]If a custom script in the */etc/grub.d/* folder  contains multiple menu entries, individual items may be removed and  others retained. 
[*]Tip: If the user wants his custom entries to appear at  the top of the menu, the file can be named a value less than *"10_linux"*,  such as *"07_custom"*. Check that the *"DEFAULT"* value  in */etc/default/grub* points to the correct *menuentry*  after making this change. 
[*]Changes will not take effect on the Grub 2 menu until "update-grub" is run to update *grub.cfg*
[/LIST]
[/LIST]

So you see from this that you can remove almost anything you want, but I suggest you keep the two different kernel entries, ie, the first 4 menu entries, just in case something goes wrong and you need to run an older kernel.

Get rid of the memtest86+ lines if you want to, and the recovery mode as well if it annoys you, though I would keep recovery mode as it can be very useful if the system goes wrong (it can happen!).

As for the two windows entries, I can't help you.  Have you two different windows installs, or is one historical?  There have been changes to the way grub deals with the newer windows bootloaders, and I don't know how you can deal with that, so wait for other answers before trying to do anything about it.

---

### Post by nhasian on 2010-05-31
it doesn't harm your system in any way to have more than one kernel installed.  I recommend always keeping a backup kernel in case the updated one has any quirks or problems with your system you can fall back to the previous kernel.

---

### Post by packpunk on 2010-06-02
Ok thanks sir

---


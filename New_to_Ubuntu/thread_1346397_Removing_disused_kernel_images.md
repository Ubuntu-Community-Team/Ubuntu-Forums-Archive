---
title: "Removing disused kernel images"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by donescamillo on 2009-12-05
Hi,

I have both WinXP and Ubuntu (KK) installed. At first the GRUB boot manager showed two Ubuntu kernel images ver 14 (one normal and one recovery), two memtests and the WinXP entry. I downloaded the StartUp manager and set timeouts and preferred OS.
Now that I have updated my system several times images v 15 and v16 have been added. So I ended up with 9 (nine) entries in the boot list. I guess I can manually edit the file where all OSes and the boot sequence are but I would rather uninstall ver 14 and 15 of the kernel images. 
Is there a easy way to do it using a GUI tool or something?

regards
donescamillo

---

### Post by ubhi on 2009-12-05
[http://www.cyberciti.biz/tips/howto-change-grub-settings-with-guitools.html](http://www.cyberciti.biz/tips/howto-change-grub-settings-with-guitools.html)

either used above link for gui tool to edit grub boot loader 

or

you can edit the file below mentioned

/boot/grub/menu.lst


open terminal from application -> Accessories - > Terminal

vi /boot/grub/menu.lst

[do whatever u want]

---

### Post by PocketDog on 2009-12-05
Removing the kernels using Synaptic will remove the entries from your grub. Incidentally, the above grub edit won't work in Karmic, you have to run  ```
gksudo gedit /etc/default/grub
``` and then run ```
sudo update-grub
```

---

### Post by qyot27 on 2009-12-05
> **PocketDog said:**
> Removing the kernels using Synaptic will remove the entries from your grub.
This.  Actually, it worked this way for the legacy GRUB as well.

The easiest way is, after firing up Synaptic, search for the version string of the kernel, i.e. 2.6.31, and go through the list and use the Completely remove option on the minor entries you don't need.  I do that because I'm paranoid and always use that option in Synaptic or *sudo apt-get purge* when I uninstall things via the Terminal.

---

### Post by scared0o0rabbit on 2009-12-06
By synaptic I assume you mean the "Ubuntu Software Center" in 9.10?

I can't actually find the kernel in the list.  Is there somewhere else I should look?  When I open it up and click installed software and search by version number, it just doesn't show up.  What am I doing wrong?

---

### Post by PocketDog on 2009-12-06
System > Administration > Synaptic Package Manager

Search for **linux-image-generic-2.6.31**.
The installed versions are highlighted down the left side of the right-hand column with a tick. Click the tick, and choose 'mark for complete removal'. Click apply.

That should be that. On reboot, the old kernel(s) will be gone from grub.

---

### Post by scared0o0rabbit on 2009-12-06
Oh, duh.  Thanks!

So, to do this, do I want to remove basically everything that's 2.6.31-14 and 2.6.31-15, or only the headers or only the images or only some of the headers or some of the images?

---


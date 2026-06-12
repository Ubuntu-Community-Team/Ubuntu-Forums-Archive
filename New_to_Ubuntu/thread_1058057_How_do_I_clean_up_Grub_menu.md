---
title: "How do I clean up Grub menu"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2009-02-02
My grub menu is very long.  It probably has 15 updates to the Linux Kernel and then my dual boot to XP.  Can someone give me specifics on how to get it to the 1 or 2 Linux kernels plus the XP without messing anything up.

Thanks

---

### Post by Gulyan on 2009-02-02
first make a backup:

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

then open the /boot/grub/menu.lst.
```
sudo gedit /boot/grub/menu.lst
```

Scroll down until you find this line 
```
## ## End Default Options ##
```

To stop something from showing, comment the lines like this:
```

#title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
#uuid		d2f1f353-4776-478d-9c0c-0c4fea5fa853
#kernel		/boot/vmlinuz-2.6.27-11-generic #root=UUID=d2f1f353-4776-478d-9c0c-0c4fea5fa853 ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic
```

# means the line is ignored by grub

This will hide this option but the kernel version will still be installed.

Hope it works for you ;)

---

### Post by Elfy on 2009-02-02
You can edit the file to get rid of entries - but probably the best thing would be to use synaptic to earch for the kernels and just keep the 2 newest - the grub update will remove the old entries.

Search for linux-image and mark old kernels for complete removal.

If you just want to edit the file then to backuop and edit 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

You can also install startup manager which has a box to enter the number of kernels to keep.

---

### Post by stoogiebuncho on 2009-02-02
> **forestpixie said:**
> 
Search for linux-image and mark old kernels for complete removal.


Yes, that's what I do as well.  It's a good idea to keep one or two old kernels around just in case you have a problem with the new one, though.  So I don't recommend getting rid of all of them.

Also, don't forget to get rid of the headers, too.  In synaptic, do a search for linux-headers (again, don't remove all of them, just the oldest ones).

If you mark them for complete removal, you can also free up a fair bit of space while you're at it. ;)

---

### Post by drs305 on 2009-02-02
Here is a link to a tutorial on StartUp-Manager. It is a gui-based app that can limit how many kernels you see, set the default kernel or OS, change the menu timeout and much more. You don't need to manually edit grub's menu.lst - SUM will do it for you. 

The tutorial also discusses options on what to do with the older kernels and how to edit the file manually if you decide to do so.

[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---


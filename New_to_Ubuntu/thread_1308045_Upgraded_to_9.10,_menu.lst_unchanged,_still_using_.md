---
title: "Upgraded to 9.10, menu.lst unchanged, still using old kernel"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by occams_beard on 2009-10-31
I've just run the dist upgrade to karmic from jaunty. During the upgrade this box kept coming up asking me "What to do about menu.lst." It had several options. The default was to "leave menu.lst in place" or something like that, so that's what I went with. 

I probably shouldn't have though, because now when I restart grub is saying Ubuntu 2.6.28-14-generic (9.04).

I've tried running sudo update-grub, but it doesn't do anything. 

How can I rebuild menu.lst to use the proper kernel?

---

### Post by Liolikas on 2009-10-31
Try reinstall same kernel and chose update menu.lst

---

### Post by occams_beard on 2009-10-31
Thanks,

Solved this myself. I simply moved menu.lst and then did update-grub and it rebuilt it to use the proper kernel. E.g:

```

sudo mv menu.lst old-menu.lst
sudo update-grub

``` 

If you have the same problem and do this **be very sure** that menu.lst does indeed exist and is correct, otherwise you'll end up with an unbootable system.

---

### Post by jwthreec on 2009-11-07
genius! I was about to reinstall the kernel but was trying to think of another way. Moving menu.lst works perfect and you don't have to worry about copying your customizations till later.

Thanks

---


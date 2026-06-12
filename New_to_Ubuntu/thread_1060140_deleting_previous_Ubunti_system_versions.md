---
title: "deleting previous Ubunti system versions"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by pablolie on 2009-02-04
the latest updates to 2.6.27-11 modified my grub loader and the windows vista partition disappeared. grr. i guess i'll edit it.

while i am at it - how does one get Ubuntu to wipe out the remnants of previous Ubuntu versions? i don't quite see the point in keeping over 4 previous version in grub, and if i remove them from there, i'd probably like to remove unneccessary files from the system as well.

thanks...paul

---

### Post by Muffinabus on 2009-02-04
In menu.lst, make sure your non Ubuntu OS's are under the line ### END DEBIAN AUTOMAGIC KERNELS LIST.  This is probably why Vista was deleted when you installed the new kernal.

Old kernals can be uninstalled via synaptic.

Also, sudo apt-get clean and sudo apt-get autoremove will remove any files that aren't being used by any programs.

---

### Post by mhh91 on 2009-02-04
other kernels are kept in case the current fails to boot :)

---

### Post by pablolie on 2009-02-05
I know I should keep an old kernel or two around, just in case, but now it's getting too many of them. 3 or 4, come on. I wish there was a transparent uninstall option in Ubuntu.

The Synaptic Package Manager option, looking for linux-* is there, but very unintuitive - I have no idea which package/file I should truly mark for thorough deletion.

---

### Post by mcduck on 2009-02-05
> **pablolie said:**
> I know I should keep an old kernel or two around, just in case, but now it's getting too many of them. 3 or 4, come on. I wish there was a transparent uninstall option in Ubuntu.

The Synaptic Package Manager option, looking for linux-* is there, but very unintuitive - I have no idea which package/file I should truly mark for thorough deletion.

linux-image, linux-headers and linux-restricted-modules (old versions only, of course, so don't uninstall "linux-image" but "linux-image-2.6.27-9-generic" or whatever the actual package versions are on your setup.)

I always uninstall the old kernel after couple of days running the new version without any problems. This far nobody has been able to come up with a situation when currently fine kernel would suddenly break and force you to use older one instead, not to mention a situation when you'd need to use a kernel several versions older than the current. ;)

Keep one older version if you want, but it's *very* unlikely you'd ever need it. Keeping more than one old version is just wasting disk space.

edit: Like Muffinabus said, if you move the Windows entry around in menu-lst you must keep it outside of the area marked as "automagick kernels list". Also any other changes you make to current setup should also be made in the default options section of the file, the kernel list itself (and the whole "automagick kernels list" section of the file are automatically re-generated during kernel updates based on installed kernels and settings in default options section. I suggest reading through the comments in the menu.lst file, it has very good explanations for all the settings and how they are used.

---

### Post by jerome1232 on 2009-02-05
> **mcduck said:**
> 
I always uninstall the old kernel after couple of days running the new version without any problems. This far nobody has been able to come up with a situation when currently fine kernel would suddenly break and force you to use older one instead, not to mention a situation when you'd need to use a kernel several versions older than the current. ;)

Keep one older version if you want, but it's *very* unlikely you'd ever need it. Keeping more than one old version is just wasting disk space.


I actually had that happen to me once (sort of), I installed the new kernel, it worked fine, then I built and installed madwifi for the new kernel and that caused that particular kernel to panic during the boot process and while the old one worked fine.

Of course I doubt you would delete the old kernel until after you have applied any changes you have to make and your sure it's working good.

---

### Post by landshrk on 2009-02-21
> **pablolie said:**
> I know I should keep an old kernel or two around, just in case, but now it's getting too many of them. 3 or 4, come on. I wish there was a transparent uninstall option in Ubuntu.

The Synaptic Package Manager option, looking for linux-* is there, but very unintuitive - I have no idea which package/file I should truly mark for thorough deletion.

Yeah, kinda wish I'd paid more attention while doing my spring cleaning. Went into Synaptic, searched linux-image-2, and I guess I got a bit delete-crazy, 'cause I no longer have any Ubu kernels at all. So, I have the partition set up, (hopefully) all the data is still there, and I need to reinstall Intrepid, but I haven't the slightest how to do it without a physical CD. I'm using XP for the time being, but I can't stand it. Any ideas? Where should I look?

---

### Post by theozzlives on 2009-02-21
Do you have a live USB? I'm pretty sure there's a way to install the kernal without re-doing the whole thing.

---


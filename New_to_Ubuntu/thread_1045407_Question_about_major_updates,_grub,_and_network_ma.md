---
title: "Question about major updates, grub, and network manager"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Cyked on 2009-01-20
So about a week ago I downloaded the newest version of Ubuntu and installed it.  This is not my first venture into linux, but for all intents and purposes I am new to the OS.  I installed Ubuntu on a separate 30gb drive in my server 2k3 machine as I want to convert everything over to run on Ubuntu without totally ditching my windows server(web, ssh, etc).  

So I installed, setup SSH and Apache, had some issues with setting a static IP but quickly had that sorted. I ran all the system updates I was prompted for and network manager stopped working, eth1 being the wired NIC I am using will not do anything and I have no network connectivity (I'm reading more on this and appears to be a fairly widespread thing).  

My question is why when after doing updates does grub show 2 options of the OS to boot to?  The new and old?   If I boot to the older version, my network works.  Is there something I should be doing to update grub to remove the "older version" if I think its safe to be doing this?  What happens after multiple big updates that make radical changes to the OS, do I just have 8 OSes listed in grub?

Sorry for the noob question, I hope my ramblings make sense....

---

### Post by hovzio on 2009-01-20
There was probably a new kernel in your updates. Grub shows the old kernel as a second option so you can load from it if things go wrong. Try using the old kernel again, things should work as they did before.


Edit, after that you could edit your menu.lst so that only the appropriate kernel is loaded on boot.

---

### Post by drs305 on 2009-01-20
Take a look at this tutorial I wrote a while back about the number of kernels displayed in the menu.lst  

It discusses StartUp-Manager, a gui-based app that will let you tweak a variety of grub options without having to manually edit any files:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

It also discusses various options on what to do with the 'extra' kernels.

---

### Post by Cyked on 2009-01-20
Thanks for the replies! :-D

---

### Post by Cyked on 2009-01-21
So if there are major updates and there is a new kernel version the new kernel is installed, so I have two kernels taking up space basically.  After a period of time when comfortable the old kernel can be deleted and grub updated, correct?

Is there a way to know whether there will be a new kernel installed if I run updates?  Also, is the process the same to remove new kernels as old ones?  i.e. delete the new, boot to the old working kernel, update grub.  I ask because as I said I am new to linux and trying to brush up on what I can to get a better understanding on how the OS works vs. windows.

Thanks again!

---

### Post by theozzlives on 2009-01-21
If you want to delete the old (or new) kernel, search synaptic for "linux-image" and remove the version you want.

---

### Post by drs305 on 2009-01-21
> **Cyked said:**
> So if there are major updates and there is a new kernel version the new kernel is installed, so I have two kernels taking up space basically.  After a period of time when comfortable the old kernel can be deleted and grub updated, correct?

Yes.

> Is there a way to know whether there will be a new kernel installed if I run updates?  
The update will be displayed as "linux-image" probably followed by the version number (such as 2.6.24-19). StartUp-Manager or editing the menu.lst can set whether a new kernel is used automatically or not after a download. It will be "installed" but not used if you elect that option.

> 
Also, is the process the same to remove new kernels as old ones?  i.e. delete the new, boot to the old working kernel, update grub.  I ask because as I said I am new to linux and trying to brush up on what I can to get a better understanding on how the OS works vs. windows.
Thanks again!

If you delete a kernel via synaptic its entry will automatically be removed from the grub menu. Of course, ubuntu won't let you delete a kernel in use.  You can tell which one you are using with:
```

uname -r

```

---


---
title: "Boot Option Question"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-04-25
I dual boot with Vista and 9.04. When I turn on my comp and choose which OS I want to use, I have three different choices of Ubuntu to choose from. One is 9.04 2.6 28-11, (generic, recovery) 2.6 27-11, and 2.6 24-23. What is the reason for this? Are there any differences in the Ubuntus? Do I NEED to have all three of them?

---

### Post by kwacka on 2009-04-25
When the kernel is updated a new line is added to grub.

If all is running well you can delete the older lines from grub's menu.

---

### Post by barney385 on 2009-04-25
That's the earlier kernel. I like to leave it in case I bork my new one.

---

### Post by Didius Falco on 2009-04-25
> **MikesGuitar said:**
> I dual boot with Vista and 9.04. When I turn on my comp and choose which OS I want to use, I have three different choices of Ubuntu to choose from. One is 9.04 2.6 28-11, (generic, recovery) 2.6 27-11, and 2.6 24-23. What is the reason for this? Are there any differences in the Ubuntus? Do I NEED to have all three of them?

If you edit your menu.lst file (located in the ~/boot/grub folder) you can simply comment out what you don't want displayed with a # at the beginning of the line. You can get to it by opening a Terminal window and putting in this command:

> gedit ~/boot/grub/menu.lst

You can also uninstall older kernels from Synaptic, and Synaptic will automatically update the menu.lst file.

Another option is to change a setting in the menu.lst file to control how many kernels it will list. Look for this section in menu.lst:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```Change the "# howmany=all" part to the number of kernels you want displayed. Set it to 1 or 2 and that's how many kernels it will list. Note that you should leave the "#" at the beginning of the line. in the menu.lst file, one "#" just prevents it from being displayed on the screen, it'll still do what it is set to. 

Personally, I'd recommend keeping the two newest ones. Looking at your list of kernels, I'd guess you were running 8.10 and updated to 9.04. The  2.6.27-11, and 2.6.24-23 kernels are from Ubuntu 8.10.

I hope this helps....

---


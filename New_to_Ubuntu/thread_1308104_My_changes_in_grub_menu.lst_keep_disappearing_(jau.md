---
title: "My changes in grub menu.lst keep disappearing (jaunty)"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by jonboy99 on 2009-10-31
Hi folks, am having some trouble with parts of my /boot/grub/menu.lst file that keep being reset to default.

I am trying to reduce the default list of kernels being displayed on bootup by changing the howmany option to 1, rather than it's current 7.

When I change 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

to 

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=1
# howmany=all

and then run sudo update grub, it changes back to the original version.  However if I change some other things, eg which default kernel to boot it sticks perfectly.

Is my grammar wrong, should I be changing the number of #s?  I have tried two # in front of the howmany=all and one # in front of howmany=1, and some other variations but nothing sticks.  Help!

Jon

---

### Post by QLee on 2009-10-31
[QUOTE=jonboy99]Hi folks, am having some trouble with parts of my /boot/grub/menu.lst file that keep being reset to default.

I am trying to reduce the default list of kernels being displayed on bootup by changing the howmany option to 1, rather than it's current 7.

When I change 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

to 

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=1
# howmany=all

and then run sudo update grub, it changes back to the original version.  However if I change some other things, eg which default kernel to boot it sticks perfectly.

Is my grammar wrong, should I be changing the number of #s?  I have tried two # in front of the howmany=all and one # in front of howmany=1, and some other variations but nothing sticks.  Help!

Jon[/QUOTE]

Those with two #s are comments, you need to change the 
# howmany=all to # howmany=1 before upgrading kernels as per your question.

However, I suggest you you use 2 instead of one, that way if a new kernel won't boot for some reason you can boot the previous working kernel but it is your choice to do it either way.

---

### Post by jonboy99 on 2009-10-31
Thanks Qlee, just tried with only one #, but as soon as I run sudo update-grub it changes straight back to how it was before I edited it!

---

### Post by heyho on 2009-10-31
I may be wrong, but shouldn't you have nothing in front of howmany=1 for it to work?

Whenever I make changes to menu.lst, I just save it then reboot to check if it has worked.  Never used update grub.

---

### Post by LewRockwell on 2009-10-31
To edit you must be sudo```
gksudo gedit /boot/grub/menu.lst
```If you aren't then it will "let" you "change" things on the display but it will NOT save your changes to the file

.

---

### Post by QLee on 2009-10-31
> **jonboy99 said:**
> Thanks Qlee, just tried with only one #, but as soon as I run sudo update-grub it changes straight back to how it was before I edited it!
Did you see this in the menu.lst file?
"### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below"

---

### Post by jonboy99 on 2009-10-31
QLee - yes, I presumed that meant I must edit the relevant section manually?  How else will they be changed?

Other points - I am using sudo.

Re the #s, yes normally they would need removing but the section above where the howmany is has a comment saying not to remove them in this section.

---

### Post by QLee on 2009-10-31
[QUOTE=heyho]I may be wrong, but shouldn't you have nothing in front of howmany=1 for it to work?[/QUOTE]
From the menu.lst file:
"## DO NOT UNCOMMENT THEM, Just edit them to your needs"

[QUOTE=heyho]Whenever I make changes to menu.lst, I just save it then reboot to check if it has worked.  Never used update grub.[/QUOTE]
+1

---

### Post by jonboy99 on 2009-10-31
Oh i'm such a numpty, it should read like this:

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

NOT

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
# howmany=1
## howmany=all


Sorted now.  :D  Thanks for help all.

---


---
title: "Ubuntu listed many times in grub loading screen"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by kickwin on 2009-09-01
In my grub screen  I see the following lines repeating 3 times. 

Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)

Any idea how I can fix this and why it is like that?

---

### Post by j7%&lt;RmUg on 2009-09-01
type this command into a terminal:

```

sudo gedit /grub/boot/menu.lst

```

This should pull up a file and when it does please post its contents here.

Im pretty sure that file path is correct but if not just do a search for a file called "menu.lst".

---

### Post by lisati on 2009-09-01
> **kickwin said:**
> In my grub screen  I see the following lines repeating 3 times. 

Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)

Any idea how I can fix this and why it is like that?

As long as the numbers are different for each of the different pairs of entries, this is normal. The entry for recovery mode is roughly equivalent to Windows "safe" mode. Ubuntu also keeps some old kernels around for a while after an update, just in case something goes wrong with an update and it doesn't suit somebody's system.

---

### Post by Finalfantasykid on 2009-09-01
> type this command into a terminal:

 	Code:
 	sudo gedit /grub/boot/menu.lst 
This should pull up a file and when it does please post its contents here.

Im pretty sure that file path is correct but if not just do a search for a file called "menu.lst".

That path is incorrect.  

```
sudo gedit /boot/grub/menu.lst
```

that should be the correct path.  And like nisshh said, just post the contents of that file, and one of us will help you get what you want.

---

### Post by anujpathania on 2009-09-01
Well, this should be harmless. If you still want to correct it then you need to modify the grub file (/grub/boot/menu.lst) as mentioned in above post. You can do that in any file editor of your liking via terminal.

---

### Post by hetx on 2009-09-01
I know it gets said alot but please use gksu for GUI apps! I'm nagging cause I have broken my own system with sudo instead of gksu.

ie
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by LewRockwell on 2009-09-01
gksudo

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

[http://en.wikipedia.org/wiki/Gksudo](http://en.wikipedia.org/wiki/Gksudo)

[http://en.wikipedia.org/wiki/Su_(Unix)](http://en.wikipedia.org/wiki/Su_(Unix))

[http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)


one should understand the differences between these...


.

---

### Post by oldos2er on 2009-09-01
> **kickwin said:**
> In my grub screen  I see the following lines repeating 3 times. 

Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)

Any idea how I can fix this and why it is like that?

 Major kernel upgrades do not overwrite any older kernels you may have, mostly for safety. If you really do have the same kernel repeating three times, then edit the file as others have pointed out. If they are different kernels and you want to trim down your menu.lst, open Synaptic, search for "linux image", and uninstall one or more older kernels. Your menu.lst will be automatically updated.

 I personally prefer to keep a couple kernels bootable, "just in case."

---

### Post by SunnyRabbiera on 2009-09-01
Yeh this is normal, no real extra space is being used.

---

### Post by sydbat on 2009-09-01
> **oldos2er said:**
> Major kernel upgrades do not overwrite any older kernels you may have, mostly for safety. If you really do have the same kernel repeating three times, then edit the file as others have pointed out. If they are different kernels and you want to trim down your menu.lst, open Synaptic, search for "linux image", and uninstall one or more older kernels. Your menu.lst will be automatically updated.

 I personally prefer to keep a couple kernels bootable, "just in case."So, using your method, I should be able to get rid of 4 of the 5 oldest kernels without harming my system, right? How much space does this free up?

EDIT - The kernels I want to remove are 2.6.24-22.45, 21-43, 19.41, 16.30 (the original Hardy kernel). That would leave 23.52 and 24.59. Is that right?

---

### Post by Niko Johnson on 2009-09-01
When you edit the /boot/grub/menu.lst with 

sudo pico /boot/grub/menu.lst 

you can simply comment out the extra bootable versions with the # sign right in front of the code. this will read your once bootable option on the menu.lst file as a comment and it wont show up on your grub screen. however it does not delete it so you dont have to worrie about accidently damageing something you didnt mean too. i had the same problem and i think this is the safest way to edit the grub screen.
example: 

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=b575ad0d-13fa-43b1-bc$
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=b575ad0d-13fa-43b1-bc$
initrd          /boot/initrd.img-2.6.28-15-generic

#title          Ubuntu 9.04, kernel 2.6.28-14-generic
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-13-generic root=UUID=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-13-generic
#quiet

#title          Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-13-generic root=UUID=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-13-generic

#title          Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-11-generic root=UUID=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-11-generic
#quiet


You can see i had a few copies myself but I only keept the (generic) and (recovery mode) and just commented out the other ones... this is good in case i want to go back and use them later... all i have to do is delete the # sign and there back in action!

---

### Post by sydbat on 2009-09-01
> **Niko Johnson said:**
> When you edit the /boot/grub/menu.lst with 

sudo pico /boot/grub/menu.lst 

you can simply comment out the extra bootable versions with the # sign right in front of the code. this will read your once bootable option on the menu.lst file as a comment and it wont show up on your grub screen. however it does not delete it so you dont have to worrie about accidently damageing something you didnt mean too. i had the same problem and i think this is the safest way to edit the grub screen.
example: 

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=b575ad0d-13fa-43b1-bc$
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=b575ad0d-13fa-43b1-bc$
initrd          /boot/initrd.img-2.6.28-15-generic

#title          Ubuntu 9.04, kernel 2.6.28-14-generic
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-13-generic root=UUID=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-13-generic
#quiet

#title          Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-13-generic root=UUID=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-13-generic

#title          Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-11-generic root=UUID=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-11-generic
#quiet


You can see i had a few copies myself but I only keept the (generic) and (recovery mode) and just commented out the other ones... this is good in case i want to go back and use them later... all i have to do is delete the # sign and there back in action!Nice. Maybe I'll do that instead. Unless, of course, removing the old kernels frees up a substantial amount of room in /...

---

### Post by egalvan on 2009-09-01
> **LewRockwell said:**
> gksudo

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)
]
[http://en.wikipedia.org/wiki/Gksudo](http://en.wikipedia.org/wiki/Gksudo)

[http://en.wikipedia.org/wiki/Su_(Unix)](http://en.wikipedia.org/wiki/Su_(Unix))

[http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)


**one should understand the differences between these...**


Absolutely!!!

+1

---

### Post by egalvan on 2009-09-01
Editing menu.lst and changing the "howmany" option will lead to a cleaner menu listing,
and subsequent up-dates will not change it.

And this can also be done in a **GUI manner via StartupManager** if one is hazy on editing system files directly.


I've settled on 2.
Here is the relevant section from /boot/grub/menu.lst

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR="Red"]# howmany=2[/COLOR]

```

---

### Post by sydbat on 2009-09-01
OK...commented out the entries...now how do I save it and exit? (I know, stupid question, but I do not know how to get the  ^X or ^G commands at the bottom of the terminal to work)

EDIT - Never mind...figured it out...

For those who do not know, ^ means the Ctrl key...DOH!

---

### Post by LewRockwell on 2009-09-01
> **niko johnson said:**
> when you edit the /boot/grub/menu.lst with 

sudo pico /boot/grub/menu.lst 

you can simply comment out the extra bootable versions with the # sign right in front of the code. This will read your once bootable option on the menu.lst file as a comment and it wont show up on your grub screen. However it does not delete it so you dont have to worrie about accidently damageing something you didnt mean too. I had the same problem and i think this is the safest way to edit the grub screen.
Example: 

Title           ubuntu 9.04, kernel 2.6.28-15-generic
uuid            b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
kernel          /boot/vmlinuz-2.6.28-15-generic root=uuid=b575ad0d-13fa-43b1-bc$
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
kernel          /boot/vmlinuz-2.6.28-15-generic root=uuid=b575ad0d-13fa-43b1-bc$
initrd          /boot/initrd.img-2.6.28-15-generic

#title          ubuntu 9.04, kernel 2.6.28-14-generic
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-13-generic root=uuid=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-13-generic
#quiet

#title          ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-13-generic root=uuid=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-13-generic

#title          ubuntu 9.04, kernel 2.6.28-11-generic
#uuid           b575ad0d-13fa-43b1-bc01-f1ca3f93cec2
#kernel         /boot/vmlinuz-2.6.28-11-generic root=uuid=b575ad0d-13fa-43b1-bc$
#initrd         /boot/initrd.img-2.6.28-11-generic
#quiet


you can see i had a few copies myself but i only keept the (generic) and (recovery mode) and just commented out the other ones... This is good in case i want to go back and use them later... All i have to do is delete the # sign and there back in action!

+ 1

.

---

### Post by oldos2er on 2009-09-01
> **sydbat said:**
> So, using your method, I should be able to get rid of 4 of the 5 oldest kernels without harming my system, right? How much space does this free up?

EDIT - The kernels I want to remove are 2.6.24-22.45, 21-43, 19.41, 16.30 (the original Hardy kernel). That would leave 23.52 and 24.59. Is that right?
[B]
ls -hl /boot/vmlinuz*[/B] will show you the size of all kernels. They're not very big, around 3.5MB each.

---

### Post by Ric_NYC on 2009-09-01
It doesn't look good to have all those entries when the computer starts.

---

### Post by sydbat on 2009-09-01
> **oldos2er said:**
> [B]
ls -hl /boot/vmlinuz*[/B] will show you the size of all kernels. They're not very big, around 3.5MB.Thanks.

---

### Post by egalvan on 2009-09-01
> **Ric_NYC said:**
> It doesn't look good to have all those entries when the computer starts.

Totally a personal choice.

Which is an area that *nix excels in :)

And what so many of us love about Linux in particular.

---

### Post by drs305 on 2009-09-01
StartUp-Manager ! - a gui tool that will tweak menu.lst without manual editing. Here is a link for a guide on how to use it and how to limit the kernels you see in your menu.lst.

[Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Yeah, I know, I'm really late to this party...  ](*,)

---

### Post by egalvan on 2009-09-01
> **drs305 said:**
> 
[Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Yeah, I know, I'm really late to this party...  ](*,)

You are welcome, the more the merrier...
or at least... more answers and choices for the OP.


And thanks for the link...
I'll be sure to bookmark it.

---

### Post by 1ronlung on 2009-09-01
Does anybody know if there's an easy workaround yet for "update-grub" not updating menu.lst ?

Thanks

---


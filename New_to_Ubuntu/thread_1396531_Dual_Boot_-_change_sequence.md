---
title: "Dual Boot - change sequence"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by nitrodrops on 2010-02-02
Hi All,

An Ubuntu-newbie here.

One question, i have just setup my PC for Dualboot (XP & Ubuntu).

The default option in the boot sequence is to Ubuntu (using Ubuntu bootloader).

How can i change the default to point to XP? 

I have googled for this URL, following the steps 

**[SIZE=1][COLOR=Blue]Changing the default operating system to boot[/COLOR][/SIZE]**

                                                                          [SIZE=1][COLOR=Blue]You can decide which operating system will be started automatically if you have not chosen one from the boot menu within a certain time (see [the section called “Changing the boot menu timeout”]("https://help.ubuntu.com/8.04/switching/dualboot-custom.html#dualboot-custom-timeout") for more information on this).[/COLOR][/SIZE]
                                    
[LIST=1]
[*]                       [SIZE=1][COLOR=Blue]Press Applications &#8594; Accessories &#8594; Terminal.[/COLOR][/SIZE]
[*]                       [SIZE=1][COLOR=Blue]The **Terminal** screen will appear. Type the following into the Terminal, entering your administrative password if prompted:[/COLOR][/SIZE]
                       [SIZE=1][COLOR=Blue]cd /boot/grub
sudo cp menu.lst menu_backup.lst
sudo gedit menu.lst[/COLOR][/SIZE]
[*]                       [SIZE=1][COLOR=Blue]The **Text Editor** will start, and will open the file menu.lst.[/COLOR][/SIZE]
[*]                       [SIZE=1][COLOR=Blue]The entry for each available operating system is arranged in blocks similar to the following:[/COLOR][/SIZE]
                       [SIZE=1][COLOR=Blue]title        Ubuntu, kernel 2.6.15-26-686
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-686
savedefault[/COLOR][/SIZE]
boot
[/LIST]


However at step 2. After stepping 

[SIZE=1][COLOR=Blue]sudo cp menu.lst menu_backup.lst[/COLOR][/SIZE]
my terminal show
[COLOR=Sienna]*cp: cannot stat 'menu.1st': No such file or directory.*[/COLOR]

Any clues from any kind souls will be much appreciated.


Cheers
Nit

---

### Post by lotharmat on 2010-02-02
menu.lst (Lowercase L not a One!)

This may cure your issues.

---

### Post by Shark_AtK12 on 2010-02-02
> **lotharmat said:**
> menu.lst (Lowercase L not a One!)
 
This may cure your issues.
 
I've made that same mistake

---

### Post by lotharmat on 2010-02-02
> **Shark_AtK12 said:**
> I've made that same mistake

To be honest; I think most people have especially in 'fdisk -l'

---

### Post by Silvertones on 2010-02-02
You didn't say whether you installed to a seperate partion of if you installed within Windows (WUBI). If WUBI it's done in Windows. Right click on my computer/properties/startup & recover. Drop down menue choose XP

---

### Post by audiomick on 2010-02-02
If you have a fresh installed 9.10, you will have grub 2, which doesn't use menu.lst anymore.

Instructions for grub 2 here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by nitrodrops on 2010-02-02
> **lotharmat said:**
> menu.lst (Lowercase L not a One!)

This may cure your issues.


thnx mate, how silly i am.

Working good now!

---

### Post by lotharmat on 2010-02-02
Cool!

Don't forget to mark the thread as solved (thread tools at the top)

---


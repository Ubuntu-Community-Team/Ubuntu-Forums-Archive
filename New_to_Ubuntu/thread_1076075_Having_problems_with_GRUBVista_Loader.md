---
title: "Having problems with GRUB/Vista Loader"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by interp on 2009-02-20
I currently have both ubuntu and vista installed.

I have tried installing them both ways round and installing grub over the vista loader but have had no luck as it boots straight into windows with no loaders showing up!

any ideas?

Thanks.

---

### Post by Hospadar on 2009-02-20
First off, for reference, things typically work better when windows is installed first, then linux.  Grub will see the windows bootloader and handle it nicely, windows will just blow away whatever is there.

What does your hard drive setup look like? do you have multiple drives?  Probably you just arn't booting off your linux drive (in the bios).  Try going into the bios settings and switching up the drives.

---

### Post by interp on 2009-02-21
My hdd setup:

hd0 - Just media drive
hd1
1 - NFS - Windows
2 - Swap
3 - ext - Ubuntu installation

I tried using EasyBCD but no luck there!

if i was going to reinstall ubuntu where should I point the bootloader in advanced?

---

### Post by interp on 2009-02-21
Ok, i got grub working again BUT now when i try to load in to vista it says NTLRD missing, what do i do? :(

---

### Post by caljohnsmith on 2009-02-21
In order to get a clearer picture of your setup related to your Windows booting problem, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---


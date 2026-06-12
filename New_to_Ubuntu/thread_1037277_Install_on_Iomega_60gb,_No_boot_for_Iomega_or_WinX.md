---
title: "Install on Iomega 60gb, No boot for Iomega or WinXP"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by jane65 on 2009-01-11
Newbie needs lots of help.  I put the live cd on to the iomega and now the only way I can use my pc is from the live cd.  I get a grub loading error21 on stage 1.5.  I wanted to try Unbuntu until I was familiar with it.  Now I spend my time searching the links on grubs and whatever else is there which coming from Windows doesn't make much sense.  Where is the best place to start and if there are books available, which is the best one for a newbie.  Really looking forward to your help.:confused:

---

### Post by caljohnsmith on 2009-01-11
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---


---
title: "Minimal BASH-like line editing is supported"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by phandrew08 on 2009-01-18
I just recently tried out ubuntu on my main laptop that i use for everything. school, fun, music, etc.. so right now reformatting is not an option. the problem first came to be when MBR stopped working so i installed grub. once installed i restarted and messages such as this started to appear;

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

i researched the forums and tried the find /boot/grub/stage1
                                                      stage2
                                                      menu.lst

 but the files were not found.

Unlike the situation of other peoples where they created another partition, i didnt.i installed ubuntu 8.10 on top of vista and now i cant access vista.

---

### Post by jpkotta on 2009-01-18
If you installed on the Vista partition, Vista's gone.  Effectively impossible to recover.  

You should repartition the drive, reinstall Vista, reinstall Ubuntu on another partition, and restore your data from backups.

---

### Post by The Cog on 2009-01-18
When you say you "tried Ubuntu", what do you mean? I can think of several possibilities:
1: You installed Ubuntu using the whole hard disk, overwriting Vista
2: You installed Ubuntu in dual-boot, shrinking the Vista partition to make space
3: You installed Ubuntu using WUBI, which doesn't reartition but creates a virtual drive file inside the Vista filesystem

If 3, then there is no stage 2/3 that GRUB can find, and you need to reinstall the Windows MBR. I believe the windows installer CD can do this.

If 1 or 2, then you may be able to get into Ubuntu using a live CD and choosing to rescue using the Linux partition and issuing the command:
**grub-install /dev/sda**
once you are in the installed Linux.

---

### Post by caljohnsmith on 2009-01-18
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---


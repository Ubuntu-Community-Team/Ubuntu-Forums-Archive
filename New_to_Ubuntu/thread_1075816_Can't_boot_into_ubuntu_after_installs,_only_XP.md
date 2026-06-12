---
title: "Can't boot into ubuntu after installs, only XP"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by fcweissbach on 2009-02-20
I did a good cleaning of 2 of my 3 hdds, my third just containing media.

Fresh install of XP on hdd 1, works fine.
Fresh install of Ubuntu 8.10 on same hdd.  After a successful installation, computer boots directly to XP.
Cleaned off Ubuntu and tried again but same outcome.  Downloaded Ubuntu 8.10 again on another computer and went through install again, this time on the blank 2nd hdd, but got same results.

Finally, downloaded 8.04 and tried to install on fresh second hdd, went through installation smoothly, then after restart I actually got some text on black screen about my USB network card not being recognized, then it proceeded to boot directly to XP. 

I downloaded a program called BootSwitcher 2.0, but to no avail, same results.

I have never used any Linux OS, and was very excited to try Ubuntu, but I'm growing tired of reinstalling it so many times.

Any suggestions?

---

### Post by sancho panza on 2009-02-20
Try running [Super grub disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") after you have successfully installed Ubuntu following a successful WinXP install to fix the Grub boot loader.

This might sound silly, but I'm assuming that you are shutting down windows before trying to boot into ubuntu, and not hibernating windows? Sorry if i'm wrong. Hope the first suggestion helps.

Cheers!

---

### Post by caljohnsmith on 2009-02-20
I think it would help to get a better picture of your setup in order to figure out what the issue is, so how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---


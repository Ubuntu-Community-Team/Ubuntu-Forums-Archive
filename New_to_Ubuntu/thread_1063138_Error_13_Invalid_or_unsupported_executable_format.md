---
title: "Error 13: Invalid or unsupported executable format"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Riggspc on 2009-02-07
I was triple booting with Vista Home Premium, Windows 7, and Ubuntu (Installed in that order).  I was running out of space on my Vista partition so I deleted the Windows 7 partition and expanded the Vista partition into that space, using the Vista partitioning tool.  Now when I turn on my computer and I get the Grub bootloader, I cannot access the Windows Vista/Longhorn loader, which is how I loaded Vista before now. I get the Error 13 code. Help, please?

---

### Post by caljohnsmith on 2009-02-07
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Riggspc on 2009-02-07
I fixed it now, all I had to do was reinstall Ubuntu.
Thanks for the help, but I didn't understand what you were saying anyways...I'm a COMPLETE Ubuntu n00b, I'm afraid

---


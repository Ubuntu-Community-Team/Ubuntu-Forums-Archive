---
title: "How do I Delete Ubuntu from Windows 98 Startup Menu?"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by lhager on 2009-10-07
I've already deleted ubuntu from my hard drive and now I'm trying to remove it from the startup menu.  On the web they suggest booting to the command prompt using my windows 98se CD and entering **fdisk /MBR**, after this type **Exit** but it didn't work.  I got the a:/ cursor but when I entered fdsik/MBR then exit, nothing happened and it didn't remove linux.  Please help if you know what I did wrong and how to correct this!

---

### Post by praveesh on 2009-10-07
Are you saying about an Ubuntu install inside windows ?. If yes, how did you remove it? By uninstalling ? Usually, unimitalling will automatically remove the boot manager entry too.

---

### Post by Mark Phelps on 2009-10-08
If you installed using Wubi (inside Windows), this is a known problem with removing Wubi.  Open your boot.ini file. Remove the ONE LINE that mentions Ubuntu.  Don't remove any other lines.  Save the changed file.  Reboot.

Should not get an OS menu anymore; should go directly into MS Windows.

---

### Post by Captain_tux on 2009-10-08
Why are you using Win 98?

---

### Post by lhager on 2009-10-09
I installed ubuntu from a CD which created a dual boot system.  I uninstalled it but it remained on the startup menu.  When I start the computer it gives me the option to choose ubuntu or windows even though ubuntu has been removed.  And I'm using win 98 because that is what was installed on the used dell inspiron 5000 laptop that I bought several years ago which came with a win 98 CD.  It's an older computer.

---

### Post by lhager on 2009-10-09
Thanks for the advice!

---

### Post by lhager on 2009-10-09
Umm...because it is the operating system that came with my computer which I bought used several years ago.

---

### Post by lhager on 2009-10-09
Where can I find the boot.ini file?  I did a search and couldn't locate it either in windows or anywhere else on my hard drive.

---

### Post by x C0MMAND0 x on 2009-10-09
On windows, go to "Start > Run > msconfig"


Then go over to the boot.ini tab

---

### Post by occams_beard on 2009-10-10
Did win98 even have a boot.ini ? I thought that was an NT thing.

---


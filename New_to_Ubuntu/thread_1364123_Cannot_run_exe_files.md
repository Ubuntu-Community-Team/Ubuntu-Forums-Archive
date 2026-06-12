---
title: "Cannot run exe files"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by DM2126@mac.com on 2009-12-25
I get a message like this when trying to run exe files. I use ubuntu 9.1 and wine.



Archive:  /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe
[/home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe or
          /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe.zip, and cannot find /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe.ZIP, period.

Help

---

### Post by overdrank on 2009-12-25
Hi and welcome, Moved to Absolute Beginner Talk

---

### Post by oldsoundguy on 2009-12-25
.exe files are Windows files.  Linux is not Windows. You can not run Windows program files natively on Linux.
You need a separate partition, or VM area, or try Wine in order to run them.  And even then, it will be a crap shoot to run them properly.

---

### Post by dwasifar on 2009-12-25
For some reason, the default Ubuntu file type association for .exe files is Archive Manager, not Wine.  Your error message is an Archive Manager error.

Right-click any .exe file, choose Properties, select the Open With tab, and change the default application to Wine Windows Program Loader.  You should be fine after that.

---

### Post by DM2126@mac.com on 2009-12-25
> **dwasifar said:**
> For some reason, the default Ubuntu file type association for .exe files is Archive Manager, not Wine.  Your error message is an Archive Manager error.

Right-click any .exe file, choose Properties, select the Open With tab, and change the default application to Wine Windows Program Loader.  You should be fine after that.
Thanks - this worked.

---


---
title: "error reading exe on cd"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by jbumgar on 2010-03-31
I get this error when I open up the cd and try to run the below exe. A couple of years ago it did ok on that version of Ubuntu.

Archive:  /media/cdrom0/AutoRunMorrowind.exe
[/media/cdrom0/AutoRunMorrowind.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/AutoRunMorrowind.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/AutoRunMorrowind.exe or
          /media/cdrom0/AutoRunMorrowind.exe.zip, and cannot find /media/cdrom0/AutoRunMorrowind.exe.ZIP, period.

How do I fix this this?

---

### Post by Bachstelze on 2010-03-31
How are you tryng to run it?

---

### Post by jbumgar on 2010-03-31
As an autorun exe.  I also tried it with the setup exe with the same results.

---

### Post by jbumgar on 2010-03-31
I don't think I have been very clear so far.  What I do is stick the cd in the drive.  Ubuntu then shows the contents of the disk files.  I am just simply double clicking on the exe.  I want to run this program under wine.  Is the more to it than that?

---

### Post by Calash on 2010-03-31
Odd, that process should have worked.

If you right-click on the exe file, is there an listing for Wine at the top of the menu?

---

### Post by NCLI on 2010-03-31
You're trying to open it with Archive Manager ;)

1) Make sure you have Wine installed.
2) Right-click the file, go to the Open With tab, then make sure Wine is selected there and click Close.
3) Try opening the file again.

---

### Post by jbumgar on 2010-03-31
Yep right clicking let me install.  Thanks a lot.  Do you know how I could update the file?

---


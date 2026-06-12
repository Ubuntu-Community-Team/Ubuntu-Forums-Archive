---
title: "Adobe Acrobat"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by Alienspecimen on 2010-11-12
I would like to install Adobe Acrobat 9 Pro PC Edition.

I already have Wine installed, interesting that other Adobe applications (for PC) started installing automatically under wine.  Those are the ones within Adobe Creative Suite-Photoshop, Illustrator, In Design.

After I put the disk in the drive, an Adobe 9 icon shows up on the desktop.  If I click on the icon, the files inside the disk show up.  I then click on the Setup.exe and this is what I get:

An error occurred while loading the archive


Archive:  /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe
[/media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe or
          /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe.zip, and cannot find /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe.ZIP, period.

Once I dug through the files, I found also the following icons to click on:  Autoplay.exe and Windows Installer KB 893803-V2-X86.exe.  After clicking on those, the same message appears, but Setup.exe is replaced with either Autoplay.exe or Windows Installer KB 893803-V2-X86.exe, depending on which icon I clicked on.

Please, let me know if it is possible to install Adobe Acrobat 9 Pro.

Thanks in advance

Best

Boris

---

### Post by sandyd on 2010-11-12
> **Alienspecimen said:**
> I would like to install Adobe Acrobat 9 Pro PC Edition.

I already have Wine installed, interesting that other Adobe applications (for PC) started installing automatically under wine.  Those are the ones within Adobe Creative Suite-Photoshop, Illustrator, In Design.

After I put the disk in the drive, an Adobe 9 icon shows up on the desktop.  If I click on the icon, the files inside the disk show up.  I then click on the Setup.exe and this is what I get:


Archive:  /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe
[/media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe or
          /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe.zip, and cannot find /media/cdrom0/Adobe Acrobat 9 Pro/Setup.exe.ZIP, period.

Once I dug through the files, I found also the following icons to click on:  Autoplay.exe and Windows Installer KB 893803-V2-X86.exe.  After clicking on those, the same message appears, but Setup.exe is replaced with either Autoplay.exe or Windows Installer KB 893803-V2-X86.exe, depending on which icon I clicked on.

Please, let me know if it is possible to install Adobe Acrobat 9 Pro.

Thanks in advance

Best

Boris

you have to copy the files from the cd to the desktop because you cannot change the permissions of the installer.

---

### Post by 3rdalbum on 2010-11-12
You do not have to copy the files off a CD.

Open a terminal and type *wine*, with a space bar at the end. Then drag your program to the terminal. Press Enter in the terminal window and the program will run.

I don't know if Acrobat is supported by Wine but you can try it.

---

### Post by Alienspecimen on 2010-11-12
Thank you for the fast reply.

I cannot install it either way.

I tried the copy files to desktop method and ended up with the same error.

Same happened with dragging the program into the root terminal window.  I tried dragging it from the disk and from the files copied to the desktop.

Do you have any other suggestions.  I am kinda on the pinch, coz my Windoz machine died...

Thanks in advance

Boris

---

### Post by oldos2er on 2010-11-12
Maybe something here will help: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=847](http://appdb.winehq.org/objectManager.php?sClass=application&iId=847)

---


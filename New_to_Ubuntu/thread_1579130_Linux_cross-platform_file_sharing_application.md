---
title: "Linux cross-platform file sharing application?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Rician on 2010-09-21
Do Linux have any  cross-platform file sharing applications? If so, what do you guys recommend?  i want to transfer files  from ubuntu > Windows or the other way windows > ubuntu. I need GUI not Command line.

Thanks

---

### Post by -kg- on 2010-09-21
If you're talking about just copying files from one to the other, you can use any file browser under Linux to transfer the files from one partition to the other.  You can use the "Places" menu, find the files you want to move, and move them to the proper place.

Things are not so simple Windows > Linux, though.  Windows does not natively recognize Linux partitions.  There are drivers you can use for this, but if you absolutely want to share some files between the two easily, you need to create a separate partition formatted to one of the Windows formats and always put the files there.  Linux will read and write to any Windows partition, and as long as you put your desired files on that partition, you can share them freely between the two without the use of a special application.

---

### Post by bradleypariah on 2010-09-21
Right click on a file you want Windows to be able to see.
Choose "Properties" in the list.
Choose the "Sharing" tab.  Click the little box that says "Share this folder."
That will prompt Ubuntu to automatically download a file-sharing service called "Samba" or "Smb4K".
If you have to restart your computer, just try to share the folder again and choose to allow "Guest Access".

---

### Post by bradleypariah on 2010-09-21
I just realized... are you wanting to share files between Windoze and Linux on a Network?
Because that's the question I answered.

If you need to share files between two OS's a dual-booted computer, you should simply create a mediator partition between the two operating systems, formatted as FAT.

---

### Post by bodhi.zazen on 2010-09-21
For sharing files over a network you have many options.

On a LAN you can use samba, NFS, or FTP.

Over the internet you can use ssh (winscp is a graphical front end for Windows clients) or any number of drop box services, including Ubuntu One.

---

### Post by abir16 on 2010-09-23
If you are not longer use in Linux, I recommend you to install Samba and share files like in Windows.
__________________
				FlashMirrors - is a free [file sharing]("http://flashmirrors.com/") web service.

---


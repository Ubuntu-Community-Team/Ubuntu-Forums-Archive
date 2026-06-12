---
title: "Tricky rsync via smb"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Lutherian on 2007-03-29
I am trying to mirror two directories via grysnc (or rsync) in the following manner

[[COLOR="Blue"]Computer 1[/COLOR]]          <====> [[COLOR="Red"]Computer 2[/COLOR]]
i.e.
[/media/[COLOR="Blue"]WorkHorse[/COLOR]] <====> //My-smbserver/[COLOR="Red"]My-Documents[/COLOR]/My-Music

[COLOR="Blue"]WorkHorse[/COLOR] = hdb1 ([COLOR="Blue"]fat32 drive[/COLOR])
[COLOR="Red"]My-Documents[/COLOR] = hdb1 (ext3) user rights rwxrwxrwx (via sudo chown -r 777)


I can sync in this direction [[COLOR="Blue"]Computer 1[/COLOR]]====> [[COLOR="Red"]Computer 2[/COLOR]]
but _not in this direction_ [[COLOR="Blue"]Computer 1[/COLOR]]<==== [[COLOR="Red"]Computer 2[/COLOR]]


This is strange to me, as I made the drive a vfat (fat32) to avoid problems with user rights etc. In any case it seems that rsync can't write to it for some reason.

I am launching grsync with the sudo command.
I am able to write to the fat32 drive manually

---

### Post by Lutherian on 2007-03-29
OK, I am answering my own post here, but anyway

It seems the answer is basically [I]" Don't use FAT32 - It sucks - it wasn't designed to handle this type of operation)
[/I]

Quote Start
*..the problem is that rsync uses mkstemp(3) to create temporary files. Since this creates temporary files with 0600 permissions and vfat fs uses the same uid to all files the file creation fails.*
Quote End


Solution it would seem is:
Reformat drive to ext 3, don't worry about Windows not being able to access the drive, just install the plug-in [ [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html) ]onto the the windows machines that will enable read & write to it.

I'll try it tonight and report back.

---


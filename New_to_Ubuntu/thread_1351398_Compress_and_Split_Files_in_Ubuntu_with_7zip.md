---
title: "Compress and Split Files in Ubuntu with 7zip"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-10
I have p7zip and p7zip-full installed i know how to compess a file using deflate 64 from the command line

7z a -t=zip -mm=deflate64 archive.zip file

How do i do spilt and zip files using deflate 64 zip like the web cit
[http://maketecheasier.com/how-to-compress-and-split-files-in-ubuntu/2008/10/06](http://maketecheasier.com/how-to-compress-and-split-files-in-ubuntu/2008/10/06)
showes for the linux bzip

Is their a way to add 7zip's deflate 64 to nautilus so that i can click on a file and it will zip it with deflate 64 or even better and split it and zip using deflate 64

---

### Post by diablo75 on 2009-12-14
It's been a while, but I remember installing 7zip on my machine and it automatically added the option of creating a 7zip formated archive with the "Create Archive" feature that's built into Nautilus.  You'd just right-click on whatever you wanna to archive, Create Archive, and then hit the drop-down box to select from a list of formats.

---

### Post by NESFreak on 2009-12-14
> **diablo75 said:**
> It's been a while, but I remember installing 7zip on my machine and it automatically added the option of creating a 7zip formated archive with the "Create Archive" feature that's built into Nautilus.  You'd just right-click on whatever you wanna to archive, Create Archive, and then hit the drop-down box to select from a list of formats.

He's saying the gui is missing some of the more advanced options. Like forinstance changing the compression algorithm (not the same as format).

To answer diablo's question: the -v{partsize} command wil split your 7z archive in chunks of the size you specified.

---

### Post by NESFreak on 2009-12-14
I took a better look at "file-roller", ubuntu's default file archiver you're referring to. The commandline options of the various formats seem to be hardcoded, however by using gconf-editor and browsing to /apps/file-roller you could change a few options. (some of the more interesting options like 'encrypt_header' and 'compression_level' are available there)

To me the compression_level option being available in gconf but not in the create archive dialog seems like a bug. I'll check if it's already filed, and if not i'll do it after tea.
----edit----
someone already filed it:
[https://bugzilla.gnome.org/show_bug.cgi?id=591630](https://bugzilla.gnome.org/show_bug.cgi?id=591630)

---


---
title: "password a folder"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by DarinB on 2009-07-31
I think i came up with strange way to password a file
but the contents can be seen but not opened
1. right click folder create archive drop down list to zip
2. expand other options. add password. 
3. create
then you will have anything that was in there require a password but once you open one file they all will open (which is fine for me) 
4. to add more files to the folder open the archive go to edit > password > add password > add files or folders 
next time you open the zip you will add password once.
i think this will work any thoughts on this??????

---

### Post by gali98 on 2009-08-03
Ummm... It looks like it will work... 
But this might work better - and more secure... and easier :) Looks neat...
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)
Kory

---

### Post by Katalog on 2009-08-03
> **DarinB said:**
> I think i came up with strange way to password a file
but the contents can be seen but not opened
1. right click folder create archive drop down list to zip
2. expand other options. add password. 
3. create
then you will have anything that was in there require a password but once you open one file they all will open (which is fine for me) 
4. to add more files to the folder open the archive go to edit > password > add password > add files or folders 
next time you open the zip you will add password once.
i think this will work any thoughts on this??????


I do the same thing you're describing when I back up stuff to Dropbox and it seems to  work just fine for me. Only difference is I use 7z instead of .zip to archive my stuff.

---

### Post by t0p on 2009-08-03
The problem with using an archive as a "password protected folder" is that when you extract the archive, your "folder" is entirely open.  If, for instance, your computer reboots or powers down suddenly for any reason (such as power supply fluctuation) the contents of the folder have been written to disk, unencrypted, and can be accessed by anyone who has physical access to your machine.

Try [truecrypt]("http://www.truecrypt.org") - powerful, on-the-fly encryption.  I don't think it's in the repos yet, but if you hit the link you should be able to find a .deb perfect for ubuntu.

---

### Post by Dr Small on 2009-08-03
Also, zip passwords can be cracked. I would archive it, then encrypt it with my GPG Public Key, then shred the original archive.

---

### Post by binbash on 2009-08-03
Encrypting via Truecrypt is way more secure than just a password protection.

---

### Post by coldReactive on 2009-08-03
> **Dr Small said:**
> Also, zip passwords can be cracked. I would archive it, then encrypt it with my GPG Public Key, then shred the original archive.

Even worse is that if you use 7-zip to password a zip file, you can open it with Windows Explorer without having to put in the password.

---


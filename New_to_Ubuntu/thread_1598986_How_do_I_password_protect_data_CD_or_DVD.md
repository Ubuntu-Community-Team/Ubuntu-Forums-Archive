---
title: "How do I password protect data CD or DVD?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-17
I would like to burn some folders with data onto a CD or DVD. I would  also like to password protect access to the entire CD or DVD..Is it possible to do it..?I know that i can zip files and give a password but what  i want to do is when the user opens the cd it should prompt for a password and the data should be opened in an explorer..

---

### Post by ronnielsen1 on 2010-10-17
The closest I can find is this:

> You can use the Archive Manager to zip the file and password protect the zip file.

That is probably the closest thing to right clicking and entering a password that you describe.

To do this right click on the file and choose "Compress" then choose zip as the archive type and in "Other options" you have the option to enter a password.

This is simple to do and stops the problem of someone mounting the file system from a live CD and getting the file that way.

Also you can easily email the file or copy to USB stick, etc without having to worry about having the means to unencrypt the files at the other end, you just need the password.

[http://askubuntu.com/questions/4796/how-can-i-simply-password-protect-a-file](http://askubuntu.com/questions/4796/how-can-i-simply-password-protect-a-file)

---

### Post by HermanAB on 2010-10-17
Howdy,

You can and you can't...

If you would encrypt the whole file system on a CD then only a Linux system would be able to read the disc it, since it won't be ISO9660 anymore.  Therefore the usual way to save data securely on a CD is to encrypt a file or archive file and then write it to the disc the usual way.

---


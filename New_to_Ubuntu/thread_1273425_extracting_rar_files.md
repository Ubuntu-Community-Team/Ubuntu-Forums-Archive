---
title: "extracting rar files"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Rob McLean on 2009-09-23
Can anyone advise what I can use to extract downloaded files with the extension.rar?

---

### Post by rampageoberon on 2009-09-23
You can use file-roller which is an archive manager for Gnome. It should already be installed but if not use the below code.

```
sudo aptitude install file-roller
```

You can also use the rar package which is command line driven

---

### Post by cariboo on 2009-09-23
File-roller is installed by default, just double click the file, and file-roller should extract it.

---

### Post by NightwishFan on 2009-09-23
Make sure you have the package unrar installed. Having this package will allow you to extract .rar archives in the GNOME file roller.

Here is a command line code to install it, first open Application -> Accessories -> Terminal. Type the following and push enter. You will need to enter your password when prompted.
```
sudo apt-get install unrar
```

You can also use System -> Administration -> Synaptic Package Manager if you wish to use a graphical interface. Just click the search button and type "unrar". Then click the checkbox.

---


---
title: "Download, Decompress, and Install Application"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mark.intrepid on 2009-02-23
New Ubuntu user.  Trying to download and install medical image viewer 'dicom2' from 

[http://www.barre.nom.fr/medical/dicom2/download-install.html#Install](http://www.barre.nom.fr/medical/dicom2/download-install.html#Install)

I followed the instructions but can't run the program.

Implementing './dicom2' yields error 'Permission denied'.  

Implementing 'sudo ./dicom2' then password yields error 'sudo: ./dicom2: command not found'

How do I get this to run?

Running Ubuntu 8.10

---

### Post by Mark Phelps on 2009-02-23
Try "sudo bash ./<filename>" to invoke the shell directly.

---

### Post by Michael.Godawski on 2009-02-23
hi,

just a guess
have you made the file executable with

```
sudo chmod a+x nameoffile
```?

---

### Post by jespdj on 2009-02-23
Make sure that the program you are trying to run is executable:
```
chmod u+x ./dicom2
```
and then try to run it:
```
./dicom2
```
Don't do things with **sudo** unless it's absolutely necessary (because doing anything under the superuser account is a security risk).

---

### Post by howlingmadhowie on 2009-02-23
> **mark.intrepid said:**
> New Ubuntu user.  Trying to download and install medical image viewer 'dicom2' from 

[http://www.barre.nom.fr/medical/dicom2/download-install.html#Install](http://www.barre.nom.fr/medical/dicom2/download-install.html#Install)

I followed the instructions but can't run the program.

Implementing './dicom2' yields error 'Permission denied'.  

Implementing 'sudo ./dicom2' then password yields error 'sudo: ./dicom2: command not found'

How do I get this to run?

Running Ubuntu 8.10

you don't need to sudo it, but you do need to make it executable. 

try:

```

chmod +x dicom2

```

and then, if you have a 64-bit system:
```

linux32 ./dicom2

```

or just plain old simple:
```

./dicom2

```

---

### Post by mark.intrepid on 2009-02-24
Thanks for the help.

---


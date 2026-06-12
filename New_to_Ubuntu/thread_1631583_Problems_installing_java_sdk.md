---
title: "Problems installing java sdk"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by paul88 on 2010-11-26
I have downloaded the java2 sdk .bin file but when installing i get the following:

```

Do you agree to the above license terms? [yes or no] 
yes      
Unpacking...
tail: cannot open `+365' for reading: No such file or directory
Checksumming...
1
The download file appears to be corrupted.  Please refer
to the Troubleshooting section of the Installation
Instructions on the download page for more information.
Please do not attempt to install this archive file.



```

Thank you for your help.

---

### Post by wojox on 2010-11-28
Did you download from the repo's or the Java website?

---

### Post by akand074 on 2010-11-28
Just download it from the repositories. Open up the Terminal (Accessories > Terminal) and copy paste this:

```
sudo apt-get install sun-java6-jdk
```

---


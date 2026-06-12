---
title: "File roller falsifying package information?"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by jre6 on 2011-03-17
It appears that the File Roller program in Ubuntu 10.10 is trying to display that the two tarballs inside a Debian package (control and data) are simply not there, but just a folder named DEBIAN, where the data of control is stored, and the folders like /usr, /etc and others are displayed as folders after DEBIAN and not in a separate tarball. How to overcome this problem?

---

### Post by TechWiz2100 on 2011-03-17
Umm which package would have 2 tarballs in it? All the packages I've seen open the same way you describe, a Debian folder with more folders within. Are you sure the tarballs are not being opened by File Roller directly and combined as per some specification and that you have the right package?

---

### Post by jre6 on 2011-03-19
All packages have two tarballs. Extract any of the archives with ar (deb is just an ar archive), so type in:

ar -x package.deb

Now, you can see the the two tarballs.

I just want to use something better than ar (trying to avoid the command line as far as possible).

See the file roller screenshot in lucid given below:

Edit : Debian documentation also defines it the same way.

---


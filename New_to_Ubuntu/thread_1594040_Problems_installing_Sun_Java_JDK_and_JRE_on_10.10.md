---
title: "Problems installing Sun Java JDK and JRE on 10.10"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by JJuel on 2010-10-11
I have been trying to install Sun Java JDK and JRE using:
sudo apt-get install sun-java6-jdk or obviously jre at the end for the jre. 

I will then always get this error:

> Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-fonts has no installation candidate

I would like someone to let me know what is wrong and what I can do to right this problem. Thanks

---

### Post by beew on 2010-10-12
Yeah, for some reason sun-java6 is not in the repository anymore (In 10.04 it is in the "Canonical Partners" repository but it doesn't exist in Maverick) Instead you may have to install it from this PPA (which is what I did)

[https://launchpad.net/~sun-java-community-team/+archive/sun-java6]("https://launchpad.net/~sun-java-community-team/+archive/sun-java6")

**EDITED:** But according to this link Sun-Java6 has been uploaded to the official repository as of "today" though it didn't say when was "today". I am pretty sure it wasn't there on Sunday. 

[http://www.webupd8.org/2010/10/sun-java-finally-uploaded-to-ubuntu.html]("http://www.webupd8.org/2010/10/sun-java-finally-uploaded-to-ubuntu.html") 

You may want to try again.

---

### Post by JJuel on 2010-10-12
Thank you! That worked great. It is in the repository if you enable the canonical partners like the second link says!

I would mark this solved but I really don't know how...

edit: figured out how to mark it solved

---

### Post by migs73 on 2010-10-12
Just at the top of the first post, click on thead tools > mark as solved.

---


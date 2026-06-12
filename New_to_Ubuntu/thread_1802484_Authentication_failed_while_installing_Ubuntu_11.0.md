---
title: "Authentication failed while installing Ubuntu 11.04"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by abudhahirs on 2011-07-12
I tried installing Ubuntu 11.04.. but faced problem in the initial step itself. it asked for username and password before the installation started. i tried with various combinations but cud not proceed further. every time the authentication failed. is there any specific username and password for installation? how should i proceed?? some one help please! :(

---

### Post by abudhahirs on 2011-07-12
I tried installing Ubuntu 11.04.. but faced problem in the initial step itself. it asked for username and password before the installation started. i tried with various combinations but cud not proceed further. every time the authentication failed. is there any specific username and password for installation? how should i proceed?? some one help please! :confused:

---

### Post by wildmanne39 on 2011-07-12
> **abudhahirs said:**
> I tried installing Ubuntu 11.04.. but faced problem in the initial step itself. it asked for username and password before the installation started. i tried with various combinations but cud not proceed further. every time the authentication failed. is there any specific username and password for installation? how should i proceed?? some one help please! :(Hi, no it should not ask for a user name or password until you have begun the install process, when you see the screen that says try or install click try and see if it runs on your system good,let us know if it will not let you try out ubuntu. You may have to burn another copy.

---

### Post by coffeecat on 2011-07-12
> **wildmanne39 said:**
> You may have to burn another copy.

+1. Agreed.

@abudhahirs, if you mean you are getting a username and password prompt while using the live CD or live USB, then the commonest cause is a faulty installation medium. Either the downloaded ISO was corrupted or there was a bad burn. Normally you are not prompted for username and password in the live session. The live username is "ubuntu" and the password is blank, but these will not work if the medium is bad.

Check the md5sum of the ISO:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you are burning a CD, always burn at a slow speed - no more than x4 if possible. If you want to check the CD you already have, tap the space bar when you see the two small icons of a keyboard and stick figure at the bottom of a purple screen. You will be taken to a text menu via the language selector. Try the disc integrity check on that menu. It's about third in the list, if I remember correctly.

---


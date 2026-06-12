---
title: "root login problem"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by om.rameshwar on 2010-07-17
Hello everyone

Well, I've jus started using Ubuntu... I've tried to login as root in my terminal but i get the following error:

rameshwar@rameshwar-laptop:~$ su
Password: 
Cannot execute /bin/csh: No such file or directory

so... please help me resolve this problem... :)

---

### Post by Elfy on 2010-07-17
By default, the root account password is locked in Ubuntu.  Use sudo.

If for some reason you need to enable the root account then the information is available.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Gone fishing on 2010-07-17
Ubuntu does not by enable root as it does not conform to the Ubuntu security model. The forum is strict about this (I once had a post removed for telling a user how to enable root)

However if you want a temporary root shell you can use sudo -i

---

### Post by om.rameshwar on 2010-07-17
well i hav tried those commands... but even when i change the password am still getting the same error... i guess there's a problem with the root shell... coz by default we will be using BASH SHELL... but when i try to login, its entering into csh shell... Also, when i enter the command sudo -s /bin/bash/, then i can login as root using the command $ su... 

So, please can u help me in how to change the root shell back to bash frm csh...??

THANKS IN ADVANCE :)

---

### Post by om.rameshwar on 2010-07-17
> **Gone fishing said:**
> Ubuntu does not by enable root as it does not conform to the Ubuntu security model. The forum is strict about this (I once had a post removed for telling a user how to enable root)

However if you want a temporary root shell you can use sudo -i


well atleast can u tell me how to change the root shell...?? that is from csh to bash back as default

---

### Post by Elfy on 2010-07-17
Use sudo -i 

It will want your normal password. 

If you want to use su then the inforamtion is available on the internet. 

Thread closed.

---


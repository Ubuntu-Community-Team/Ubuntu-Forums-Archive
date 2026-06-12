---
title: "Problem with installing winbind"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by pinkfloyd65 on 2005-10-25
Hello everybody,

I have just installed Breezy 5.10 and would like to make it part of a Windows 2003 domain. I read about the changes I need to make to a bunch of files in samba and PAM, but first I appears that I need to install winbind.
I downloaded the winbind_3.0.14a-6ubuntu1_i386.deb. 
When I try to execute it, I get a "archive type not supported" message. 
Did I download the wrong file? If it is the correct package, what am I doing wrong?

Thanks,

PS: In case you didn't notice, I am very new to Linux in general and to Ubuntu in particular. Any suggestion is greatly appreciated.

---

### Post by Samuel on 2005-10-25
the comand to install .deb files is dpkg -i yourfilename.deb
in this case type:
```
sudo dpkg -i winbind_3.0.14a-6ubuntu1_i386.deb
```
i dont know about the program so i cant give you any help setting it up sorry but thats how to install it

but even better would be to use synaptic to install it or:
```
sudo apt-get install winbind
```

---

### Post by pinkfloyd65 on 2005-10-25
Great! the dpkg -i worked! Thank you.

---


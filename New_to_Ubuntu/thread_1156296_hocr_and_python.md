---
title: "hocr and python"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by yaronsiv on 2009-05-11
Hello all,

I am a total beginner in ubuntu and linux, and unfamiliar with most of the terms... nevertheless, i know how to follow orders, so don't be afraid to try to answer!

I've been trying to install the hocr application on my Ubuntu 9.04, but not the version that is in the Ubuntu catalog but rather an updated one. Since it didn't seem to work I contacted the developer, who said that the version is not developed for python 2.6 but to the older version (2.5). I tried to install python 2.5, but since i cannot uninstall 2.6 i think the hocr doesnt recognise 2.5 and still doesnt work.
shall i downgrade my Ubuntu?
or is there a way to notify hocr that it has the possibility to use python 2.5??

thanks allot,

yaron

---

### Post by hw-tph on 2009-05-11
I don't now, but I have had several versions of Python running on Ubuntu/Debian before. You can install python2.5, it shouldn't remove the 2.6 version you already have. The main python executable, /usr/bin/python, is in fact only a symlink to python2.6.

---

### Post by yaronsiv on 2009-05-11
> The main python executable, /usr/bin/python, is in fact only a symlink to python2.6.

thanks alot. how do i 'tell' the hocr when i open it to not use the default python but the older version? is it something that i should do during the installation or some command i have to add to the batching process?

---

### Post by yaronsiv on 2009-05-11
Quote:
 	 	 		 			 				The main python executable, /usr/bin/python, is in fact only a symlink to python2.6. 			 		 	 	 
thanks alot. how do i 'tell' the hocr when i open it to not use the default python but the older version? is it something that i should do during the installation or some command i have to add to the batching process?

---

### Post by durand on 2009-05-11
You can just delete /usr/bin/python and symlink /usr/bin/python2.5 to it.
```
sudo rm -rf /usr/bin/python
sudo ln -s /usr/bin/python2.5 /usr/bin/python
```

That is only a temporary solution though. When python is updated next, that symlink will move back so you should try to find a better method. There is an ubuntu program which changes the default python version but I have no idea what it is called.

---

### Post by hw-tph on 2009-05-12
It appears there is no update-alternatives magic by default for Python: [http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html](http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html)

However, you can still use update-alternatives: [http://codeghar.wordpress.com/2009/01/27/update-alternatives-in-debian/](http://codeghar.wordpress.com/2009/01/27/update-alternatives-in-debian/)

---


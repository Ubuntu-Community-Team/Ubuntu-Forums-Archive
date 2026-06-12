---
title: "XmBlackberry tether failure."
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by azrale on 2008-05-09
Thanks in advance for any response. I am a nub to compiling but i am starting to get the hang of it. Anyways i was able to finally get Xlt installed which was a pain. so i went to install Xmblackberry and it was successful. Now when i go to run XmBlackBerry i get the following error. 

root@jakers-laptop:/home/jakers/Desktop/xmblackberry-0.3.0# XmBlackBerry
XmBlackBerry: error while loading shared libraries: libXlt.so.0: cannot open shared object file: No such file or directory

does anyone know what i am doing wrong. Any help would be great as i would really like to not user windows to tether when i go on trips.

---

### Post by hermes0710 on 2008-05-09
You are missing a library "libXlt" but as i googled it you must manually install it, i didn't see it in any ubuntu package

---

### Post by azrale on 2008-05-09
THANKS MAN!!!! got it to work here is what i had to do to install LibXlt

cd ~
cvs -d :pserver:anonymous@xlt.cvs.sourceforge.net:/cvsroot/xlt co Xlt
cd Xlt
./CVSMake
./configure --prefix=/usr
make
sudo make install 
joe

---


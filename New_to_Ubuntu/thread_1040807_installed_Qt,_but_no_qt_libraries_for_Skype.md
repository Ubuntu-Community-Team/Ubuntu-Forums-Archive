---
title: "installed Qt, but no qt libraries for Skype"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by susiriss on 2009-01-15
Hello all,
             I successfully installed the Qt form source directly downloaded from the Trolltech site. I did the eventual installation with checkinstall with the command, ```
sudo checkinstall sudo make install
```. I modified the PATH variable  in the .bashrc, too.

Now I want to install Skype and downloaded the .deb package from Skype site and tried installing with ```
dpkg -i <skypedebpackage.deb>
```.

But I get an error saying that dependency on qtlib-core or something fails.
My question is do I need to install additional Qt libraries when I have already installed the full Qt package from Trolltech. Or have I missed something in Qt installation.

Thanks.
-susiriss

---

### Post by dummyhead3 on 2009-01-15
Just install what dependencies are missing. Why did you bothe compiling from source anyways?

---

### Post by susiriss on 2009-01-16
Did install from source bcos I did not have a proper Internet connection to my PC.

thanks

---

### Post by susiriss on 2009-01-29
But I guess, like all other development platforms, Qt should install these core libraries when it is installed. In fact, I could see the corresponding shared objects (.so files) in the Qt /lib directory for these "missing libraries" (as reported by package manager). 

I tried ldconfig for the Trolltech/lib directory but no luck.

Any idea ??

Thanks !

---


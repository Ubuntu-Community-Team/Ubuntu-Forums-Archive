---
title: "dpkg -i command not found when installing deb file"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by ugogo on 2010-12-16
Hello

I have ubuntu 8.04 installed.  Someone very clever installed it for me, but he has disappeared.  I love it and am starting to learn all about how to use it, but I am a real green absolute beginner in this.

So anyway, Firefox told me I have a whole bunch of updates i must installed.  I started with the flash player update.  I downloaded the deb file, saved it on my desktop, and double clicked it as per the installation instructions.  All it did was open an archive file.

So I opened the terminal and tried both of the installation commands, and both of them ended up giving me "command not found" errors after I entered my password.

I used the administrator account for this.  

Here is what I tried pasted below. I've removed username and password information and replaced with asterisk.  I entered the password under the line referring to superuser privilege


> c*******@*****-desktop:~$ dpkg -i install_flash_player_10_linux.deb
dpkg: requested operation requires superuser privilege
c*******@*****-desktop:~$  ************
bash: FloggleBat1: command not found


> c*******@*******-desktop:~$ dpkg -i install_flash_player_10_linux.deb
dpkg: requested operation requires superuser privilege
c*******@*****-desktop:~$  *******
bash: FloggleBat1: command not found

Here is where I received the installation instructions from:

[http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3](http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3)

Any help would be appreciated.

---

### Post by nothingspecial on 2010-12-16
Put sudo infront of it, 

or to run the previous command with sudo without having to type it all over again

```
sudo !!
```

---

### Post by ugogo on 2010-12-16
Thanks for the super fast suggestion - unfortunately  that didn't work either.  See below.

I also discovered I actually have Xubuntu 8.10 installed, not Ubuntu 8.04 like I originally thought!

> ........-desktop:~$ sudo dpkg -i install_flash_player_10_linux.deb
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb

> ......................-desktop:~$ sudo dpkg --install install_flash_player_10_linux.deb
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
  Any suggestions would be appreciated.  Thanks!

---

### Post by nothingspecial on 2010-12-16
Where is the file?

If it`s on your Desktop you have to tell the terminal.

```
sudo dpkg -i Desktop/install_flash_player_10_linux.deb
```

Or if it`s in your Downloads folder```


sudo dpkg -i Downloads/install_flash_player_10_linux.deb
```

Or you could just double-click it ;)

---

### Post by oldos2er on 2010-12-16
Right-click on the *deb file, and open it with gdebi. This will install any needed dependencies for you.

---

### Post by ugogo on 2010-12-17
Thank you very much to both of you - both of those methods worked.  

This is my first time ever trying to do something on Xubuntu, and I must say it reminds me very much of DOS.

Very few people in my country seem to know about it.  I think it might be worth my while to learn how to install and maintain this operating system.  Not that I am a technical person by profession, but it just makes sense.  

And I cannot believe how willing this open source community is to assist total strangers.

So that you - not just for me, but for all beginners that you are assisting.

:KS:KS:KS

---


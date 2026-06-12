---
title: "ubuntu 64 insted of 32"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by alfetta79 on 2009-01-21
hi

i am trying to work with ubuntu but i install the 64 version, and my pc is old so he need the 32 version.

the 64 is working but i cant install some add ons like flash.

i downloded the 32 ver but after the first screen its freeze.

any ideas how i format the pc and install the right ver.


thanks

guy

---

### Post by oldos2er on 2009-01-21
If your PC wasn't 64 bit capable, you wouldn't have been able to install the 64 bit version.

 64 bit Flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

 If you still want to install 32 bit Ubuntu, you can download it here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by stchman on 2009-01-21
> **alfetta79 said:**
> hi

i am trying to work with ubuntu but i install the 64 version, and my pc is old so he need the 32 version.

the 64 is working but i cant install some add ons like flash.

i downloded the 32 ver but after the first screen its freeze.

any ideas how i format the pc and install the right ver.


thanks

guy

64 bit Flash is now easy.

Do this in a terminal:

```

cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
sudo apt-get autoremove flashplugin-nonfree
tar -C ~/mozilla/plugins -xvzf ~/libfla*
rm -f ~/libfla*

```

If you have firefox running restart it.

Flash 10 64 bit should work just fine.


After that do this in a terminal

---

### Post by alfetta79 on 2009-01-21
i will try, but i am really new with it

so lets hope

thanks

---

### Post by LowSky on 2009-01-21
Welcome to the forums

follow stchman's instructions and flash will work.
I know from experience, I'm using 64bit edition as well.

---


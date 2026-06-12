---
title: "Java flash player installing know-how..."
date: 2009-01-11
forum: New to Ubuntu
---

### Post by king EZi on 2009-01-11
Hi i downloaded this file 
wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

but then i got no idea how to carry on from there. Please help.

---

### Post by zakirs on 2009-01-11
extract it some where and there is a readme inside it which explais everything

---

### Post by zakirs on 2009-01-11
you basically should ./name of file inside it

---

### Post by taurus on 2009-01-11
1.
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Or 2.
```
cd ~/Desktop
tar xvzf install_flash_player_10_linux.tar.gz
cd install_flash_player_10_linux
sudo ./flashplayer-installer
```

---

### Post by king EZi on 2009-01-11
Thanks, was so scared of opening it.lol. I saw the readme file...thanks again.

---

### Post by king EZi on 2009-01-11
I'm getting an error message:
 Please enter the installation path of the Mozilla, Netscape, or Opera browser (i.e., /usr/lib/mozilla): ##i write## /usr/lib/mozilla

Then i get:

WARNING: Please enter a valid installation path.


Please help.

---

### Post by noelvh on 2009-01-11
As stated above use the restricted extras. It dose all the work for you. When you install from the tar file you end up with allot of work. I think there needs a sim link to firefox for it to work.

I just do
sudo apt-get install ubuntu-restricted-extras and click OK when prompted to.

Noel

Not new to Linux, just to Ubuntu (kubuntu convert)

---


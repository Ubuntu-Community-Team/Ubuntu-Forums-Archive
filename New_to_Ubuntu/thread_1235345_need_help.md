---
title: "need help"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by publicladykilla on 2009-08-09
im trying to install unrar so i can open rar files. i have it downloaded onto my desktops... but how do i install it. id assume id use the terminal but what do i type?

---

### Post by coldReactive on 2009-08-09
You don't download unrar yourself manually in ubuntu.

Go into Terminal (Applications > Accessories > Terminal) and run **sudo apt-get install unrar**.

It'll ask for your password, but typing won't make password characters (or asterisks appear) so make sure you type every character of your password correctly, as you can't backspace.

If you can't do that for some reason, use gksudo instead of sudo.

---

### Post by publicladykilla on 2009-08-09
thanks alot.. now once  i download a rar file how do i use unrar

---

### Post by staf0048 on 2009-08-09
I don't have "unrar" I use "rar" - not sure if they are related or not, but You should be able to just right click on the icon of the file you want to extract and simply "extract here"

---

### Post by zkriesse on 2009-08-09
> **publicladykilla said:**
> im trying to install unrar so i can open rar files. i have it downloaded onto my desktops... but how do i install it. id assume id use the terminal but what do i type?
Hey...a note...whenever you want to install an app you most always use sudo apt-get install whatever the app is....for example if you wanted to install Mozilla Thunderbird. You would type sudo apt-get install mozilla-thunderbird.

---

### Post by coldReactive on 2009-08-09
> **publicladykilla said:**
> thanks alot.. now once  i download a rar file how do i use unrar

Double click a rar file that you want to open or extract. Or install xarchiver from add/remove.

Also, if you want to extract lzh archives, do **sudo apt-get install lha** and open the lzh with xarchiver.

---

### Post by talsemgeest on 2009-08-09
> **publicladykilla said:**
> im trying to install unrar so i can open rar files. i have it downloaded onto my desktops... but how do i install it. id assume id use the terminal but what do i type?
Also, as a side note, please don't forget to use a descriptive title. Just about every thread in this forum is asking for help, so we need something to differentiate between them ;)

Thanks,

talsemgeest

---


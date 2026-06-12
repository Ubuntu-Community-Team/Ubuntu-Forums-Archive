---
title: "how to deinstall an old driver?"
date: 2022-09-21
forum: Networking &amp; Wireless
---

### Post by mustang700 on 2022-09-21
I installed the w-lan driver as following: 

```
sudo apt update
sudo apt install git dkms
sudo  git clone https://github.com/gnab/rtl8812au.git
sudo  cp -r rtl8812au /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo  dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2

```

I found now a newer driver for this realtek, so how do I deinstall the old one?

---

### Post by mikewhatever on 2022-09-21
You can use <dkms uninstall ...>

---

### Post by chili555 on 2022-09-21
I recommend:

```
sudo dkms remove rtl8812au/4.2.2 --all
```

---

### Post by mustang700 on 2022-09-22
well, driver is uninstalled, but I am not able to delete the folder home/..../[COLOR=#000000][FONT=&quot]rtl8812au
I was able to move it into the trashcan, but I am still not able to delete it from there.[/FONT][/COLOR]

---

### Post by mustang700 on 2022-09-22
[COLOR=#000000][COLOR=#000000]as well as:  [/COLOR][/COLOR]/usr/src/rtl8812au-4.2.2/   is still there

---

### Post by chili555 on 2022-09-22
Please do:

```
ls .local/share/Trash/info
```Your files may be located in the info directory. If so, do:

```
sudo rm -r .local/share/Trash/info/rtl8812au

```
And then:

```
sudo rm -r /usr/src/rtl8812au-4.2.2
```

---

### Post by deadflowr on 2022-09-22
To add context to the above post, what happened was you sudo'd the git command which then downloaded the files as root.
Since your user is not root, it will not delete root owned files.
Of the commands you ran, it was the only one that did not require sudo.

---


---
title: "HP Compaq small form factor and enabling internet ."
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by user20002 on 2017-07-04
Help enable cable internet use, with ethernet wire for my computer with , OS, Ubuntu " MATE " , 17.4.

---

### Post by slickymaster on 2017-07-04
Hi user20002, welcome to the forums.

Please have a read at [this sticky]("https://ubuntuforums.org/showthread.php?t=370108") and perform accordingly

---

### Post by user20002 on 2017-07-04
I edited the post. Help enable the internet.

---

### Post by slickymaster on 2017-07-04
Please open a terminal window (Ctrl+Alt+T) and run the following commands```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```This will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself.

---

### Post by user20002 on 2017-07-04
I use ethernet wire.

---

### Post by jeremy31 on 2017-07-04
The wireless script will get us some useful information even if you are trying to use ethernet cable

---

### Post by slickymaster on 2017-07-04
You already been told what you should do in order to get help. Please do what's asked in [this post]("https://ubuntuforums.org/showthread.php?t=2365280&p=13662502&viewfull=1#post13662502")

---

### Post by user20002 on 2017-07-04
I typed the command, you said to put and pressed enter , and says No such file or directory.

---

### Post by slickymaster on 2017-07-04
You have to run the commands one at a time. 

First```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
```Second:```
chmod +x wireless-info && \
```Third```
./wireless-info
```

---

### Post by user20002 on 2017-07-04
I typed the command again and pressed enter and now shows, unable to resolve host address 'github.com

---

### Post by jeremy31 on 2017-07-04
[https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385)
See the offline version, method 2

---

### Post by user20002 on 2017-07-04
Okay

---

### Post by user20002 on 2017-07-04
I put the commands , the way you suggested.

---

### Post by user20002 on 2017-07-04
Nothing shows, when I use method 2 because my computer doesnt use wireless adapters.

---

### Post by lisati on 2017-07-04
If you ran the script, you should have a file "wireless-info.txt" on your computer. Please copy and paste the contents of the file between [noparse]```
 and 
```[/noparse].

---

### Post by user20002 on 2017-07-04
I not need, help from forum. Bye.

---


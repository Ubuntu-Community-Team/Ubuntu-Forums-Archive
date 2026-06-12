---
title: "trying to md5sum"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by 2roombas on 2010-04-08
I am trying to check the md5sum of the kubuntu 10.04 beta 2 I just downloaded, but I'm obviously not doing it right?!   Here are the steps I' taking....

The iso was downloaded to my desktop, so I open the terminal and type
```
cd \
```

I hit enter and I get >

Then I type
```
md5sum kubuntu-10-04-beta2-desktop-i386.iso
```

I hit enter then get this....
```
bash: cd: md5sum: No such file or directory.
```

So what am I doing wrong with this?

---

### Post by adam22 on 2010-04-08
You are not using cd correctly.

cd (change directory) to /home/Desktop by typing
```
cd /home/name/Desktop
```or more simply

```
cd ~/Desktop
``` because ~ is shorthand for /home/name.

Or, open dolphin, go to the Desktop directory, and hit tools>open in terminal.

---

### Post by 2roombas on 2010-04-08
thank you!:)

---

### Post by lovinglinux on 2010-04-08
Want to do it easily, install [CheckIt](http://ubuntuforums.org/showthread.php?t=1449161) extension for Firefox. It allows to select the checksum, select the algorithm and the file to compare from Firefox context menu.

I have created it to make my life easier ;)

---

### Post by adam22 on 2010-04-08
> **2roombas said:**
> thank you!:)

You're welcome.

---


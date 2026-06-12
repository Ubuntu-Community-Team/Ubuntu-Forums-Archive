---
title: "[SOLVED] sun-java5-plugin not available"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-05
sun-java5-plugin doesnt install through terminal... is there substitute for this? 

thank you :popcorn:

---

### Post by Michael.Godawski on 2008-12-05
try
```
sudo apt-get install sun-java6-plugin
```

---

### Post by gandaran on 2008-12-05
> **007casper said:**
> sun-java5-plugin doesnt install through terminal... is there substitute for this? 

thank you :popcorn:
sun-java6-plugin, if you are running ubuntu 8.10 32-bits, java5 is old outdated!

---

### Post by jespdj on 2008-12-05
Which version of Ubuntu are you using?

The latest version of Sun Java is version 6. If you are using 32-bit Ubuntu 8.10 or 8.04, do:
```
sudo apt-get install sun-java6-plugin
```
Note that there's no Sun Java plugin available for 64-bit (yet; it will be there in a few months).

If you're using 64-bit Ubuntu 8.10:
```
sudo apt-get install icedtea6-plugin
```
If you're using 64-bit Ubuntu 8.04:
```
sudo apt-get install icedtea-gcjwebplugin
```
To find out if you're using 32-bit or 64-bit Ubuntu:
```
uname -m
```
i686 = 32-bit, x86_64 = 64-bit

---

### Post by 007casper on 2008-12-06
thank you everyone

I am using intrepid ibex 8.10 64 bit
x86_64

so I should remove java5 and install 6? or could I have both?

---

### Post by Nepherte on 2008-12-06
The answer is already given:
> **jespdj said:**
> If you're using 64-bit Ubuntu 8.10:
```
sudo apt-get install icedtea6-plugin
```


---

### Post by 007casper on 2008-12-06
I know Nepherte... the first question has been answered by jespdj...
thank you... 

>>so I should remove java5 and install 6? or could I have both?

---

### Post by wolfen69 on 2008-12-06
> **007casper said:**
> I know Nepherte... the first question has been answered by jespdj...
thank you... 

>>so I should remove java5 and install 6? or could I have both?

you can't install 6. there is no java plugin for 64bit systems. install the icetea plugin as explained. if java is important to you, use 32 bit ubuntu.

---

### Post by 007casper on 2008-12-06
cheers wolfen69 thank you

---


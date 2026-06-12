---
title: "how to change gcc and g++ version 4.3.3 to 3.5"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by sazz on 2010-05-19
hii
i want to change gcc and g++ version from 4.3.3 to 3.5. I am using ubuntu 9.04. last time i tried to change symlink but the file was broken. 

anyone plz help me with the proper guidelines as I am new to ubuntu. 

thanx in advance

---

### Post by anaconda on 2010-05-19
Might be difficult.

I would install an older version of ubuntu in virtualbox. A version that has the g++ you want. And when I would need the old g++ I would just use the virtualbox...

---

### Post by ibuclaw on 2010-05-19
What on earth are you talking about? [GCC 3.5]("http://gcc.gnu.org/releases.html") doesn't exist. ;)


I think you mean GCC-4.5, in that case, you can get them from launchpad [https://launchpad.net/ubuntu/+source/gcc-4.5/4.5.0-3ubuntu1](https://launchpad.net/ubuntu/+source/gcc-4.5/4.5.0-3ubuntu1)


Or simply build it yourself.

---

### Post by sazz on 2010-05-19
[LEFT]@anaconda, thnx. but can you tell me how i can install virtual box or older version of ubuntu.

@actually i need older version of gcc. it could be gcc 3.5 or any 3.x.x for ubuntu. 
[/LEFT]

---

### Post by gmargo on 2010-05-19
You can install an older 3.x version, but do not remove or change your default gcc.

This PPA has gcc-3.3 and gcc-3.4 compiled for Lucid and other releases:
[https://launchpad.net/~yofel/+archive/off-ppa]("https://launchpad.net/%7Eyofel/+archive/off-ppa")

---

### Post by sazz on 2010-05-20
it is still not working. is there any other way??

---


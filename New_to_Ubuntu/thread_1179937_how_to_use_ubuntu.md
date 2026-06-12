---
title: "how to use ubuntu"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by christian18 on 2009-06-06
hi...i'm juzt newbie in this world of linux/unix system..
please guide me to use this OS..i choose this one cz i think it's possibly easy..:p
the first time after instalation..what do i have to do???

---

### Post by terdon on 2009-06-08
Basically, all you have to do is use it (!). Let us know if you have any specific problems. 

I would also recommend you try out [Linux Mint]("http://www.linuxmint.com") which is based on Ubuntu but even more user friendly for the new user.

---

### Post by lisati on 2009-06-08
> **christian18 said:**
> hi...i'm juzt newbie in this world of linux/unix system..
please guide me to use this OS..i choose this one cz i think it's possibly easy..:p
the first time after instalation..what do i have to do???

Welcome to the world of Ubuntu.
Some information that might help you get started can be found at [https://help.ubuntu.com/9.04/newtoubuntu/C/index.html](https://help.ubuntu.com/9.04/newtoubuntu/C/index.html)
You can also use Ubuntu's "Help" facility, which has some information that you might find usefult - click on the "?" at the top of the screen.

---

### Post by QIII on 2009-06-08
Check out

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by zvacet on 2009-06-08
@ **christian18**

First go to the system>admin>software sources and under Ubuntu software check all except **source** and under update tab check first two.Reload.Now you have added new repositories.System>admin>update manager and update your system.It will ask for password and you will use one you used during installation.

Go to the applications>accessories>terminal and type 

```
sudo apt-get install ubuntu-restricted-extras
```

That will install Flash,java and more for you.At the end add Medibuntu repository as described [here.]("https://help.ubuntu.com/community/Medibuntu") After that go to the system>admin>synaptic and in search box type w32codecs.When you find them install.

If you have more questions just ask.welcome to Ubuntu and enjoy!

---

### Post by joyneo04 on 2009-06-08
first of all welcome to the world of ubuntu.after installing the ubuntu you can run the update anager for any updates...then after as per your requirement you can directly unstall softwares as well as you can first download them and then install them through terminal...now its upto your usage you have to choose the sofwares....in case you have any problem in installing any software then you can visit old post in this forum as well as you can put ur problem here...we all are here to help each other....nothing to worry....ENJOY UBUNTU>>>>>>>

---

### Post by Sef on 2009-06-08
> First go to the system>admin>software sources and under Ubuntu software check all except **source** and under update tab check first two.Reload.Now you have added new repositories.System>admin>update manager and update your system.It will ask for password and you will use one you used during installation.

Go to the applications>accessories>terminal and type 

 	Code:
 	sudo apt-get install ubuntu-restricted-extras 
That will install Flash,java and more for you.

That is the hard way.  

The easy way is Applications > Add/Remove > Show: All Available Applications > Search: Restricted > Click on the box next to Ubuntu Restricted Extras (top choice) > Apply changes > apply > Close.

---


---
title: "quick n easy question ? SSH client"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by abhicool1 on 2010-09-19
I just have  switched  to ubuntu and using KDE, I am very impressed and i will never leave such a great open operating system many thanks to ubuntu developers. 

I am using centos as a web server i wish to connect it via SSH / SHELL but unlike windows i know there is inbuild SSH client in kubuntu. please help me to find that if not please give me a correct direction to download n Install putty for linux.

Thanks in advaance

Abhijeet

---

### Post by k33bz on 2010-09-19
> **abhicool1 said:**
> I just have  switched  to ubuntu and using KDE, I am very impressed and i will never leave such a great open operating system many thanks to ubuntu developers. 

I am using centos as a web server i wish to connect it via SSH / SHELL but unlike windows i know there is inbuild SSH client in kubuntu. please help me to find that if not please give me a correct direction to download n Install putty for linux.

Thanks in advaance

Abhijeet

putty should be in the synaptic manager

---

### Post by abhicool1 on 2010-09-19
> **k33bz said:**
> putty should be in the synaptic manager

Thank you very much ! :)

---

### Post by marshmallow1304 on 2010-09-19
Open up the terminal (I believe the default in KDE is Konsole) and use the ssh command.  See 
```
man ssh
```
for more info.

If you want a GUI, install Putty, as mentioned above.

---

### Post by abhicool1 on 2010-09-19
> **marshmallow1304 said:**
> Open up the terminal (I believe the default in KDE is Konsole) and use the ssh command.  See 
```
man ssh
```for more info.

If you want a GUI, install Putty, as mentioned above.

This will be more effective thanks ! :)

---

### Post by Old *ix Geek on 2010-09-19
Do you want to run this from a command line? If so, it's just **ssh**. You can do this:

```
man ssh
```

to see the manual page for ssh; it'll tell you just about everything you could ever want to know about using ssh!

I know there are GUI frontends, such as **secpanel** available for ssh but I've never tried any.

Whichever way you want to go, the easiest way to install them is via Synaptic. From your menu, System > Synaptic Package Manager

Once in Synaptic type "ssh" in the search box at top, then browse through the list of matches you get to find the app(s) you want and to install them.

---

### Post by k33bz on 2010-09-19
also you could just open up konsole```
ssh username@ip.address.of.server
```

---


---
title: "how do you kde ubuntu?"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by 007casper on 2010-03-02
What is the command line to run kde over gnome on ubuntu?

I know I can use kubuntu, but I read the implementation isnt great.

Thank you.

---

### Post by LowSky on 2010-03-02
```
sudo apt-get install kubuntu-desktop
```


then log out, change the desktop enviroment to KDE

---

### Post by 007casper on 2010-03-02
thank you so much. I am going to try that...

---

### Post by takisan on 2010-03-02
I just launch synaptic and click anything pertaining to KDE-base, KDM, and Oxygen (Dolphin, Konqueror, and more should be automatically checked.)

---

### Post by EssexEagle on 2010-03-02
> **007casper said:**
> I know I can use kubuntu, but I read the implementation isnt great.

What do you mean by the implementation isn't great?  (I use Kubuntu and FWIW I love it!)

---

### Post by wojox on 2010-03-02
You you feel real daring [Backport KDE 4.4]("http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml")

---

### Post by corncob on 2010-03-03
> **LowSky said:**
> ```
sudo apt-get install kubuntu-desktop
```


then log out, change the desktop enviroment to KDE

I did this but how does one change the desktop environment to KDE?  As the only user on this computer I'm bypassing the login screen so I might be missing something there?

---

### Post by philinux on 2010-03-03
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by nothingspecial on 2010-03-03
You do not have to install the whole of kubuntu to try kde

```
sudo apt-get install kde-minimal
```

---

### Post by baddnady23 on 2010-03-03
You'll probably need to set it so that it requires you to log in each start up so that you can select your session type.

Go to:

System->Administration->Login Window  

and change it there.

---


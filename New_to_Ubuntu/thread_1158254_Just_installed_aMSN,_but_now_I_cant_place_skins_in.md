---
title: "Just installed aMSN, but now I cant place skins in the folder..."
date: 2009-05-13
forum: New to Ubuntu
---

### Post by retskrad on 2009-05-13
I just installed amsn v.0.97.2 and I downloaded this skin:
[http://www.amsn-project.net/getURL.php?id=18](http://www.amsn-project.net/getURL.php?id=18)

I saved it on my desktop and clicked "extarct here" then I go to:

/usr/share/amsn/skins

when I put the extracted map there, I get the message:

Access denied.

Whats going on? Just installed ubuntu again, but I have tried google and everything, nothing works, im about to ****** throw the computer of the windows..

I also have Ubuntu 9.04.

---

### Post by retskrad on 2009-05-13
bump

---

### Post by Elfy on 2009-05-13
You need to do that with root rights - you can open nautilus as root - be very careful you can do a lot of damage if you make mistakes.

This will open naultilus in the amsn folder as root

```
gksudo nautilus /usr/share/amsn/skins
```

Right click the folder on the desktop and paste into the skins folder

Alternatively from the terminal

```
sudo cp -R ~/Desktop/WinMSN7 /usr/share/amsn/skins
```

Please do not bump so soon.

---

### Post by retskrad on 2009-05-13
thank you.

---

### Post by m_2009 on 2009-05-13
You can place skins in the follwing location:
 
 
```
~/.amsn/skins/
```
 
and plugins to:
 
```
~/.amsn/plugins
```
 
Beacuse these will be located within your home folder you wont need root access to be able to install the skins/plugins.

---


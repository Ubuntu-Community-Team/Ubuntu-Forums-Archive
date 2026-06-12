---
title: "Bluesoleil"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by LequidMetal on 2010-03-14
I just installed bluesoleil on my 9.10 , but whenever i click on Applications > Accessories > Bluesoleil I get the following error .

[CENTER][ATTACH]150076[/ATTACH][/CENTER]

The application refuses to initialise 

The package was downloaded from IVT's site .

---

### Post by yeats on 2010-03-14
The program is looking in the /opt/bluesoleil directory for the file "bluesoleil_link.sh" - is it there?  If not, find out where it is and you can symbolically link to it:

```
cd /opt/bluesoleil
ln -s */path/to/bluesoleil_link.sh* bluesoleil_link.sh
```

Where */path/to/bluesoleil_link.sh* is the path to the correct location (may need to preface the "ln" command with sudo to work).  This creates a file that points to the file "bluesoleil_link.sh."

---

### Post by LequidMetal on 2010-03-14
It isnt in the opt folder and i have no idea where it installed itself ! . where do files from a default installation generally go ? (.deb file)

---

### Post by yeats on 2010-03-14
A good way to find the file is to use the locate command:

```
locate bluesoleil_link.sh
```

If it is not found, it may be a false negative.  You can update your "locate" database by doing: 

```
sudo updatedb
```

This indexes all the files on your system so it may take a while.

Then try the locate command again.

---

### Post by LequidMetal on 2010-03-14
Nothing was returned even after an update :o

---

### Post by yeats on 2010-03-14
Then try to find where the program files are:

```
locate bluesoleil
```

What steps did you take to install this?

---

### Post by LequidMetal on 2010-03-17
> **chrissharp123 said:**
> Then try to find where the program files are:

```
locate bluesoleil
```


/usr/share/applications/bluesoleil.desktop
/usr/share/icons/hicolor/24x24/apps/bluesoleil.png
/usr/share/icons/hicolor/32x32/apps/bluesoleil.png
/usr/share/icons/hicolor/48x48/apps/bluesoleil.png
/usr/share/icons/hicolor/64x64/apps/bluesoleil.png
/var/lib/dpkg/info/bluesoleil.list
/var/lib/dpkg/info/bluesoleil.postinst
/var/lib/dpkg/info/bluesoleil.postrm
/var/lib/dpkg/info/bluesoleil.preinst
/var/lib/dpkg/info/bluesoleil.prerm

> 
What steps did you take to install this? 

Downloaded the deb file and installed

---

### Post by yahyablora on 2010-07-04
I have different problem with the same bluesoleil bt adaptor. But my problem is that the .deb package i've downloaded from bluesoleil didn't support my current kernel that is newer. What should i do to solve it without downgrading the kernel?
Thanks.

---


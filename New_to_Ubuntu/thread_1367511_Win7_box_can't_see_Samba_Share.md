---
title: "Win7 box can't see Samba Share"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Image0fman on 2009-12-29
I usually share folders of stuff back and forth with my windows and linux pc. I wanted to make this more organized than just right clicking a folder and sharing it so I installed Samba configuration console from the repository. Now my win 7 box can't even see my Linux machine. Any tips/advice is greatly appreciated. Thanks inadvance

---

### Post by stim on 2009-12-29
I'm not sure what configuration tool you are using, but I have successfully set up Samba sharing to my windows 7 box on debian lenny, ubuntu 9.04/8.10/8.04.

```

sudo apt-get install samba

```

```

sudo gedit /etc/samba/smb.conf

```

and copy the section all the way at the bottom with the example, changing file paths and names where applicable.

then 

```

sudo /etc/init.d/samba restart

```

---

### Post by Morbius1 on 2009-12-29
I assumed you not only installed the configuration utility but used it.

Please post the output of the following commands:

Open **Terminal**
type **net usershare info**
type **sudo net usershare info**
type** testparm -s**

Hopefully it's something as simple as using "Classic" samba and Nautilus-share ( right click a folder - share method ) at the same time that's the problem.

---


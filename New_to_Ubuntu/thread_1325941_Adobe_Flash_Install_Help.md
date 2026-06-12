---
title: "Adobe Flash Install Help"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by noeyou on 2009-11-13
Hello, brand new to Ubunto and loving it so far.  I am having trouble installing Adobe Flash Player.  I tried to download both the restricted extras file and Adobe Flash but it keps saying it cannot locate the file for it.  Here is the what itis telling me:

The following partially installed packages will be configured:
  adobe-flashplugin 
0 packages upgraded, 57 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 74.9MB will be used.
Do you want to continue? [Y/n/?] Y
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

I tried downloading the info from the two following sites: 
[http://ubuntu-tutorials.com/2009/10/31/install-flash-and-multimedia-support-on-ubuntu-9-10-karmic-koala/](http://ubuntu-tutorials.com/2009/10/31/install-flash-and-multimedia-support-on-ubuntu-9-10-karmic-koala/)

sudo apt-get install ubuntu-restricted-extrasAny help that can be given to get Adobe Flash downloaded would be greatly appreciated.  I am a very novice user so please dummy it down for me.

Thank you

---

### Post by kansasnoob on 2009-11-13
> **noeyou said:**
> Hello, brand new to Ubunto and loving it so far.  I am having trouble installing Adobe Flash Player.  I tried to download both the restricted extras file and Adobe Flash but it keps saying it cannot locate the file for it.  Here is the what itis telling me:

The following partially installed packages will be configured:
  adobe-flashplugin 
0 packages upgraded, 57 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 74.9MB will be used.
Do you want to continue? [Y/n/?] Y
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

I tried downloading the info from the two following sites: 
[http://ubuntu-tutorials.com/2009/10/31/install-flash-and-multimedia-support-on-ubuntu-9-10-karmic-koala/](http://ubuntu-tutorials.com/2009/10/31/install-flash-and-multimedia-support-on-ubuntu-9-10-karmic-koala/)

sudo apt-get install ubuntu-restricted-extrasAny help that can be given to get Adobe Flash downloaded would be greatly appreciated.  I am a very novice user so please dummy it down for me.

Thank you

Go to System > Administration > Software Sources and make sure that the Partner repo is checked under the Other software tab, then run:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by dlceladon on 2009-11-22
Hi noeyou,

I had a similar problem and I found this link to be particularly helpful to me. Good luck!

[http://ubuntuforums.org/showthread.php?t=1285455&highlight=adobe+error](http://ubuntuforums.org/showthread.php?t=1285455&highlight=adobe+error)

---

### Post by sandyd on 2009-11-22
```

sudo apt-get install flashplugin-installer
```

---


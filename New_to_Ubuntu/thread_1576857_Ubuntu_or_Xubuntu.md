---
title: "Ubuntu or Xubuntu?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by mr_luksom on 2010-09-17
I've recently installed Ubuntu Lucid on an old laptop (Toshiba A80 - 1.7ghz Pentium M 512mb RAM), and I've noticed it lags a little.

Ubuntu has surprisingly good compatibility with the laptops hardware (wireless, sound, graphics).

I'm considering changing to Xubuntu, and I am wondering if I will lose any functionality? My main uses at the moment are Chrome, Evolution, Transmission, Rhythmbox and zsnes.

Do I have to download another iso and completely reinstall? Or is there a simpler way?

---

### Post by Jesus_Valdez on 2010-09-17
If you have enough disk space you can install both of them and choose between them at login.

Check this [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by xumuk37 on 2010-09-18
just ```
sudo apt-get install lxde
``` and select it when you log in ... it's about only 45 Mb.

---

### Post by slakkie on 2010-09-18
> **mr_luksom said:**
> I've recently installed Ubuntu Lucid on an old laptop (Toshiba A80 - 1.7ghz Pentium M 512mb RAM), and I've noticed it lags a little.

Ubuntu has surprisingly good compatibility with the laptops hardware (wireless, sound, graphics).

I'm considering changing to Xubuntu, and I am wondering if I will lose any functionality? My main uses at the moment are Chrome, Evolution, Transmission, Rhythmbox and zsnes.

Do I have to download another iso and completely reinstall? Or is there a simpler way?

You can just install the xubuntu-desktop package (aptitude search tu-desktop to see all desktop packages). All the applications you mention can be installed separately, so there is no real issue in using then in combination with Xubuntu. You might want to remove the ubuntu-desktop packages and all of the dependencies. Have a look here: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by mr.xulu on 2010-09-18
> **slakkie said:**
> You can just install the xubuntu-desktop package (aptitude search tu-desktop to see all desktop packages). All the applications you mention can be installed separately, so there is no real issue in using then in combination with Xubuntu. You might want to remove the ubuntu-desktop packages and all of the dependencies. Have a look here: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)



Hi! In case you try Xubuntu and you don't like it you can remove everything and go back to pure gnome environment. :)

This is the link:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by slooksterpsv on 2010-09-18
> **mr.xulu said:**
> Hi! In case you try Xubuntu and you don't like it you can remove everything and go back to pure gnome environment. :)

This is the link:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

I've done that, it works really well, it will remove any current applications you have installed that the dependencies were removed for, so if you have lots of apps already installed, you may have to reinstall them. But overall, the basic regular functionality will be the same and be all there.

Note: Xubuntu doesn't use OpenOffice.org it uses Abiword and Gnumeric. But you can install OpenOffice if needed.

---

### Post by mr_luksom on 2010-09-18
Thanks for the pointers guys.

I've done it - installed xubuntu-desktop. I'm using it now, performance generally has improved significanlty and everything seems to be working swimmingly!

I do have one ridiculously dumb question though - how do I add application shortcuts to the menu bar? In Gnome, I just dragged them over - doesn't seem to be working for me in xfce.

---

### Post by mr_luksom on 2010-09-18
Nevermind, I figured it out.

Right-click the panel, Add New Items, then select "Launcher". Then you manually add the name, command, icon, etc.

---

### Post by TNT1 on 2010-09-18
> **xumuk37 said:**
> it's about only 45 Mb.

```
After this operation, 43.6MB of additional disk space will be used
```

I just installed it

---


---
title: "Disable Auto login using Terminal"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by SnoopFogg on 2011-07-07
Hi, I only have access to the terminal since upgrading to 11.04.  Can I disable auto login?

Background 

I upgraded to 11.04 on a Revo and now only have a blank desktop with no top or side panels.  I have followed this but had no joy:  [http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html?showComment=1309606247955#c4109511834520525515](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html?showComment=1309606247955#c4109511834520525515).  

In the meantime I would like to switch back to classic gnome, but all the advice to do this is based on having some sort of usable desktop e.g. this was no help:  [http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

I can access the terminal. The Revo is set up to auto login.  If I could disable auto login I should get the option to select classic.  Is there a simple way to do this via the terminal?

Otherwise is there a simple way to use the terminal to switch to classic?

I can't do anything at the moment so any help would be very much appreciated!

---

### Post by wojox on 2011-07-07
You need to remove the custom.conf file or edit it:

```
sudo nano /etc/gdm/custom.conf
```

Change to:

```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true <- Here to [COLOR="Red"]false[/COLOR]
TimedLogin=wojox
AutomaticLogin=wojox
TimedLoginDelay=30
DefaultSession=gnome
```

---

### Post by SnoopFogg on 2011-07-07
Brilliant, thank you very much!

---

### Post by wojox on 2011-07-08
Your welcome.

---


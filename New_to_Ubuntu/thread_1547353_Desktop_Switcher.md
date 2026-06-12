---
title: "Desktop Switcher?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Vol Vox on 2010-08-06
Hello all,

When reading Wikipedia and a few other sites before I downloaded and installed Ubuntu Netbook Edition (thanks to a **very** helpful person here on the forums!), it seemed to say that there was a feature to switch between the 'netbook view' and the 'desktop view'. I have searched and cannot find this fabled Desktop Switcher.

Have I just not looked hard enough? Do I need to download something? Does it even exist?

Thanks for any help with this issue. I can't say I'm in love with Ubuntu, but I think with time it'll grow on me. :D

---

### Post by Matt__ on 2010-08-06
desktop switcher was removed from 10.04 I believe.
you would have to install the packages for desktop ubuntu via terminal or synaptic.
not on ubuntu atm so I cant help you with more details.

if your not running 10.04 then its in the preferences menu (I think)

it might be as simple as ```
sudo apt-get install ubuntu-desktop
```

as the reverse is sudo apt-get install ubuntu-netbook

---

### Post by Elmer Fudd on 2010-08-06
I'm sure someone will come up with the exact place but for now..

I did a netbook install for someone and changed to the normal desktop but don't remember exactly which menu (icon) got me to it. Is is a selection in the System or Bootup/Starup selection- I believe.

---

### Post by davec64 on 2010-08-06
i think what you're after is to change the session?

Start up the netbook and when you get to the login screen, at the bottom is the session button. I think you can change to a standard gnome desktop here. 
If your netbook boots straight to the desktop (no logion screen) just select log out from the closedown menu.

---

### Post by Matt__ on 2010-08-06
> **Matt__ said:**
> 
it might be as simple as ```
sudo apt-get install ubuntu-desktop
```

as the reverse is sudo apt-get install ubuntu-netbook

Ok so scratch what i said here...UNR sits on top of normal desktop ubuntu.

In the 10.04 Remix version you can select the standard Gnome desktop in the dropdown box at login.

or if you dont use a login

To switch from Classic to Remix, or back again, go into System> Administration> Login Screen. There you can set your preferences for your next boot.

hope this solves it for you :)

---

### Post by Old_Grey_Wolf on 2010-08-06
I haven't tried this on my wife's eeePC; however, it may help [http://www.liliputing.com/2009/02/how-to-quickly-switch-ubuntu-netbook-remix-interface-on-and-off.html](http://www.liliputing.com/2009/02/how-to-quickly-switch-ubuntu-netbook-remix-interface-on-and-off.html).

---

### Post by Vol Vox on 2010-08-07
Thanks all! It was so simple, yet so awesome. I love the 'GNOME' desktop. Thanks again.

---


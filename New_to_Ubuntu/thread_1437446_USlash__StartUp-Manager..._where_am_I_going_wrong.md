---
title: "USlash / StartUp-Manager... where am I going wrong?"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by the_jermz on 2010-03-23
Trying to install a new boot splash to replace the boring white logo on the flat black back.  I installed StartUp-Manager like the how to said.  Installed my theme (fingerprint.so).  But nothing but a random color test box thing.  here is the how to I am trying to follow:_[https://lists.ubuntu.com/archives/ubuntu-br/2007-March/018670.html](https://lists.ubuntu.com/archives/ubuntu-br/2007-March/018670.html)_ []("http://ubuntuforums.org/picture.php?albumid=1743&pictureid=5825")  Step 2 does nothing:  
[I][I]sudo gedit /boot/grub/menu.lst
[/I][/I]

---

### Post by friv_livs on 2010-03-23
Start-up manager isn't up to snuff with editing grub.cfg yet.

You are better off looking at grub2 documentation and then:
```
sudo nano /boot/grub/grub.cfg
```

to effect your changes.

-friv_livs

---

### Post by the_jermz on 2010-03-24
err...  I love wasting my time.  Thanks for the info, I'll give it a shot.

---


---
title: "how do I get the restricted drivers back?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by ConXtionS on 2009-10-10
Hi

I upgraded to 9.10 and I no longer have the widget telling me to get the restricted drivers for my nvidia card

How do I get those drivers now?

thanks

Jim

---

### Post by OpenGuard on 2009-10-10
What card do you have ?

---

### Post by ConXtionS on 2009-10-10
jim@mythtv:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
jim@mythtv:~$ 

I think thats it

---

### Post by ConXtionS on 2009-10-10
System -> Administration -> Hardware Drivers

I did that and a widget popped up... 

hope it was the right one...lol

thanks 

Jim

---

### Post by OpenGuard on 2009-10-10
```
sudo apt-get install nvidia-glx-96 nvidia-settings

```

Restart your PC and you should be fine :)

---

### Post by RichardLinx on 2009-10-10
Open the command line: (Ctrl + Alt + F1)
```
sudo dpkg-reconfigure xserver-xorg
```
Accept most the defaults and choose "vesa" as the the driver. Then:
```
startx
```

Edit: OpenGuard has given you a better solution.

---


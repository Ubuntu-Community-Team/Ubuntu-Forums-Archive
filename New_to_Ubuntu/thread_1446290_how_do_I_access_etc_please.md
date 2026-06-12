---
title: "how do I access /etc/ please?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by listerdl on 2010-04-03
Hi how do I access and add the following line to /etc/modprobe.d/alsa-base.conf ?

thanks! 

I am trying to follow a tutorial to get sound!!

---

### Post by NoaHall on 2010-04-03
Open a terminal, and enter ```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Or, if you don't use the Gnome version, you could do

```
a="Some Text"
echo $a | sudo tee -a /etc/modprobe.d/alsa-base.conf 
```

---

### Post by ibuclaw on 2010-04-03
> **NoaHall said:**
> 
```
a="Some text"
sudo echo $a >> /etc/modprobe.d/alsa-base.conf 
```

That won't work. Although 'echo' gets executed as root, as soon as it enters the pipe, it is back to the original user's bash shell, and will return a permissions error.

```
echo $a | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
would be the proper way to do that.

Regards

---

### Post by listerdl on 2010-04-04
thanks

---


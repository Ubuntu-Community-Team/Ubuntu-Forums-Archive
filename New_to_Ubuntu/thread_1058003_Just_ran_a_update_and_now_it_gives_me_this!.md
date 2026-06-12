---
title: "Just ran a update and now it gives me this!"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Repent on 2009-02-02
Any ideas?

[IMG]http://i642.photobucket.com/albums/uu143/Repent203/Screenshot.png[/IMG]

---

### Post by taurus on 2009-02-02
Close the the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Repent on 2009-02-02
Thank You Taurus.

Now when I go to NVIDIA X SERVER SETTINGS it gives me this!

[IMG]http://i642.photobucket.com/albums/uu143/Repent203/Screenshot-1.png[/IMG]

---

### Post by taurus on 2009-02-02
So did you run that command from a terminal first?

```
sudo nvidia-xconfig
```
Then, you have to reboot.

---

### Post by Repent on 2009-02-02
Yes Sir it gave me this reply.

joe203@joe203-desktop:~$ sudo nvidia-xconfig
[sudo] password for joe203: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

joe203@joe203-desktop:~$

---

### Post by taurus on 2009-02-02
The message means that it backed up your original /etc/X11/xorg.conf to /etc/X11/xorg.conf.backup while it generated a new one for nvidia driver.

Reboot again and see if everything is running fine now?

---

### Post by Repent on 2009-02-02
lol.. I'm sorry I did not see were you said (Then, you have to reboot.) I just did and every thing is fine now thank you so much.

---


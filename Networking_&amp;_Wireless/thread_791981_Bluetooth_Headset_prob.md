---
title: "Bluetooth Headset prob"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by illbashu on 2008-05-12
Whenever i try to get my bluetooth headset to connect i get this error 
```
Couldn't display "obex://[00:07:A4:F2:64:E6]/".
Error: Host down
Please select another viewer and try again.
```

my bluetooth headset is this 
[img]http://www.welectronics.com/Bluetooth/motorola_ht820.jpg[/img]
Motorola HT820

And my bluetooth headset is this
[img]http://www.unikoo.com/ebay/photo/bluetooth/BT-004.jpg[/img]

how do i fix this?

---

### Post by illbashu on 2008-05-12
Bump!

---

### Post by illbashu on 2008-05-15
bump!

---

### Post by illbashu on 2008-05-20
Bump!

---

### Post by dmizer on 2008-05-20
have a look here: [http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)

---

### Post by illbashu on 2008-05-21
how do i do this step?

5) Add .asoundrc file to your home directory

and is there a comand to install all the files that i need through terminal?

---

### Post by dmizer on 2008-05-21
to install software:
```
sudo aptitude install softwarename
```

in this specific case, you could use this command:
```
sudo aptitude install bluetooth bluez-audio bluez-gnome bluez-utils
```

as for the linux-ubuntu-modules-(kernel version)-generic, you'll have to figure out your kernel version by looking at the output of this command:
```
uname -r
```

your output will look different from this, but it will look similar to this:
```
2.6.22-14-generic
```
and your insall line will look like this:
```
sudo aptitude install linux-ubuntu-modules-2.6.22-14-generic
```

regarding how to add the .asoundrc file, use this command:
```
touch ~/.asoundrc
```

the dot in front of the file name means that it is a hidden file, so you will not see it when you list your directory but it's there.

you can edit the file via command line with this:
```
nano ~/.asoundrc
```

---

### Post by illbashu on 2008-05-21
Thx, but it didn't work i did all the steps on the other thread :(

---

### Post by dmizer on 2008-05-21
then i suggest you look through the many replies to that thread.  if you still do not find an answer, post in that thread and maybe someone with bluetooth headset experience can help you.

---


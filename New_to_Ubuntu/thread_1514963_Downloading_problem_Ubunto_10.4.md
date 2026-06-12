---
title: "Downloading problem Ubunto 10.4"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by Farmersboy on 2010-06-21
Burned a disc using Infrarecorder at a slow speed and, because I have been having problems wih XP this was removed before installing Ubunto.

Download went ok on step 4 I checked the 'erase and use the entire disc' button

Clicked install which went as far as 5% and the following message came up:

[COLOR=Navy]Creating ext4 file system / in partition #1 of SCS16 (0,0,0)(sda)[/COLOR]

I have given the download a good hour but the installation doesn't go beyond 5%

My computer knowledge is not great:confused: so simple advice please and I have carried out a search before posting

Many thanks

---

### Post by nhasian on 2010-06-21
you should test your hard disk.  boot of the liveCD and in a terminal type:

```
lshw -C disk
```

this will show you the manufacturer and model of your hard disk.  go to the manufacturer's website and download their disk tools to check your hard disk for problems.

also you can go to system-> administration-> disk utility and see if there are any issues in there with your hard disk.

---


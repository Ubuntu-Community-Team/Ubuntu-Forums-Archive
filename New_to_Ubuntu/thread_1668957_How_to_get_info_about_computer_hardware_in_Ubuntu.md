---
title: "How to get info about computer hardware in Ubuntu"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by ravi.krishan1986 on 2011-01-17
Hello Friend,
i m a newbie in Ubuntu, and used Windows before i installed Ubuntu on my computer.

i m not sure whether there is any option in ubuntu to get information of my computer
such as my Motherboard, sound card, display card and lan card info.
how can i get this on a single page without opening my cabinet.

and 
i installed ubuntu on my PC, dual boot (Other OS is winXp). after installing when i boot my computer it shows 4-5 options for Ubuntu.
and one option for Windows.
is it possible to show only two options while selecting OS.:confused::confused:

Thanks

---

### Post by Elfy on 2011-01-17
Hi - some commands to get system information

```
lspci
lsusb
sudo lshw
sudo dmidecode 
```

> when i boot my computer it shows 4-5 options for Ubuntu.You don't say what these are - I suspect that you have kernel update and it's recovery option. You can remove the old kernels so they don't show. 

There is a GUI app that will help - I never remember the name of it - someone will though I'm sure.

---

### Post by CryptSphinx on 2011-01-17
if you want a graphical program to list off your hardware:

If using kde (kubuntu) - click alt+f2 and type in : device viewer
[it should be installed by default]


I'm not sure, but if your using gnome(Ubuntu) you could try install 
gnome-device-manager via synaptic.



and

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

this is a link to a exhaustive article on configuring
grub2 (your boot manager)
so if you want to remove some options the relevant section would be

"7.Removing Entries from Grub 2"



Hope that helps

---

### Post by cascade9 on 2011-01-17
"Hard info" ("system profiler and benchmark") will show you at least some of the information you can get from lshw. 

I prefer lshw myself, but if you like a GUI you might prefer hardinfo.

---


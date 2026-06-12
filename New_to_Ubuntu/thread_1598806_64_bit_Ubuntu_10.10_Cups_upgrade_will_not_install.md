---
title: "64 bit Ubuntu 10.10 Cups upgrade will not install"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by phubert28 on 2010-10-17
"Install Updates" in my Update Manager (removed completely / reinstalled) does not function, but has been identifying updates for CUPS server and PPD manipulation utilities:

cups
cups-ppdc

Using "sudo apt-get updatge && sudo apt-get upgrade"

These STILL are not installed.

?????

---

### Post by diablo75 on 2010-10-17
Try running this command in Terminal:

```
sudo dpkg --configure -a
```

---

### Post by beew on 2010-10-17
We need more information than simply you can't install. What is the error message? 

I think
```

dpkg --configure -a 
``` fixes broken packages but based on what little you tell us I can't assume that you have broken packages. This wouldn't help if it wouldn't install because of dependencies problems or simply because the server is down.

---

### Post by phubert28 on 2010-10-17
Fetched 110kB in 2s (37.4kB/s)                         
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following packages have been kept back:
  cups
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

***

It's a long list of messages,but I didn't see anything I could identify as a causative error message. Lots of Hit's Ign's and a few Get's

It does not appear to say WHY the cups package was kept back"

---

### Post by cariboo on 2010-10-17
Use synaptic to try and install the update, it will tell you what the problem is. There is usually some unmet dependency.

---

### Post by phubert28 on 2010-10-17
Thanks for that suggestion. I'm still having some problem orienting to how things are done in Linux/Ubuntu. I simply didn't connect Synaptic and Update Manager.

Even after complete removal/reinstall, my Update Manager's "Install" button doesn't function which is why I was using terminal to install.

When I checked out cups in Synaptic, its 'box' was gray with an exclamation mark.
After complete removal/reinstall it's back to green.

---


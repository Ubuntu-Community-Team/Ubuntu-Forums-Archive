---
title: "Radeon 5750 drivers and Nvidia"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by HradX on 2010-10-15
Need help  please:

I have a Ubuntu 10.4 only installation.

i3 integrated graphics and a His  ATI 5750  graphics card. 

The Ubuntu  ATI FGLRX drivers are installed but not currently in use. 
 
So I'm assuming the integrated graphics are running. So is there a fix :confused:

Can someone please shed some light on this on this?

HradX

---

### Post by Claus7 on 2010-10-15
Hello and welcome to the forums!

Now let's start cause you have to do some things:

Open synaptic package manager (from System-> Administration) and install these packages:

> fgrlx
fgrlx-dev
fgrlx-amdcccle
fglrx-modaliases
jockey-common
jockey-gtk 

Then go to System->Administration -> Additional drivers and enable the drivers you will see there.

Then type:
```
sudo aticonfig --initial
```

Reboot!

This might not do the trick as you might have to create a xorg.conf file, yet is another story. In case you do, you have to use one like mine from here:
[http://ubuntuforums.org/showpost.php?p=9940327&postcount=15](http://ubuntuforums.org/showpost.php?p=9940327&postcount=15)

Just rename it as xorg.conf , use your own settings for resolution (from your monitors manual) and finally use the name of your graphics card:
type ```
lspci | grep VGA
``` and use what you will see after the**:** .

Hope it helps,
Regards!

edit: what for is nvidia in your title?

---

### Post by HradX on 2010-10-15
:PThanks Claus 7 for the input...

Only minutes ago I just decided to remove the Drivers and then I reinstalled the drivers and had to restart my computer....then wallah!

I have Ati Catalyst working....YES!

Now all I need is Steam for Linux and it's bye bye Microsoft....

I thought the integrated graphics may have been Nvidia....wrong.

My next step is to buy Ubuntu magazine with the extended Ubuntu OS. Could I dual boot both? 

Or will I have to reinstall? One way to find out....One thing for sure Ubuntu Linux is getting better and easier to install.

Regards HradX

---

### Post by Claus7 on 2010-10-15
Hello,

glad you solved your problem!

About steam this might be helpful:
[http://developer.valvesoftware.com/wiki/Steam_under_Linux](http://developer.valvesoftware.com/wiki/Steam_under_Linux)

About extended ubuntu OS I do not get you exactly, yet you might have to start another thread about this and in case you have queries about steam, for that as well.

Regards!

---


---
title: "wirless networking issues"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by cjnodell on 2005-06-02
Ubuntu dosent recognize my wirless network card. I have a no-name network card that has an AMD am1772 chipset. I connect to the internet, using the wirless network card and a DSL router. I have tried a tutorial on the ubuntu wiki about using ndiswrapper, but it didnt work. What can i do. by the way, i am compleatly new to linux so somthing like "compile a driver from the kernal source code" means nothing to me. Any help would be great.

---

### Post by joplass on 2005-06-02
You should be able to have your card working if your windows driver has files of type .sys and .inf.

---

### Post by Psquared on 2005-06-02
[QUOTE=cjnodell]Ubuntu dosent recognize my wirless network card. I have a no-name network card that has an AMD am1772 chipset. I connect to the internet, using the wirless network card and a DSL router. I have tried a tutorial on the ubuntu wiki about using ndiswrapper, but it didnt work. What can i do. by the way, i am compleatly new to linux so somthing like "compile a driver from the kernal source code" means nothing to me. Any help would be great.[/QUOTE]

Has it ever worked or is this your first try?

If you are in Gnome, click on the menu on the upper left and find the network configuration applet and click on it. (I am not in Gnome right now and I can't remember how they are exactly labeled)

Anyway, you will have to enter your user password and then look for your wireless card as either eth0 or eth1. You may have to configure it with your ESSID and WEP key if you have that enabled on your router. After you set it up you should be able to highlight it and click on activate.

---

### Post by cjnodell on 2005-06-03
Hey. My drivr contains an inf and two sys files. It still didnt work... I will check out that network config applet. Thanks for now...

---

### Post by spd106 on 2005-06-04
Hi, there are three wiki pages on this subject, i have found that 
this one [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

is far better than this one
[http://www.ubuntulinux.org/wiki/HowToSetUpNdiswrapper](http://www.ubuntulinux.org/wiki/HowToSetUpNdiswrapper)

the third one is for amd64 users
[http://www.ubuntulinux.org/wiki/HowtoUseNdiswrapperOnAmd64Ubuntu](http://www.ubuntulinux.org/wiki/HowtoUseNdiswrapperOnAmd64Ubuntu)

The first thing to do is try the ndiswrapper-utils package from synaptic. Then use the desktop config tool.

If this is no go then you will have to try the commandline tools.

```
$lspci
```
This will arm you with more info. Go to the ndiswrapper web page and search the list for your card. You may have more luck with a different driver.                                                                           When you install the driver you must have the .inf and .sys files in the current working directory.

Good luck

---


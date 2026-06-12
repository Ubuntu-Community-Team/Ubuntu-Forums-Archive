---
title: "MCP51 network problem"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by Snow24 on 2006-09-12
Ok, I am a big time newb to Linux & Ubuntu. I have read and tried a million things tot fix my problem but have not fixed it yet. I am dual booted with XP on main hard drive and Ubuntu on another hard drive. My setup is a Geforce 6100-939 (AMD3500) which has built in network and video. I can't get my stupid network card to work right. I can ping my dsl modem/router to configure it but I can't go anywhere else. Sometimes synaptic works. I tried to follow the "Installing nVidia's nForce network driver HowTo" but I get something about a xserver is running which I am clueless on how to stop. 

Please help. Very frustrated.

---

### Post by holy_bazooka on 2006-09-12
First of all, the network problem, well i have the same chipset(mcp-51)on my asus motherboard and i never had any problems with it in Linux. as u say it works sometimes and sometimes it doesn't. i think what u need to do is to shut down your computer fully incl. taking out the power cable and then booting it directly in ubuntu. there is an issue with this chipset where if u boot between winxp and linux without shuting down completely, network starts behaving weirdly.

as for the driver issue, just do this, first go to a vitual console by ctrl+alt+f1....f6, then, 

```
sudo /etc/init.d/gdm stop
```

then you can install your driver, afterwards, 

```
sudo /etc/init.d/gdm start
```

hope that helps

---

### Post by Snow24 on 2006-09-12
Well in my great stupidity I uninstall the xserver in synaptic and now I can't boot into Ubuntu at all. I get this blue screen of telling me the xserver is messed up (obviously since I uninstalled it). Is there a way to fix this from the command line or do I need to reinstall. Man that was a stupid thing to do.

---

### Post by holy_bazooka on 2006-09-13
Probably best to reinstall.

---

### Post by Snow24 on 2006-09-13
Well I looked up how to bring back the xserver from the command line so I might do that or I might just reinstall.  We will see. I have a network card laying around so I might throw that in as well. Then finally I might be able to get my graphics card configured right. 

Any words of wisdom on configuring my intergrated video card on my Geforce 6100-939 made by Nvidia as well?

---

### Post by Snow24 on 2006-09-14
Well, I reinstalled and put in a NIC I had laying around but I still had network problems. I read something about IPv6 and decided it was probably that and sure enough it was. I disabled it and internet work like a charm. My video still need help so I was trying ever thing under the sun to get it right but couldn't get it to update to the new drivers or change my resolution. I tried some script and now Ubuntu is screwed up again and I will probably have to reload again.

I am tired of this. Does anyone know the right step for a Geforce 6100-939 to get it working right?

---


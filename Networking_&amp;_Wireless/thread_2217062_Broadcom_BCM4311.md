---
title: "Broadcom BCM4311"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by protoss96 on 2014-04-15
Hi,

I don't know when Ubuntu dropped out-of-the-box driver support for Broadcom [COLOR=#333333][FONT=Ubuntu]BCM4311 but everytime i need to install a new version of Ubuntu i have to install driver manually and i don't like it, because its a pain >.< :/ I am not really very skilled person with making kernel modules and that stuff... I checked this page:
```
[/FONT][/COLOR]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom[COLOR=#333333][FONT=Ubuntu]
```

And it says that [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]BCM4311 isn't supported or am i wrong? By  the way i just wanted to ask if someone knows, will Ubuntu 14.04 support my wireless card out-of-the-box because i am really exited about new LTS release :D, or if not is there some easy way to install [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]BCM4311[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] driver without compiling and stuff. Thank you so much for every helpful reply.

-Cheers, Aleksandar. :)[/FONT][/COLOR]

---

### Post by bazsound on 2014-04-15
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

broadcom wireless support has always been iffy. 

2 options. go with something that is better supported under linux. you can find out what chipsets work well.

or

Once you get it installed, dont reinstall linux. If it aint broke dont fix it. I see no reason to keep installing new versions of ubuntu, you can upgrade when needed, you dont have to upgrade the distro when the newest one comes out. you can wait.

I have a broadcom wireless adapter, its worse for support since you have to use ndiswrapper to use the windows driver.

Reasons for not working out of the box? probably because the firmware is closed source, and due to the licensing of ubuntu non-free stuff sometimes cant be included and it has to be installed afterwords

---

### Post by protoss96 on 2014-04-15
> **bazsound said:**
> [http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

broadcom wireless support has always been iffy. 

2 options. go with something that is better supported under linux. you can find out what chipsets work well.

or

Once you get it installed, dont reinstall linux. If it aint broke dont fix it. I see no reason to keep installing new versions of ubuntu, you can upgrade when needed, you dont have to upgrade the distro when the newest one comes out. you can wait.

I have a broadcom wireless adapter, its worse for support since you have to use ndiswrapper to use the windows driver.

Reasons for not working out of the box? probably because the firmware is closed source, and due to the licensing of ubuntu non-free stuff sometimes cant be included and it has to be installed afterwords

Hi, bazsound and thank you for reply.

I was thinking about new wireless card because how can i see, i am not the only one with this problem, and about open-source there is only b43-fwcutter its a tool that extracts proprietary firmware and firmware-b43-installer is probably firmware for my wireless card, and this stuff is in the ubuntu repositories, i should then try to install drivers from ethernet connection when i am finished installing Ubuntu 14.04. By the way thank you for informations :D

---

### Post by mörgæs on 2014-04-15
A 4311 is easy to get to work. Please read the sticky notes here (moved to Networking and Wireless).

---

### Post by praseodym on 2014-04-15
Install the package **linux-firmware-nonfree**

---

### Post by chili555 on 2014-04-15
> broadcom wireless support has always been iffy. 

2 options. go with something that is better supported under linux. you can find out what chipsets work well.In fact, a few are tricky but most are not. His 4311 works perfectly well with firmware as we shall soon see.

The askubuntu link you gave is, for the most part, a confused and conflicting mess. I should know; I have done considerable work on it myself. It's now a bit less confused, but not much.

The sticky that mörgæs referred to is much better.

---

### Post by protoss96 on 2014-04-16
> **praseodym said:**
> Install the package **linux-firmware-nonfree**

That looks promising, i don't need to install fwcutter anymore >.< Great info thanks :D

---


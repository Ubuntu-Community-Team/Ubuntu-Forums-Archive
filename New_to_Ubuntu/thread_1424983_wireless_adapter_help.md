---
title: "wireless adapter help"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by jklopez on 2010-03-08
[SIZE=3]After installing ubuntu 9.10 everything worked out of the box including my awuos36h usb wireless adapter ,now my issue is when i boot up windows 7 ,which i installed the driver using the disk that came with my adapter ,i get 8 or 9 stong signals and fast internet but when i boot ubuntu i only get 2 or 3 signals and there very weak and in my room where win 7 is also strong with ubuntu it say's i'm connected but if i open firefox i can't load any pages, i just get "connot find server" error ,my usb adapters disk came with drivers for varios windows os,mac and unix linux, the folder that say's unix linux has 2 folders in it, one labled Debian 3.1 driver (kernal 2.6.13) inside that is a zip file labled debian 31-8187(110).zip and the other folder is labled linux driver 2.6.X and inside is a .tar.gz labled rtl8187_linux_26.1025.0328.2007.tar.gz ,if i'm correct and the problen is the driver that ubuntu installed by defult,then witch driver on the disk do i install and how do i install it ,i have no idea on how this is done and would i have to uninstall the driver thats presently in use and if so how do i pull that off....is it the driver or something else,any input,idea or suggestion will be helpfull,  thanx 4 listening.[/SIZE]

---

### Post by AComplex on 2010-03-08
> **jklopez said:**
> [SIZE=3]After installing ubuntu 9.10 everything worked out of the box including my awuos36h usb wireless adapter ,now my issue is when i boot up windows 7 ,which i installed the driver using the disk that came with my adapter ,i get 8 or 9 stong signals and fast internet but when i boot ubuntu i only get 2 or 3 signals and there very weak and in my room where win 7 is also strong with ubuntu it say's i'm connected but if i open firefox i can't load any pages, i just get "connot find server" error ,my usb adapters disk came with drivers for varios windows os,mac and unix linux, the folder that say's unix linux has 2 folders in it, one labled Debian 3.1 driver (kernal 2.6.13) inside that is a zip file labled debian 31-8187(110).zip and the other folder is labled linux driver 2.6.X and inside is a .tar.gz labled rtl8187_linux_26.1025.0328.2007.tar.gz ,if i'm correct and the problen is the driver that ubuntu installed by defult,then witch driver on the disk do i install and how do i install it ,i have no idea on how this is done and would i have to uninstall the driver thats presently in use and if so how do i pull that off....is it the driver or something else,any input,idea or suggestion will be helpfull,  thanx 4 listening.[/SIZE]

I'm also having this problem, any help would be appreciated

---

### Post by 2hot6ft2 on 2010-03-08
There is a newer driver available from realtek here:
[RTL8187L Driver page]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true")

Make sure you get the RTL8187**L** driver NOT the RTL8187**B** or the RTL**8185L**.

You want the one at the bottom of the screenshot below.
Download it to your home folder.

I just read the install instructions and hold on a minute I'll write a simpler way to install it.

---

### Post by 2hot6ft2 on 2010-03-08
Once you have the downloaded driver in your home folder.
Open a terminal
Applications > Accessories > Terminal
and use the following commands one at a time (just copy and paste them into the terminal and hit Enter) then your password and Enter.
```
sudo apt-get install alien
```
once that finishes
```
sudo alien rtl8187L_linux_26.1039.0104.2010.release.tar.gz
```
Once that finishes you should have a
```
rtl8187L_linux_26.1039.0104.2010.release.**deb**
```
file in the home folder you can just double click on to install it.

---

### Post by jklopez on 2010-03-08
when i tried the first command it installed i think and then asked for permission because it was going to occupy more space or something i put y and it tried to establish an internet connection to ubuntu.com but couldn't ,do i procced with the second command or do i have to install it in some other fashion, with ubuntu i have no type of connection ,i had to boot up in windows to post this...

---

### Post by jklopez on 2010-03-09
thanx 4 the help guys...

---

### Post by daboochmeister on 2010-04-26
Guys - can I ask, is this needed for Lucid?  The RTL8187L has kernel modules in place, but I'm having some weird problems (e.g., sometimes works under Gnome, but not KDE [so maybe NM is handling things right where KDE's network manager isn't?]).

In any case, is the driver from Realtek preferred over the in-kernel modules that are in the Lucid kernel?

Thanks!
d.

---


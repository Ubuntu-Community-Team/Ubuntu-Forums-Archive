---
title: "installing ubuntu 4m iso file!!!!!"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by star123 on 2011-01-07
hello every1... i have decided to switch 4m windows to ubuntu.. i m very new to computer..and need assisstance...i have an iso file of ubuntu and wanna install it in virtual box first b4 becoming reguolar user of ubuntu so pls guide me to install ubuntu in virtualbox 4m an iso file... pls be generous as i m not a tech savvy guy..thanks 2 all :p:p:p:p

---

### Post by Verbeck on 2011-01-07
instructions with screenshots @ [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by star123 on 2011-01-07
is it possible to have full dcreen view in virtualbox.? how if yes?

---

### Post by mastablasta on 2011-01-07
why not just use a liveUSB to try it out? USB key can be made persistant, so that settings stay. you only need 1GB USB to do it.
 
it's easy if you use **uNetbootin** or **Linuxlive USB creator** programmes to make a liveUSB.
 
Or a liveCD, but those can't be persistant.

---

### Post by Verbeck on 2011-01-07
> **star123 said:**
> is it possible to have full dcreen view in virtualbox.? how if yes?
you'll need to instal the guest additions first. 
1. in the virtualbox window, go to devices>install guest additions. that would mount a .iso file (a cd icon should appear on your desktop). 

2.double click it and the file browser would open. then press ctrl+L and copy the location.

3. open a terminal (applications>accessories) and enter *sudo*[space]*sh*[space]*ctrl+shift+V/autorun.sh*
(it should look like *sudo sh /path/to/autorun.sh*)

after that, reboot the guest os and if you weren't able to do so before, you can select 'full-screen' or 'seamless mode' from the machine menu

edit: remember that the os would run slow then it normally would if your pc specs aren't good enough, since you're basically running two OS's at once. 
a live usb could be a better choice, so +1 on the previous post

---

### Post by star123 on 2011-01-08
> **Verbeck said:**
> you'll need to instal the guest additions first. 
1. in the virtualbox window, go to devices>install guest additions. that would mount a .iso file (a cd icon should appear on your desktop). 

2.double click it and the file browser would open. then press ctrl+L and copy the location.

3. open a terminal (applications>accessories) and enter *sudo*[space]*sh*[space]*ctrl+shift+V/autorun.sh*
(it should look like *sudo sh /path/to/autorun.sh*)

after that, reboot the guest os and if you weren't able to do so before, you can select 'full-screen' or 'seamless mode' from the machine menu

edit: remember that the os would run slow then it normally would if your pc specs aren't good enough, since you're basically running two OS's at once. 
a live usb could be a better choice, so +1 on the previous post


thanx 4 ur help.. but regarding the prob of fullscreen.. i cud not find seemless option in machine menu... i have oracle virtual box

---

### Post by sandyd on 2011-01-08
Im not suppsoed to post images fulsize, but so you get the idea...
[http://img268.imageshack.us/img268/8830/snapshot12v.png](http://img268.imageshack.us/img268/8830/snapshot12v.png)

and please kill the "4"s in your sentances.

---

### Post by star123 on 2011-01-08
> **sandyd said:**
> Im not suppsoed to post images fulsize, but so you get the idea...
[http://img268.imageshack.us/img268/8830/snapshot12v.png](http://img268.imageshack.us/img268/8830/snapshot12v.png)

and please kill the "4"s in your sentances.

thanx for such an illustrative figure. the problem is even in fullscreen mode its not covering the entire screen only some 2/3 screen is covered remaining is a black background

---

### Post by sandyd on 2011-01-09
> **star123 said:**
> thanx for such an illustrative figure. the problem is even in fullscreen mode its not covering the entire screen only some 2/3 screen is covered remaining is a black background
install the guest additions

---


---
title: "No Wifi in Ubuntu 9.10?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Running_Dualboot on 2010-04-03
I and running Ubuntu 9.10 Karmic Kola and It won't let me use wireless. I have an HP Dv6-1230US (Pavilion). Help me out?:guitar:

---

### Post by Joshcush on 2010-04-03
You are probably missing a proprietary driver. 

Is there any way you can connect to the net using a Ethernet cable? If you can connect using an Ethernet, you should be able to install the driver manually.

To do this go to   System->Administration->Hardware Drivers

Hope this helps :)

---

### Post by Piro24 on 2010-04-03
I'm not sure what kind of Chipset is used in your laptop, but you'd more than likely be able to use Ndiswrapper, a program that allows you to use Windows drivers in Linux. 

I used to have to use that and it worked great, so check it out if there's no stable/good driver for your wi-fi card.

---

### Post by anewguy on 2010-04-04
Please do the following:

- open a terminal window (applications/accessories/terminal)

- type:

lspci <press enter>

lsusb <press enter>

Please post the output of both of these back here so we can see what type of device chipset you have and guide you better on what to do.

Dave ;)

---

### Post by mcoleman44 on 2010-04-04
sudo apt-get update
sudo apt-get upgrade
sudo reboot

You should now have your wireless driver listed under system>admin>hardware drivers

---

### Post by Running_Dualboot on 2010-04-06
> **anewguy said:**
> Please do the following:

- open a terminal window (applications/accessories/terminal)

- type:

lspci <press enter>

lsusb <press enter>

Please post the output of both of these back here so we can see what type of device chipset you have and guide you better on what to do.

Dave ;)




Results for LSPCI : [http://tinypic.com/r/iml7kp/5](http://tinypic.com/r/iml7kp/5)


Results for LSUSB : [http://tinypic.com/r/4ih2cz/5](http://tinypic.com/r/4ih2cz/5)


Oh, and when I tried to do the Apt-get update thing it crashed my Ubuntu part of the computer. I re-installed it and those are the results.

---

### Post by DarkStar786 on 2010-04-06
I've been having the same problem with my netbook, on my desktop this problem doesn't seem to occur, i couldn't find a solution so i moved over to Ubuntu 8.04 seems to work fine there...

---

### Post by anewguy on 2010-04-10
According to the outputs you posted in the pictures, your wireless is Broadcom 4322.  That requires a driver before it can work.  Please check under the system  menu for restricted drivers - if one shows enable it.  I haven't done so, but others have posted that if you can hard-wire to an ethernet connection, you can do sudo apt-get update, followed by sudo apt-get upgrade and reboot then see if the wireless is there.  Before I post more here, try searching the forum with broadcom 4322, and if you don't find an answer that way (you should) you can always try a Google, Yahoo or whoever search using ubuntu 9.10 broadcom 4322 driver.

If worse comes to absolute worse, we can use the Windows driver and a program called ndiswrapper to have Linux use those drivers.

Post back with any questions, comments, or need to try ndiswrapper.

Dave ;)

---

### Post by Running_Dualboot on 2010-04-13
[SOLVED]


Thanks guys!

---


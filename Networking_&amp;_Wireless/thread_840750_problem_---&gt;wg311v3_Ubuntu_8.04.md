---
title: "problem ---&gt;wg311v3 Ubuntu 8.04"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by agel1 on 2008-06-25
i'm using ubuntu 8.04 and netgear wg311v3

i follow this guide but didn't work, maybe i did something wrong

---------------------------------------
I installed Ubuntu 8.04 today and faced this problem of WiFi again but ths time even installing ndiswrapper diddnt worked so had to find a way to make WiFi work on boot and here it is

For this First You need to install ndiswrapper, no need for net coz the packages are included in the CD / DVD of Ubuntu just go to System>>Administration>>software sources then uncheck all downloadable from internet, Third party and Update repo’s only select Installable from CD-ROM/DVD. Now open a Add/Remove from Applications>>Add/Remove.. there select all avaliable appliactions in show, now seach for ndis you will see Windows Wireless Drivers select it and click Apply changes it will ask you for the CD insert the CD and it will get installed, now you just have to install the drivers of your card for this open System>>Administration>>Windows Wireless Drivers and install the windows wireless drivers ( bcmwl5.inf for hp6515b bcm4312) now follow these steps, type
sudo -i now you must be as root then type
nano /etc/rc.local the file should read
rmmod ndiswrapper
rmmod ssb
modprobe ndiswrapper
exit 0

all done now just reboot and enjoy your Linux……..
-----------------------------------------------------


i install ndiswrapper and the driver without problem folowing the guide

what i think i did wrong was
---------------------------------------------
open the terminal

type

sudo -i 

(press enter) 

then i paste the 5 lines together

nano /etc/rc.local 
rmmod ndiswrapper
rmmod ssb
modprobe ndiswrapper
exit 0

(press enter) 
-----------------------------------------------
every time i try to connect to my unsecure wireless network the computer freeze and the keyboard lights start flashing

i try with windows 2000 and windows xp drivers

thanks

---

### Post by chili555 on 2008-06-25
> what i think i did wrong wasHey, [people make mistakes! Even old chili$

Do not try to connect before you open a terminal and type:```
cat /etc/rc.local > local.txt
```A text file will be created in your user directory called local.txt. Transfer it by thumb drive or otherwise to a computer with a working connection, post it here and we will examine it and guide you step-by-step to fix it.> then i paste the 5 lines togetherOuch!

---

### Post by agel1 on 2008-06-25
here is local.txt


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

---

### Post by chili555 on 2008-06-26
Open a terminal and do:```
sudo gedit /etc/rc.local
```The text editor, gedit will open with your file ready to edit. Type in the lines so the file looks like this:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod ndiswrapper
rmmod ssb
modprobe ndiswrapper

exit 0
```Proofread carefully, press the 'Save' button and close gedit. Now reboot and see if you connect or freeze.

---

### Post by agel1 on 2008-06-26
thank you chili555, did what you said and freeze again

---

### Post by agel1 on 2008-06-27
can somebody recommend a cheap (usb wireless card that works out of the box in ubuntu)

thanks

---

### Post by agel1 on 2008-06-28
i think maybe is impossible to get this card (wg311v3) to work, maybe i buy (Linksys WUSB54GC USB 2.0 Wireless Adapter) i think work out of the box

---

### Post by agel1 on 2008-07-01
i reset my router and wg311v3 is working with wpa, the only thing i change in my router settings was the name of the wireless network, previous name was too long

---


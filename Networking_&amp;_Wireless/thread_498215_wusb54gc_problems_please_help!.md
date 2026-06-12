---
title: "wusb54gc problems please help!"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by edwin.e.johnson on 2007-07-11
here is my problem..  plug in my usb wireless and it seems all good i caN see my network and i can start to connect to it enter wep key but nothing! it just tries and tries... its the rt73 chipset aND im using the t73usb driver that feisty assigned to it.. when i look at my network connections it showes 2 wireless cards... i tried to use the ndiswrapper and windows xp drivers still nothing . this is my only access to the internet from that machine can anyone help me trouble shoot this thing?  

thankyou

anything at all will help i have tried every thread on this site and linuxquestions that had any connection to this problem still no luck

---

### Post by edwin.e.johnson on 2007-07-11
noone has gottin this to work without a hardwire internet connection?

---

### Post by ~cyrus~ on 2007-07-11
Follow this brilliant [HOWTO: RT73 (RT71) serialmonkey drivers]("http://ubuntuforums.org/showthread.php?t=400236") by [diepruis]("http://ubuntuforums.org/member.php?u=130971")

Should do the trick...!

---

### Post by edwin.e.johnson on 2007-07-11
as it turns out i dont have a hardline internet connection on the computer im tring to get this to work on. the only connection i can get is wireless. and it wont connect does anyone have a solution i know someone has done this.

i tried blacklisting the rt73use drivers and install ndiswrapper and used the windows driver still wont work..

anything please

---

### Post by edwin.e.johnson on 2007-07-11
someone anyone!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

anyhow it work under mandriva but im not to happy with the way commands are run on that distro.. at least not yet. maybe this problem will be fixed in 7.10???

if anyone can help please help.

thankyou

---

### Post by edwin.e.johnson on 2007-07-11
how can noone have had a fix to this problem i seen the same question plastered all over the internet but with no fix for the offline user.................................




SOMEONE HELP

---

### Post by hendricks on 2007-08-03
Please check out this thread I started if you are still having problems:

[http://ubuntuforums.org/showthread.php?p=3127959#post3127959]("http://ubuntuforums.org/showthread.php?p=3127959#post3127959")

  --Hendricks

---

### Post by kevdog on 2007-08-03
I would recommend the serial monkey driver fix.  You only need another computer to download one file (the serial monkey rt73 driver file), and then transfer this to your wirless computer via a USB stick.  Im sure you have access to one computer you can do this from.  Beyond this one step, you dont need an internet connection. You will however need the Ubuntu installation disk to install additional packages.

---

### Post by boem on 2007-08-28
or you can use ndiswrapper successfully as I did.

[http://ubuntuforums.org/showthread.php?t=534865&highlight=wusb54gc]("http://ubuntuforums.org/showthread.php?t=534865&highlight=wusb54gc")

good luck!

---


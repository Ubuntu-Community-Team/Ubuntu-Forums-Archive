---
title: "Atheros Wireless"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by hasek522 on 2008-09-09
Hello,

   I have an Atheros AR5007 802.11b/g WiFi Adapter on my HP laptop.  I just recently installed Ubuntu 64 bit but have been unable to get my wireless working.  There is no wireless option and no wireless networks appear.  A couples additional peices of information:

The card works fine on Vista

Under restricted drivers the Atheros Driver is listed as being installed.

Any one know how to get the wireless working?

---

### Post by lilmale1 on 2008-09-09
[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

that is for your card

i got it from here
[http://www.atheros.cz/](http://www.atheros.cz/)

---

### Post by lilmale1 on 2008-09-09
get the tar.gz one and i'll tell you how to install it

---

### Post by lilmale1 on 2008-09-09
at terminal wich is in the menu under applications tab

open terminal and type: [COLOR="red"]su[/COLOR]
then type your password

then type the following after you have place the file in your name tree. or directory i should say.

mine is xbatis. yours is the directory where you have your name of you computer in that directory put the tar.gz file of madwifi you downloaded.

then you will go to terminal

after you have typed your password

type command:

 [COLOR="Red"]tar -zxvf madwifi-0.9.4.tar.gz[/COLOR]         


it will extract your file

you will type

commant: 

[COLOR="red"]cd /home/xbatis/madwifi-0.9.4[/COLOR]
 
check. that i put xbatis but it should be your computer name


then after type when it looks like

root@xbatis-desktop:/home/xbatis/madwifi-0.9.4# [COLOR="red"]make[/COLOR]


and then type command:


root@xbatis-desktop:/home/xbatis/madwifi-0.9.4# [COLOR="red"]make install[/COLOR]

---

### Post by lilmale1 on 2008-09-09
and then you will need wifi radar

which its better than configuring more other things on your network connection

---


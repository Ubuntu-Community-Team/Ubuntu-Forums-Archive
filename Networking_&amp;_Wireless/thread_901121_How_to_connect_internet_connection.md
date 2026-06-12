---
title: "How to connect internet connection"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by filesharer on 2008-08-26
Hello everyone,

I am file sharer from India.I have an internet connect with MTNL.
I am unable to setup network connection.Man concerning to internet services in MTNL also gave me a modem and a CD. But my computer could not read the CD.
Plz suggest me what may be the problem?Is there any problem with mode?

---

### Post by Iowan on 2008-08-27
CD is probably Windows-based.  You might configure Ubuntu for DHCP and restart.  If your luck is better than mine, the modem will act as DHCP Server and all will work. I doubt that will be the case.
... but I gave your thread a bump, so maybe better advice will notice.

---

### Post by zedx555 on 2008-10-07
Well if you are still there and for future MTNL users...




1) This is for those who are connected by ethernet. I don't know about USB... it may / may not work...




2) Open Firefox and type [http://192.168.1.1](http://192.168.1.1) and press enter. You may ask    your MTNL man to set all the values or to do by yourself :
         2.a) Default password and username are admin. enter and login.
         2.b) Go to Setup -> triband
         2.c) Enter all the values. Ask MTNL if you don't know. In my case,
              the correct values were  already entered. Press apply.
         2.d) Go to Tools -> System Commands and click on Save All.




3) Reboot Ubuntu.



4)  Go to System -> Administration -> Network



5) Click Unblock and enter your Username and Password. 



6) There should be a 'Wired Connection' Icon. Select it and click on Properties. In Configuration, choose Static IP address. Enter the IP address, Gateway address and Subnet Mask there. These correspond to the IP Adress, Default Gateway and Subnet Mask values in Windows XP Network configuration. Ask the MTNL man if you don't know. If you want to know these values from Windows, then :
           6.a) Right Click on My Network Places and click on Properties.
           6.b) Right Click on the working Local Area Network Connection
                and click properties. Click on Internet 
                Protocol(Don't click on the checkbox!)  and 
                click on properties.
           6.c) Write IP Adress, Default Gateway, Subnet 
                Mask Preferred DNS server and Alternate DNS
                Server  on a piece of paper.




              

7) Go to DNS (In Ubuntu System -> Admin -> Network of course!) and click on Add. Enter the value that is 'Preferred DNS' In step 6.c) and press Enter. Click Add again and enter the value that is 'Alternate DNS server' in step 6.c) and click on Close.

8) Your MTNL broadband should be working. 






I configured mine in Xubuntu Hardy a month ago but I might have missed a step or two. Don't forget to experiment if it doesn't work!

---


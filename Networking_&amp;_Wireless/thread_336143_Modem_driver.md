---
title: "Modem driver"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by blade575 on 2007-01-11
First Hi to everyone on this forum. I have a problem with setting my internet connection from ubuntu 6.10 Edgy Eft. I can not find proper modem driver for my dial up connection. I was hoping that someone will help me determine which driver i need and  direct me to some instructions how to install and setup connection. I scaned system with scan modem utillity and got information on attached file.
thanks and sorry for bad english

---

### Post by tagginannie on 2007-01-11
> **blade575 said:**
> First Hi to everyone on this forum. I have a problem with setting my internet connection from ubuntu 6.10 Edgy Eft. I can not find proper modem driver for my dial up connection. I was hoping that someone will help me determine which driver i need and  direct me to some instructions how to install and setup connection. I scaned system with scan modem utillity and got information on attached file.
thanks and sorry for bad english

You don't need a driver all you have to do is first go /etc/ppp/ and right click on the 
"Options" file and go to actions->edit as root. Look for the word "auth" and put a "#" befor 
it so it will look like this "#auth" now save.Now go to your home folder and right clck and 
choose "creat new->text file and save it as a blank file and name it "resolv.conf", open the
terminal witch you can find in system tools of the menu and type "sudo cp resolv.conf 
/etc/resolv.conf.Now start the gnome network config or KPPP and enter the name of your 
ISP and access number.Now click on modem and enter your modem name and change 
the speed to 57600. Dont bother with querying the modem because Ubuntu will not detect
it, that only works after you have connected to your ISP. Close the boxes, now enter your
user name and password and click connect

BTW, if you can't see any of the sub-directories that is because they are hidden to view them in Gnome and Konqueror clickon view show hidden files 

Suzy

---

### Post by blade575 on 2007-01-23
I have tried everything you said but it did not work for me. After I enter my username, password and set speed to 57600 inside Gnome ppp it does not connect becouse modem is not found. I dont understand how can I connect  to ISP first if modem is not detected.
Maybe I did something wrong before that. When I did "sudo cp resolv.conf 
/etc/resolv.conf" both documents (resolv.conf in home directory and resolv .conf in etc directory) were empty, is that suposed to be like that? When I open Gnome ppp-modem, modem name is /dev/modem, should i change it? And the last question: inside Gnome ppp I did not find option to enter my ISP name, only username and password?
Thanks

---


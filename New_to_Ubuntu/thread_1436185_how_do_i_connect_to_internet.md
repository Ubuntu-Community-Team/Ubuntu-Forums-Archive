---
title: "how do i connect to internet ?"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by mastikhor_maddy on 2010-03-22
How do i connect to internet in ubuntu 9.04 i have a broadband connection which requires username and password in windows i connect the following way

---

### Post by mastikhor_maddy on 2010-03-22
plzz help me guys its urgent

---

### Post by Gone fishing on 2010-03-22
have a look at this:

[http://www.indiabroadband.net/linux/10828-how-configure-bsnl-broadband-connection-ubuntu.html](http://www.indiabroadband.net/linux/10828-how-configure-bsnl-broadband-connection-ubuntu.html)

---

### Post by mastikhor_maddy on 2010-03-22
Taskbar >> System >> Administration >> Network.
i dont hav netowrk in Administration

---

### Post by Gone fishing on 2010-03-22
Ok got the message 

"i dont have network in Administration"

That for older ubuntus I think its easier - right click the networking applet on the top panel. Then select Edit connections, select DSL click add. You can then add username, password service etc

---

### Post by dineshs on 2010-03-23
Actually you are using Bridge mode which requires a PPPoE dialler.But I suggest you to use an always on mode -that is a DSL modem can be configured with your username and password.
If you do this you need not use dialler in Windows or Ubuntu.Just open browser and type the site.To do this follow configure modem as in
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
under CPE configuration
If you want to use the dialler(the same methd you are using at present) -Pl read this
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by khushalb on 2010-07-20
What if I need a PPPOE Dialer. Is it possible to have a pppoe dialer so that I can connect to the internet when I want to.

---

### Post by dineshs on 2010-07-20
You can configure  DSL tab in Network manager

---

### Post by dineshs on 2010-07-20
Right-click NM icon(top right of the panel) - click Edit Connections. 
Select DSL tab - click add - Enter username and password-tick available to all users-apply(connection name =DSL connection by default)
Now to connect DSL click on NM icon click `DSL connection'

---

### Post by TopEnder on 2010-12-07
> **dineshs said:**
> Right-click on the NM icon( on top right of the panel) and then click on Edit Connections. 
Select the tab DSL - click add - Enter username and password-tick available to all users-apply(connection name =DSL connection by default)
note:If you want a particular DNS to be used, manually set DNS under ipv4 -automatic PPPoE addresses only , give DNS and apply eg:4.2.2.1)
Now to connect DSL click on NM icon click `DSL connection'

Followed your instructions ( Step 1, Step II and Step III.   The problem I have is as I have no NM icon in either top or bottom panel, how can I connect to DSL?

Thanks for the help so far, TopEnder

---

### Post by vasa1 on 2011-08-13
> **dineshs said:**
> Right-click NM icon(top right of the panel) - click Edit Connections. 
Select DSL tab - click add - Enter username and password-tick available to all users-apply(connection name =DSL connection by default)
Now to connect DSL click on NM icon click `DSL connection'

Hi Dinesh ...
Do you have any idea about how or whether NM can be made to redial ***several times*** when a connection drops and not just once?

---


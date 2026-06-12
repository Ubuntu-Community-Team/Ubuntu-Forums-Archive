---
title: "Kismet and Atheros Card / Madwifi"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by savien on 2007-01-26
Hey all!

I am a relatively new Linux user and I am trying to learn.  I have been working on getting Kismet working on my laptop and I have encountered many problems and most of which I have been able to work through.  I have kismet installed however the issue I have has to do with the capture source type.  When I run kismet I have the following error.

Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to oscar (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'madwifi_g' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.


I have downloaded and i " BELIEVE " installed correctly the latest madwifi drivers from madwifi.org.  (on a side note is there some way to verify the drivers? )  

Any help? Thanks!

---

### Post by piotrwoj on 2007-01-27
Hey!
My English is very weak and he writes for the help of translating program
See as the configuration file looks at me. My Atheros Card based on an single chipset 5005.
Link to kismet.conf is here: [www.domar.biz.pl/download/kismet.conf]("http://www.domar.biz.pl/download/kismet.conf") 
You probably use madwifi-ng (not old madwifi)
In the line change:
source=madwifing_g,wifi0,atheros
Bye!, Piotrwoj, PL, skype piotr_wojciechowski, web: [drzwi]("http://www.domar.biz.pl")

---

### Post by March20 on 2007-03-07
same problem... and can somebody tell me how to uninstall kismet 2007? i compiled it from source.

---

### Post by piotrwoj on 2007-10-04
> **March20 said:**
> same problem... and can somebody tell me how to uninstall kismet 2007? i compiled it from source.
From suorce You run command: make uninstall.
apt-get install kismet is good idea
linux-restricted-drivers including madwifi work bad with single chip 5005. The best is from madwifi complied driver madwifi-ng with wlanconfig utility. In my works extra!
---------------------------------------------------------------------------------------
Bye!, Piotrwoj, PL, skype piotr_wojciechowski, web: [drzwi]("http://www.domar.biz.pl/")

---


---
title: "[SOLVED] Mrtg conf files"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by alynx on 2008-10-03
Hi

I have a problem with mrtg.conf files.

I dont want every single site to be shown in the localhost/mrtg when i view them in my browser.

I tried to make a new folder home/***/mrtg and put all my mrtg.conf files in there. This means site1.cfg site2.cfg site3.cfg and so on.

then i made indexmaker for all the new cfg files and that works out aswell. The problem is that the cron job is set to do /etc/mrtg.cfg. DO i have to make a cron job on every single cfg file ? Or is it any easier way to do this ?

Thanks in advance
Alynx

---

### Post by alynx on 2008-10-06
Issue solved !  Kudos to my old workmate who helped out 

I decided to make the setup on mrtg like this :

/etc/mrtg/cfg-files  <---- Stores cfg for every switch i've run cfgmaker on.


/etc/mrtg/cfg-location <------i make 1 cfg file for every location in here with Include: /etc/mrtg/cfg-files/appropriate_cfg_files

/etc/mrtg.conf <-------- is still in cron job and the only tekst i have in this is Include: /etc/cfg-location/appropriate_cfg_files

To get theese up and running in a browser i do indexmaker /etc/mrtg/cfg-location/appropriate_cfg_file > /var/www/mrtg/example_one

then i go to the /var/www/index.html file and make a hyperlink to my desired location , in this case example_one.

Hope this is of some use to anyone out there:guitar:

---


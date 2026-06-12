---
title: "Ubuntu (client) to access internet via WinXP (host)"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by ChengTng on 2008-06-25
Hi,

I am a newbie here. Would like to ask a question regards to the above problem.

I have a XP PC connected to internet via wireless GSM. This PC is connected to a LAN (router) wirelessly. Another laptop with ubuntu is connected(wired) to the same LAN.

I ping from the ubuntu laptop to the PC, no problem. I think I would need to set some gateway IP somewhere.
On XP side, I have configure shared internet access.

Would appreciate any help. And also is there any other settings needed to be done?

Thanks in advance.

---

### Post by dmizer on 2008-06-25
well, if you can ping windows from ubuntu, your ubuntu machine is all set.

you'll need to configure your windows machine for internet connection sharing.  here's the howto i used when i did it the first time: [http://www.homenethelp.com/connection-sharing.asp](http://www.homenethelp.com/connection-sharing.asp)

---

### Post by superprash2003 on 2008-06-25
when you configure windows to ICS.. then your ubuntu ethernet card should be set to DHCP under system->admin->network ..

---

### Post by ChengTng on 2008-06-25
Thanks for all helps! 

dmizer, it works now. thanks for your help! 

superprash2003, I did not check that portion, as I did not change any setting there. Will check if it already set as your advise. Thanks for your recommend.

---


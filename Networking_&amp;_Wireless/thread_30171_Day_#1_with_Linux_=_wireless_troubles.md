---
title: "Day #1 with Linux = wireless troubles"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by shamrog12 on 2005-04-27
I have a wireless D-Link DWL-520 and I've looked at other threads for help but haven't been able to make use of them.  I found the Networking portion of the System menu and my wireless card isn't listed in there.  What can I do?

I'm a REAL linux newbie so please take that into consideration when you tell me how to do this.  ](*,) 

Thanks a million.

---

### Post by az on 2005-04-27
[http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)

If you have a revision d - it is a realtek card and you will need to use ndiswrapper, since th elinux driver will not work.

Basically it uses your indowsXP driver 
You will need to use the console

sudo apt-get install ndiswrapper-utils

go to the directory where you have the xp driver

cd /media/cdrom
cd Driver
sudo ndiswrapper -i (filename.inf)
sudo modprobe ndiswrapper
than go the the networking thing again....
add the word
ndiswrapper
to /etc/modules so that the module loads on boot.

---


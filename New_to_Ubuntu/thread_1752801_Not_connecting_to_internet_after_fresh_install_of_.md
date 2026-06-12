---
title: "Not connecting to internet after fresh install of Ubuntu 11.04"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by dkc.com on 2011-05-08
Hi Friends,

Just did a fresh install of Ubuntu 11.04 on my Dell Inspiron 1520.

Broadcom Card/model: BCM4401
PCI.ID: 14e4:170c

Ethernet or Wifi are not working. However when I try to install Broadcom STA Proprietary Driver using Additional Drivers, a message appears that Eth0 disconnected and than it connects to eth0. STA driver won't install because of an error:

Sorry, the installation of this driver failed.

Please have a look at the log file for details.: /var/log/jockey.log

Also tried to install firmware-b43-lpphy-installed using synaptic but it seems that BCM4401 is not supported.

Thanks in advance.

---

### Post by keroman on 2011-05-08
this may help


[http://ubuntuforums.org/showthread.php?p=10720776#post10720776](http://ubuntuforums.org/showthread.php?p=10720776#post10720776)

---

### Post by dkc.com on 2011-05-08
Dear Keroman,

Thanks for a quick reply but it didn't work for me.

Basically, I couldn't activate the STA driver right from beginning so that was out of question. It still isn't activated.

I also installed b43 driver as indicated in that thread and restarted but situation is still the same.

The thing that surprises me the most is the 'eth0' connection. The system won't detect it even if the cable is plugged. When I will try to activate the STA driver from 'Additional Drivers', eth0 will activate itself and also the power button in system tray area will go red to inform me that a restart is required to install an update. This happens every time when it connects to 'eth0'.

Any idea friends?

---

### Post by keroman on 2011-05-08
a bit more reading, this may help, am sure someone here will solve this for you

[http://ubuntuforums.org/showthread.php?t=1741775](http://ubuntuforums.org/showthread.php?t=1741775)

---

### Post by dkc.com on 2011-05-08
Hi Friend,

Did the following, as suggested in the thread but no success:

> sudo gedit /etc/NetworkManager/NetworkManager.conf 
instead of Gedit you can use what ever editor you like

Find a section with the title [ifupdown]
and there should straight under it be a line saying

managed=false

Just change false to true, save, restart and hopefully it should be working


Any idea?

---

### Post by keroman on 2011-05-08
have you looked here
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---


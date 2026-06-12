---
title: "ndiswrapper error"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by talon4g63 on 2007-07-03
hey guys,

i am completely frustrated at trying to get this broad comm 4306 wireless card to work on my hp ze5500.  I have tried a few times to get the card working, and ever tine i can see and connect to the wireless network, but it doesn't load any data from the wireless. i went to reinstall the drivers again and i get this error.  thanks for the help cody

 ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by chicoicho on 2007-07-03
Use automatix 2 and install ndiswrapper driver

---

### Post by kevdog on 2007-07-03
Uninstall ndiswrapper completely, and then reinstall from source.  Follow these instructions:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by talon4g63 on 2007-07-03
i got the card working finally i pluged in the laptop to a cable and then tried another method which someone had written a program to install the drivers.  i am still very new to linux and how its all setup and how the os is organized

---


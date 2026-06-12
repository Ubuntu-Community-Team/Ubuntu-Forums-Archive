---
title: "Wireless card is not recognized (Network unclaimed)"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Capocannoniere on 2010-07-13
Hi Guys, 
I am pretty new using Ubuntu 8.04 and this is my first question in this forum. I have a Lenovo Y 4100 and two weeks ago it was working ok, but now the wireless card is not recognized by the system. I already run this command 
"sudo lshw -C network"

[FONT=Verdana]and I get this output[/FONT]

"*-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0"

[FONT=Verdana]I couldn't find any clear information of what to do next to fix this problem.
I will appreciate any help or thoughts to fix it.

Thanks [/FONT]

---

### Post by anewguy on 2010-07-13
I'm not sure if there is a restricted driver for that adapter or not, but I would try:

- hard-wire a connection from your PC to the access point/router

- open a terminal window

- type:

sudo apt-get update <press enter>

- close the terminal window

- check in System/Administration/Hardware Drivers and see if a driver is listed there for your wireless - if so, enable it

- physically disconnect the hard-wire connection

- check in network manager to be sure "Enable Wireless" is checked

See if your wireless works now - if not, we can work on other solutions.

Dave ;)

---

### Post by Capocannoniere on 2010-07-14
It worked!!!. Thank you very much for your help!.:D

---

### Post by anewguy on 2010-07-15
Glad it worked for you!

Dave ;)

---

### Post by contrafactus on 2011-03-03
I followed these steps and my driver did not come up in the list.  What do I do now?  I have an Atheros AR5009 which Linux recognizes as an AR928x instead.  It was working for several days after I installed madwifi, but I think an update wrecked my wifi.  Please help!  Thanks

---

### Post by gandaran on 2011-03-03
> **contrafactus said:**
> I followed these steps and my driver did not come up in the list.  What do I do now?  I have an Atheros AR5009 which Linux recognizes as an AR928x instead.  It was working for several days after I installed madwifi, but I think an update wrecked my wifi.  Please help!  Thanks
I believe you have to reinstall madwifi every time there is a kernel update.

---


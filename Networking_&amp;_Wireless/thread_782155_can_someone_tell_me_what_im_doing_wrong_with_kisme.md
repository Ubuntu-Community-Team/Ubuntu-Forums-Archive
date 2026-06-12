---
title: "can someone tell me what im doing wrong with kismet?!"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by iwallet on 2008-05-04
im trying to get aircrack to install aircrack.. but i cant get kismet to work?!
this is what i get when i run sudo kismet

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.


my problem is that i dont know how to configure ANY packet source.. 
i know i know.. im disappointing many of you by saying that.. sooorrryy!!! :P 
but please help!

---

### Post by chili555 on 2008-05-04
Please do: ```
less /usr/share/doc/kismet/README.gz
```especially sections 6 and 12. The 'less' command will allow you to scroll back and forth in the README. You can simultaneously open a second terminal and edit */etc/kismet/kismet.conf* with your favorite text editor which I hope is vim. If you are hard core enough for kismet, then you are hard core enough for vim.

Save, close and try again.

---

### Post by Monicker on 2008-05-04
> **chili555 said:**
> Please do: ```
less /usr/share/doc/kismet/README.gz
```especially sections 6 and 12. The 'less' command will allow you to scroll back and forth in the README. You can simultaneously open a second terminal and edit */etc/kismet/kismet.conf* with your favorite text editor which I hope is vim. If you are hard core enough for kismet, then you are hard core enough for vim.

Save, close and try again.


Kismet rocks!   ;)

---

### Post by openflame06 on 2008-06-21
What you are doing wrong is not editing the kismet.conf file and telling it what device to use.

Depending on the drivers it will be different, i have an atheros card and my kismet.conf file has this:

# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi

- If it hasnt been changed i think it says source=addme

---

### Post by rlzyoner on 2008-07-09
Alternatively, you can run a command to add the source and run kismet

kismet -c madwifi_ag,wifi0,madwifi

---


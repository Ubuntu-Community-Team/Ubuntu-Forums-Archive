---
title: "Automatically connect on boot"
date: 2019-05-11
forum: Networking &amp; Wireless
---

### Post by aabuntu on 2019-05-11
I'm not sure why but Ubuntu will not connect to my wired connection on boot.  I installed network manager so I can connect to a VPN.  I included a screenshot of what my network setting is at boot.  I need to enable it every time which doesn't make any sense.  Any help would be appreciated.  Thanks.

[ATTACH=CONFIG]283242[/ATTACH][ATTACH=CONFIG]283241[/ATTACH]

---

### Post by SeijiSensei on 2019-05-11
Look at the properties for the wired connection. Do you have "Connect automatically" enabled?

---

### Post by aabuntu on 2019-05-11
Yes I have connect automatically checked.  I've tried over and over to get it connect on startup.  The only solution I came up with is to use a script with nmcli to connect to my Ethernet interface.  I can't get the script to run on startup though.  I tried using crontab -e to have it run but it never does.  I run the script manually at this point.

---


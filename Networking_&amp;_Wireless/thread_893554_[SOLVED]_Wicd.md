---
title: "[SOLVED] Wicd"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by elkade on 2008-08-18
Am running Hardy Heron on a Compaq Presario F767cl laptop that came with Vista installed.  The wireless card # 4104A-ARBXB63H googled says that it is an AR5006.

Installed madwifi ar5700 drivers

Then I installed wicd ver 1.5.1 after uninstalling network manager

When I attempt to start wicd, I get the following:
Could not connect to wicd's D-Bus interface. Make sure the daemon is started.

In sessions I added wicd, wicd-client 

Also I can not connect to the internet.

What do I do know???

Larry

---

### Post by mikespug on 2008-08-18
I, too, am looking for a solution to the issue however, i've found that downgrading to 1.4.2, which you can install by first uninstalling ver 1.5.1 and then adding deb "http://apt.wicd.net hardy extras" without the quotes to your repos and installing through synaptic package manager, will allow you to at least USE wicd even if it is an older version.  Oddly enough I was able to install ver 1.5.1 with Xubuntu without any issues.

---

### Post by jimv on 2008-08-18
You should probably make sure the daemon is started, like it said.  To do that, open a terminal and type:

sudo /etc/init.d/wicd start

---

### Post by elkade on 2008-08-18
JimV,

Tried your fix, still nothing.  Get the same error message 

Any other ideas

Larry

---

### Post by imdano on 2008-08-18
Can you post the contents of /etc/init.d/wicd here?  I have a feeling you're using the 1.4.2 version with 1.5.1, which won't work.  Also make sure you remove any Sessions entry you have for the tray icon that lived in /opt/wicd/tray.py, since that isn't used in 1.5.x.

---


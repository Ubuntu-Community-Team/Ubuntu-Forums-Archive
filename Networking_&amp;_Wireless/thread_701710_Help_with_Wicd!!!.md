---
title: "Help with Wicd!!!"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by ecoA on 2008-02-19
I tried installing wicd wireless manager on my dell latitude 110L, but 
it doesn't start. I found soem similar problems on the forum, but none 
really helped me, so I decided to make a new post.

This far i have tried reinstalling wicd, and also launching 
/opt/wicd/daemon.py and /opt/wicd/gui.py from console, but this is waht 
i get:

ecoa@rotikas:~$ /opt/wicd/daemon.py
---------------------------
wicd initalizing...
---------------------------
wicd daemon: pid 5535
ecoa@rotikas:~$ configuration file exists, no settings found, adding defaults...
Traceback (most recent call last):
  File "/opt/wicd/daemon.py", line 1236, in <module>
    object = ConnectionWizard(bus_name)
  File "/opt/wicd/daemon.py", line 116, in __init__
    self.ReadConfig()
  File "/opt/wicd/daemon.py", line 1088, in ReadConfig
    configfile = open(self.app_conf,"w")
IOError: [Errno 13] Permission denied: 'data/manager-settings.conf'

ecoa@rotikas:~$ /opt/wicd/gui.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined
ecoa@rotikas:~$

---

### Post by Whiffle on 2008-02-19
daemon.py is meant to be run as root. gui.py depends on daemon.py to be running.
Try

sudo /etc/init.d/wicd start

then start the gui.

---

### Post by ecoA on 2008-02-20
So its still not working. What should i do next?


ecoa@rotikas:~$ sudo /opt/wicd/daemon.py

wicd daemon: pid 7267

ecoa@rotikas:~$ ---------------------------

wicd initalizing...

---------------------------

found wireless interface in configuration... setting wireless interface eth1

found wired interface in configuration... setting wired interface eth0

found wpa driver in configuration... setting wpa driver wext

0

setting use global dns to 0

setting use global dns to boolean False

setting global dns

global dns servers are None None None

wired autoconnection method is 1

wireless configuration file found...

wired configuration file found...

chmoding configuration files 0600...

chowning configuration files root:root...

lo        no wireless extensions.



eth0      no wireless extensions.



autodetected wireless interface... automatically detected wireless interface eth1

eth1

using wireless interface... returning wireless interface to client

eth1

autoconnecting... returning wireless interface to client

eth1

scanning start

 ##### 00:A0:C5:E9:D8:69

 ##### 00:02:6F:3F:3A:93

 ##### 00:13:49:60:C6:E8

 ##### 00:13:49:60:A2:DA

 ##### 00:13:49:60:C6:E3

scanning done

found 5 networks: 00:13:49:60:A2:DA

00:13:49:60:C6:E8

False

False

00:02:6F:3F:3A:93

False

False

00:13:49:60:C6:E3

False

False

00:A0:C5:E9:D8:69

False

False



no wired connection present, wired autoconnect failed

attempting to autoconnect to wireless network

returning wireless interface to client

rheWireless has profile

unable to autoconnect, you'll have to manually connect

None

---

### Post by imdano on 2008-02-20
Looks like the daemon is working.  What happens when you run /opt/wicd/tray.py or /opt/wicd/gui.py?

---

### Post by ecoA on 2008-02-23
Still nothing :S

ecoa@rotikas:~$ /opt/wicd/gui.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined
ecoa@rotikas:~$ /opt/wicd/tray.py
attempting to connect daemon...
daemon not running...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.

---


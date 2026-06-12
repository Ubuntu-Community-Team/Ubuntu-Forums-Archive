---
title: "wicd trippin'."
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by arnicainthemembrane on 2008-04-07
So I've been using wicd for a few months with no issues, then today it started trippin. Trippin as in not turning on. (Excuse my lack of technical terminology here...) I tried to access it via terminal and here's what I got:

arnica@arnica-laptop:~$ /opt/wicd/gui.py
attempting to connect daemon...
success
starting gui.py...
refreshing...
using global dns: 0
disabling ip
disabling dns
dns checkbox toggled False
global dns checkbox toggled False
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 1319, in <module>
    app = appGui()
  File "/opt/wicd/gui.py", line 910, in __init__
    self.refresh_networks(fresh=False)
  File "/opt/wicd/gui.py", line 1190, in refresh_networks
    wiredNetwork = PrettyWiredNetworkEntry()
  File "/opt/wicd/gui.py", line 306, in __init__
    PrettyNetworkEntry.__init__(self,WiredNetworkEntry())
  File "/opt/wicd/gui.py", line 540, in __init__
    self.profileList = config.GetWiredProfileList()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 135, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 603, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.ConfigParser.ParsingError: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 655, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/opt/wicd/daemon.py", line 904, in GetWiredProfileList
    config.read(self.wired_conf)
  File "ConfigParser.py", line 267, in read
    self._read(fp, filename)
  File "ConfigParser.py", line 490, in _read
    raise e
ParsingError: File contains parsing errors: data/wired-settings.conf
[B]        [line 17]: '[]\n'

... what the hell is all that about?????[/B]

---

### Post by MrFSL on 2008-04-07
it might have something to do with the last line:
> ParsingError: File contains parsing errors: data/wired-settings.conf

You should be able to delete this file without harm:
```
# stop wicd
sudo /etc/init.d/wicd stop
# Remove File
sudo rm /opt/wicd/data/wired-settings.conf
# Start WICD
sudo /etc/init.d/wicd start
```

---

### Post by arnicainthemembrane on 2008-04-08
no, nothing, really. Doesn't that just govern the oethnet connection? I'm having issues with it even starting up at all. So I tried to reinstall it, and got the following:

arnica@arnica-laptop:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wicd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up vmware-server (1.0.4-1gutsy2) ...
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth1, eth2, 
eth1:avah. Which one do you want to bridge to vmnet0? [eth0] 

The ethernet device "eth0" was not detected on your system.  Available ethernet
devices detected on your system include eth1, eth2, eth1:avah.  Are you sure 
you want to use this device? (yes/no) [no] 

Invalid default answer!
Execution aborted.

dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

**how do i deal with that?**

---

### Post by imdano on 2008-04-08
MrFSL is right, deleting the wired-settings.conf file will fix the crash problem.

---

### Post by arnicainthemembrane on 2008-04-14
seems to work, thanks for the advice

---


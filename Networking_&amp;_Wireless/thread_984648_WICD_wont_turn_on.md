---
title: "WICD wont turn on"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by riminicat on 2008-11-16
Hey I have wicd as my network manager and for some reason it wont start, I've tried starting it from the terminal and the menu.  I had it set up to turn on at start up but for some reason it stopped working.  Can anyone help, I need to get back out of my microsoft partition because I hate it!  I keep it around for things like this though.

---

### Post by pytheas22 on 2008-11-16
What output do you get when you try to start it in the terminal?  Also, I think that this is the command you should be using to start it from the terminal--just typing 'wicd' probably won't work:
```

python /opt/wicd/tray.py
```

Does that work?  If not, what is the total output that you get?

---

### Post by imdano on 2008-11-16
If you're using a version more recent than 1.4.2, running /opt/wicd/tray.py won't work; wicd doesn't live there anymore.  You start it by running ```
wicd-client
```If that doesn't work, please post the error message you get, and the contents of /var/log/wicd/wicd.log.

---

### Post by riminicat on 2008-11-17
Thanks guys I'll test and post what I get when I get out of work.

---

### Post by riminicat on 2008-11-18
Here is the error message I get.  I can't open the log file.  I tried opening it in the terminal as Su but it wouldn't let me.  I also tried opening it manually but I get a permission denied warning.  How do I give myself permission to open the file?





```

Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 2006, in <module>
    setup_dbus()
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 174, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files
```

---

### Post by pytheas22 on 2008-11-18
Somebody in [this thread]("http://forum.ubuntu-fr.org/viewtopic.php?pid=2096363") (French) reports having what looks like an identical issue (at least based on the command-line output) and that it was solved by running the following commands:
```

sudo rm /var/lib/dpkg/info/wicd*
sudo apt-get remove --purge wicd
sudo apt-get install wicd
```

Note that you'll need to be online in order for those commands to work.  If you don't know how to connect to your wireless network without using wicd, please post the output of:
```

sudo iwlist scan
```

and tell us the name of your network, and we can get you connected manually.  Or just use ethernet if available.

If this doesn't work there are some other things to try, but based on my quick googling, I think that the stuff from the French thread looks most promising.

---

### Post by riminicat on 2008-11-18
I'll try the codes and report back to you.  I do have an installer for WICD so I could probably just purge and reinstall, but I didn't think of that when I was trying to feed my internet addiction!

---

### Post by imdano on 2008-11-18
Before you do that, try running ```
sudo wicd -foe
```from a console and check for error messages.  This way you won't need to check the log file (you should be able to open that with sudo, I'm not sure what's going on there).  If you haven't recently upgraded wicd its unlikely that you have to reinstall.

The error message you got when trying to run wicd-client indicates that the daemon isn't started.  This probably means its crashing when it tries to start.  Running wicd -foe will start the daemon in the foreground, so you can capture the backtrace that gets left behind when it crashes.

---

### Post by riminicat on 2008-11-20
Here's the message that comes up when I try running Sudo wicd -foe

```
wicd initializing...
---------------------------
Automatically detected wireless interface wlan0
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-daemon.py", line 1647, in <module>
    main(sys.argv)
  File "/usr/lib/wicd/wicd-daemon.py", line 1618, in main
    obj = ConnectionWizard(d_bus_name, auto_connect=auto_connect)
  File "/usr/lib/wicd/wicd-daemon.py", line 159, in __init__
    self.ReadConfig()
  File "/usr/lib/wicd/wicd-daemon.py", line 1374, in ReadConfig
    default=iface))
  File "/usr/lib/wicd/wicd-daemon.py", line 1345, in get_option
    config.read(self.app_conf)
  File "/usr/lib/python2.5/ConfigParser.py", line 267, in read
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 462, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /etc/wicd/manager-settings.conf, line: 1
'0.000000 1226832765 0.000000\n'


```

---

### Post by imdano on 2008-11-20
Yikes, your manager-settings.conf file got corrupted somehow.  Delete /etc/wicd/manager-settings.conf, restart the daemon (using "sudo /etc/init.d/wicd start") and you should be all set.

---

### Post by riminicat on 2008-11-20
Alright thanks.  I got an error message once when I started Ubuntu, something about things being messed up and fixing them.  I just clicked yes, mayba thats what did it.

---


---
title: "Cannot get NM to run"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by Fodo on 2007-02-28
My goal is to connect to a WPA secured network. I am running Ubuntu 6.10 on an IBM Thinkpad T40p. Built-in wireless is disabled in BIOS, I use a D-Link DWL-G650M PCMCIA card instead. The card works fine using the XP drivers under Linuxant. I have no problems connecting to an open network after manually configuring the ESSID and IP info. To get WPA support, I installed NM by : "sudo apt-get install network-manager-gnome". The command completed successfully. Then I edited the "interfaces" commenting out everything except the "Io" statements. However, even after several reboots, still no sign of NM. 

Synaptic tells me that network-manager and network-manager-gnome are installed, v 0.6.3.2ubuntu6. The nm-applet is listed in the Start-up Programs list. 

When "killall NetworkManager && NetworkManager --no-daemon" (as suggested in another thread)

root_at_Frodo:/home/rer# killall NetworkManager && NetworkManager --no-daemon
NetworkManager: <information>  starting...
NetworkManager: <Warning>        nm_dbus_init (): nm_dbus_init (): could not acquire hte NetworkManager service as it is already taken (ret-3). Is the daemon already running?
NetworkManager: <ERROR>   [1172619287.397157] main  ():    nm_dbus_init ()  failed, exiting. Either dbus is not running, or NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:                        NetworkManager(main+0x47f)  [0x80681af]
NetworkManager:                        /lib/tls/1686/cmov/libc.so.6(__libc_start_main+0xdc)  [0xb7c2f8cc]:
NetworkManager: <debug info>     [117261947.586695] nm_print_open_socks  (): Open Socket List Done.
NetworkManager:                        NetworkManager  [0x80530a1]
Trace/breakpoint trap  (core dumped)


Any idea what could prevent NM from running, what am I missing?

Thx

---

### Post by nachotronics on 2007-03-02
Hi, i also had trouble to get it working, i solved the problem following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**.

My startup program entry is:

nm-applet --sm-disable

Hope this helps.

---

### Post by oranguman on 2007-03-02
seems from the output that it is already running. since it's an applet, your system may be lumping it in with the 'notification area' applets. 

there's an easy way to find out if this little mixup is the problem; just go to your menubar, right click, and "add".. then drag the "notification area" icon onto the menubar. NM's networking icon may appear in this area.

---


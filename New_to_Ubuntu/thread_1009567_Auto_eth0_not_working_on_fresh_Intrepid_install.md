---
title: "Auto eth0 not working on fresh Intrepid install"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2008-12-12
Just installed Ibex on a Compaq Presario V2000 series; installation went smoothly.  Auto eth0 doesn't work.  And I know the following:
[list=1][*]the cable works.
[*]the router accepts DHCP. 
[*]the router has internet connectivity.
[*]no settings in the new installation have been modified.[/list] 
When trying to acquire a network address, it searches for a long time and then gives up, saying I was disconnected.  Any help?  Please and thank you.

If it's of any importance, there is a wireless chip whose drive I'm trying to install, and it's a pesky Broadcom.

---

### Post by Michael.Godawski on 2008-12-13
hi InfectedWithDrew, 
some input please. Open the terminal, run these commands and post the output here, thx.

```
sudo lshw -C network
iwconfig
ifconfig
sudo iwlist scan
cat /etc/network/interfaces
```

---

### Post by InfectedWithDrew on 2008-12-14
Solved.  Installed Hardy instead, and roaming ethernet worked.  Then did sudo apt-get update and installed 200 updates and b43-fwcutter worked.

File this under bad ethernet card support in Intrepid.

---


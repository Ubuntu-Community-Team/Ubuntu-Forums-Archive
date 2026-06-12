---
title: "Ndiswrapper problem - using 100% cpu"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by sparkov on 2007-07-24
I've been trying for the past few days to get a Belkin F5D7000 working with a clean install of Feisty.  I have no trouble installing ndiswrapper and the realtek driver (net8185) or assigning the driver to the device.

The command:
```
ndiswrapper -l
``` reports that the driver is installed and that the device is present.

However, when I issue the command

```
sudo modprobe ndiswrapper
```

the whole system becomes extremely unresponsive.  Mouse cursor position on the screen is only updated every 5 seconds or so, as are commands typed into the terminal.

iwconfig shows wlan0 working fine, however running "top" shows that a process called wrapndis is using 100% of my CPU which explains why my system is so slow.  I am unable to kill this process and only a hard reset seems to return my system to normal (without working wireless).

Can anyone help?

---


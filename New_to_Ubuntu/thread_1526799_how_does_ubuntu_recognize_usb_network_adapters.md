---
title: "how does ubuntu recognize usb network adapters"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by hdtvman on 2010-07-08
I have a new install of Ubuntu 10.04 on a desktop machine with a Linksys WUSB300N attached.  This is a wireless-N adapter based on a Marvel chipset (according to Windows 7).  I have downloaded all the Windows drivers from Linksys but there were not any Linux drivers.

Questions: (1) How do I get Ubuntu to 'recognize' the card is plugged in?

(2) If there is no Linux driver available, can I setup Ubuntu to use the Windows drivers?

As always, Thank You, hdtvman

---

### Post by nothingspecial on 2010-07-08
The first thing to do is type

```
lsusb
```

To see if it is recognised

---

### Post by cariboo on 2010-07-08
lsusb will recognize the device, but it won't tell you if the correct drivers are loaded. Open an Applications->Accessories->Terminal and type:

```
dmesg | tail -n10
```

just after you have plugged your device in. This command will show if your device is recognized, and hopefully the correct driver is loaded.

---

### Post by hdtvman on 2010-07-08
here is the result of those commands:

jp@amd-u:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 13b1:0029 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jp@amd-u:~$ dmesg tail -n10
klogctl: Operation not permitted
jp@amd-u:~$ dmesg | tail -n10
[   14.654444] type=1505 audit(1278611540.160:7):  operation="profile_replace" pid=924 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.654543] type=1505 audit(1278611540.160:8):  operation="profile_replace" pid=924 name="/usr/lib/connman/scripts/dhclient-script"
[   14.760087] type=1505 audit(1278611540.266:9):  operation="profile_load" pid=925 name="/usr/bin/evince"
[   14.762255] type=1505 audit(1278611540.266:10):  operation="profile_load" pid=925 name="/usr/bin/evince-previewer"
[   14.763636] type=1505 audit(1278611540.266:11):  operation="profile_load" pid=925 name="/usr/bin/evince-thumbnailer"
[   15.318210]   alloc irq_desc for 29 on node 0
[   15.318214]   alloc kstat_irqs on node 0
[   15.318220] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
[   17.043595] ppdev: user-space parallel port driver
[   26.020298] eth0: no IPv6 routers present
jp@amd-u:~$ 

Now what do I do?  There doesn't appear to be any wireless devices in the network manager.

---

### Post by nothingspecial on 2010-07-08
According to google you are going to have to use the windows drivers. You have the windows drivers already so it should be easy. Click the link I post under this and read it carefully

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---


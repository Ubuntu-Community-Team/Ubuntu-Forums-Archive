---
title: "WG111v1 Feisty:  Worked first time, after reboot no longer works . . . help"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by blastoff on 2007-08-11
Feisty with a netgear wg111 version 1.

Installed Ndiswrapper -common 1.38, ndiswrapper -utils 1.38 and ndisgtk 0.6.

Installed driver with ndisgtk graphical interface and I had a connection, internet working, everything was good . . .

Restarted and it no longer works.  Tried deleting drivers, uninstalling/reinstalling ndiswrapper and ndisgtk to no avail.

I don't think it sees the device anymore as there is no longer an option under the "wireless connection" utility (ndisgtk).

Any help is appreciated. Thanks

---

### Post by bmartin on 2007-08-11
I'm not familiar with the ndiswrapper graphical installer. Try adding the kernel module by typing the following into a terminal (after you've configured everything):
```
sudo modprobe ndiswrapper
```

You can have the kernel module load every time by using the following command:
```
echo ndiswrapper | sudo tee -a /etc/modules
```
That command is equivalent to editing your /etc/modules file by hand and adding in a line that simply has the **ndiswrapper** kernel module's name.

---

### Post by blastoff on 2007-08-11
I'm not certain this is my problem since I don't think that it even sees my device anymore . . . but maybe it is . . . comments/suggestions?

---

### Post by cmp1988 on 2007-08-11
Well, this is what works in Dapper to get that specific card working.  I would know that it works because I got one to work on another computer with dapper.  Might work in Feisty as well.

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28wg111%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28wg111%29)

You can basically go to the Blacklisting part in Dapper, and just do that, and configure network the normal way you do.

---

### Post by kevdog on 2007-08-12
Something tells me you have an old version of ndiswrapper.  Can you post the following:

lspci -nn
lshw -C network
modinfo ndiswrapper

---


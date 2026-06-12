---
title: "network printing, samba, and unsupported printers."
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-08-11
okay ... i have a small business network on which unbuntu is functioning as a file/samba server.  i'm working on migrating everything over from an aging win2000 server which hosts the networked printers.

these printers do not have drivers in linux.  really they do not.  i've been working on this for the better part of 8 months.

in any case the printers in question are usb printers.  when i plug one in i see this in dmesg:
```
[208271.813461] usb 1-2: new full speed USB device using uhci_hcd and address 5
[208271.960917] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1081
[208404.574972] usb 1-2: USB disconnect, address 5
```
my samba looks like this:
```
[global]
    ; General server settings
    netbios name = IPC10512
    server string =
    workgroup = i&f
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    load printers = yes
    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[E]
    path = /home/shared/common2
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = admin
    force group = admin

[&#26087;&#65403;&#65392;&#65418;&#65438;&#20849;&#26377;]
    path = /home/shared/&#26087;&#65403;&#65392;&#65418;&#65438;&#20849;&#26377;
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = admin
    force group = admin

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = yes
```
when i plug the printer in, i cannot see it on the network even after restarting samba.

is it even possible to host a printer via linux if there is no driver for the printer in linux?  if it is possible, how would one go about it?

---

### Post by dmizer on 2006-08-12
well, i can see a printer now.  i've made the following changes to my samba conf:
replaced
```
[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = yes
```
with this
```
[printer1]
    printable = yes
    print command = /usr/bin/lpr -P%p -r %s
    printer = canonbj
    printing = CUPS
    path = /var/tmp
    guest ok = yes
```
so now a printer is shown on the server, but i cannot print to it.

i realize that the above configuration will show a printer even if no printer exists on the computer no?  so, how do i get samba to see the printer on the usb or lpt port?

---

### Post by dmizer on 2006-08-13
um ... please?

---


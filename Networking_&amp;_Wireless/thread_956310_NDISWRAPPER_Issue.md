---
title: "NDISWRAPPER Issue"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by myattb on 2008-10-23
I am trying to get my NetGear WG511v2 card to work with 8.04.
I have installed ndiswrapper but hove come across an issue and I don't know how to resolve?

ben@Inspiron8200:~/Drivers/Wireless/Netgear/INF$ sudo ndiswrapper -i WG511v2.INF
installing wg511v2 ...
couldn't find "WG511v2XP.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "WG511v2XP.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete

ben@Inspiron8200:~/Drivers/Wireless/Netgear/INF$ sudo ndiswrapper -i WG511v2.INF
driver wg511v2 is already installed

ben@Inspiron8200:~/Drivers/Wireless/Netgear/INF$ ndiswrapper -l
wg511v2 : invalid driver!

How do I remove the current install and try again?
I know there is a -r option but I can't be sure I can identify what to remove?

ben@Inspiron8200:~/Drivers/Wireless/Netgear/INF$ lspci -n
00:00.0 0600: 8086:1a30 (rev 04)
00:01.0 0604: 8086:1a31 (rev 04)
00:1d.0 0c03: 8086:2482 (rev 02)
00:1d.2 0c03: 8086:2487 (rev 02)
00:1e.0 0604: 8086:2448 (rev 42)
00:1f.0 0601: 8086:248c (rev 02)
00:1f.1 0101: 8086:248a (rev 02)
00:1f.5 0401: 8086:2485 (rev 02)
00:1f.6 0703: 8086:2486 (rev 02)
01:00.0 0300: 1002:4c66 (rev 01)
02:00.0 0200: 10b7:9200 (rev 78)
02:01.0 0607: 104c:ac42
02:01.1 0607: 104c:ac42
02:01.2 0c00: 104c:8027
03:00.0 0200: 11ab:1faa (rev 03)


Many thanks,

Ben.

---

### Post by kilroy423 on 2008-10-23
-e <driver>
    removes an installed Windows XP driver named <driver>. 

try

```
sudo ndiswrapper -e WG511v2.INF
```

---

### Post by myattb on 2008-10-23
Tried as suggested

ben@Inspiron8200:~/Drivers/Wireless/Netgear/INF$ sudo ndiswrapper -e WG511v2.INF
[sudo] password for ben: 
couldn't delete /etc/ndiswrapper/WG511v2.INF: No such file or directory

---

### Post by kilroy423 on 2008-10-23
my bad, I believe that it's 

```
sudo ndiswrapper -e WG511v2
```

---

### Post by myattb on 2008-10-23
sorry, same outcome?

ben@Inspiron8200:~/Drivers/Wireless/Netgear/INF$ sudo ndiswrapper -e WG511v2
[sudo] password for ben: 
couldn't delete /etc/ndiswrapper/WG511v2: No such file or directory

---

### Post by myattb on 2008-10-23
Fixed using Ndisgtk.

---

### Post by Ayuthia on 2008-10-23
For future reference if you don't use ndisgtk, the problem was that you used upper case letters.  It should have been:
```
sudo ndiswrapper -e wg511v2
```
Generally, when you load the driver it has the .inf extension, but when it is removed it does not.  If you are not for sure if it is upper case or lower case, you can always look at /etc/ndiswrapper.  That is where the folders are stored.  You should be able to see them through Nautilus or if you want to use the Terminal:
```
ls /etc/ndiswrapper
```

---


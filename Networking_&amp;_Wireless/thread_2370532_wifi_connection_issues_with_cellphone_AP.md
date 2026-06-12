---
title: "wifi connection issues with cellphone AP"
date: 2017-09-04
forum: Networking &amp; Wireless
---

### Post by wojciechtomasz on 2017-09-04
hello,

since quite long time I have problems while connecting to wifi network made by blackberry classic phone.
network is listed in tray icon, system tries to connect, but after a while 'provide password' window appear.

workaround is to use:
```
sudo service network-manager restart
```
but sometimes I need to execute this command about 10 or 15 times and quite often it kills nm-applet (so it need to be relaunched from another terminal window).

I want to find a solution for connecting wireless network every time and with first try :)

some details:
**system:** ubuntu 16.04 LTS 64bit
**network card**: ```
wojciech@ideapad:~$ lspci | grep -i eth
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
wojciech@ideapad:~$ cat /var/log/dmesg | grep -i eth
wojciech@ideapad:~$ 
```
**network settings**:
mode: client
security: wpa & wpa2 personal
IPv4: dhcp
IPv6: automatic

would be great if you could help with some ideas why it happens/ how to fix it/ where to search for solution.

thanks!

---

### Post by jeremy31 on 2017-09-04
Please see the wireless script link in my signature and post results

---

### Post by wojciechtomasz on 2017-09-04
Thank you for your reply. Output below.

```


wojciech@ideapad:~$ sudo apt update
[sudo] password for wojciech: 
Fetched 5455 kB in 2s (1913 kB/s)                                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
wojciech@ideapad:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-packagekitglib-1.0 liblouis-data liblouis9 libpackagekit-glib2-16
  python3-louis snapd
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 12,0 MB of archives.
After this operation, 4464 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
wojciech@ideapad:~$ sudo apt install pastebinit
wojciech@ideapad:~$ ./diagnose.sh 

Results saved in "/home/wojciech/wireless-info.txt".

Results also archived in "/home/wojciech/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

http://paste.ubuntu.com/25467231/

wojciech@ideapad:~$ 

```

[http://paste.ubuntu.com/25467231/](http://paste.ubuntu.com/25467231/)

---

### Post by jeremy31 on 2017-09-05
Disable IPv6 in Network Manager and can you remove the space in Blackberry hotspot.  The system is complaining about invalid WMM settings on the hotspot but I don't think we can fix that

---

### Post by wojciechtomasz on 2017-09-05
thanks,  I'll try that:
a/ IPv6: method -> ignore
b/ remove white and special characters from AP SSID

invalid WMM settings might be connected with phone usb connection (perhaps) - BB was connected to USB port in time requesting diagnose script.

anyway, Ill change those, and come back with results (i hope that will be [solved] tag :) ), and, of course, check things connected with WMM (by now im not sure if its by default connected with AP, or result of some_mode_of_usb_connection).

can you please tell me how to check if errors/issues are connected with WMM?

---


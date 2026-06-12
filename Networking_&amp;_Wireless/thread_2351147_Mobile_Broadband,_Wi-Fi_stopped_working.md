---
title: "Mobile Broadband, Wi-Fi stopped working"
date: 2017-01-31
forum: Networking &amp; Wireless
---

### Post by EthioJOB on 2017-01-31
[COLOR=#111111][FONT=Ubuntu]I installed Ubuntu 16.04 on a new Acer VN7-792G and everything was working normally until about a week ago when the Mobile Broadband dongle and WiFi stopped working. When inserting the dongle, a prompt to run Huawei shows up, but it doesn't do anything. At first rebooting while the dongle is inserted seemed to solve the problem but later on it stopped working completely. After this trying to connect to Wifi became problematic as it crashes Network Manager and I will have to reboot just to get it working again (just the applet, connecting to Wifi is not possible at this moment). I'll try to list all the things I tried so far.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Typing lsusb in terminal shows the dongle:[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]Bus 001 Device 006: ID 12d1:1f01 Huawei Technologies Co., Ltd. E353/E3131 (Mass storage mode)[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]
I tried [/FONT][/COLOR]"[COLOR=#111111][FONT=Ubuntu][FONT=courier new]sudo service NetworkManager stop[/FONT]" then "[FONT=courier new]sudo service NetworkManager start[/FONT][/FONT][/COLOR]"
[COLOR=#111111][FONT=Ubuntu]
Doesn't work.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I typed this and edited to add E3272, and changed it again to E353/E3131:[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]
Didn't work. I typed [/FONT][/COLOR]"[FONT=courier new][COLOR=#111111]sudo systemctl restart modemmanager[/COLOR][/FONT]"[COLOR=#111111][FONT=Ubuntu] and "[FONT=courier new]sudo service modemmanager restart[/FONT]", and for both I got this:[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]Failed to restart modemmanager.service: Unit modemmanager.service not found.[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]
I tried "[FONT=courier new]sudo restart modemmanager[/FONT]", then I got this:[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Ubuntu]
Then I typed this "service modemmanager status", for which I got the following:[/FONT][/COLOR]
```
&#9679; modemmanager.service   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
```
[COLOR=#111111][FONT=Ubuntu]
After a little online research I suspect this occurred after an update, and caused some sort of clash between upstart and systemd process, but I'm not sure. I'm at the end of my rope and I would really appreciate some help.[/FONT][/COLOR]

---

### Post by gdesilva on 2017-02-01
The output of lsusb shows that the dongle is in 'mass storage mode' which means it is being treated an ordinary storage device. I have never used broadband dongles so I may be barking up the wrong tree here but it may be worth checking whether the mode setting is correct here.

---

### Post by EthioJOB on 2017-02-01
> [COLOR=#000000]The output of lsusb shows that the dongle is in 'mass storage mode' which means it is being treated an ordinary storage device. I have never used broadband dongles so I may be barking up the wrong tree here but it may be worth checking whether the mode setting is correct here.[/COLOR]
Probably. The problem is it used to work. I don't know why it's acting up now, though I suspect an update has something to do with it.

---


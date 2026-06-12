---
title: "Windows 11 can't connect to Ubuntu samba shares?"
date: 2023-09-04
forum: Networking &amp; Wireless
---

### Post by kenne76 on 2023-09-04
[COLOR=#232629][FONT=-apple-system][FONT=var(--theme-post-body-font-family)][FONT=inherit]I have problem to connect from Windows 11 to my sambashares on Ubuntu 22.04.3 LTSbut to my sambashare on Linux raspberrypi 6.1.21-v8+ the connection works.
[/FONT]
[FONT=inherit]When I tested with Windows 10 I was able to connect both Ubuntu's and RaspberryPi's samba shares without problems. 
Raspberry Pi has Samba version 4.13.13-Debian installed and Ubuntu has Samba version 4.18.6 installed.
[/FONT]
[FONT=inherit]Can someone help me with this issue?[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Morbius1 on 2023-09-04
Way more information is required to answer that question but first .....

Find the ip address of your Ubuntu machine:
```
hostname -I
```
Then in Win11 open explorer and enter:
```
\\the-ip-address-you-got-from-above\share-name
```
What error message do you get?

The information required to make more than a guess would be the output of these commands in Ubuntu:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by kenne76 on 2023-09-05
With ip adress or hostname.local (eg. ServerPC.local) it works, so this solution is enough for me.

---

### Post by colin020 on 2023-09-16
I have the same problem.

All other PC's on our network connect without error but, the single Win 11 PC just chokes on it with errorcode 0x80004005

---

### Post by Morbius1 on 2023-09-16
0x80004005 is Microsoft's "We have no idea what the hell the problem is" error message.

To rule out a host name resolution problem:

[1] Make sure avahi is installed on Ubuntu so you can do what kenne76 did:
```
sudo apt install avahi-daemon
```
[2] And for Win10/11 to be able to "discover" your Ubuntu server under Network in explorer install WS-Discovery in Ubuntu:
```
sudo apt install wsdd
```

If that does nothing for you your issue is unrelated to the original question and you might want to start your own topic.

---


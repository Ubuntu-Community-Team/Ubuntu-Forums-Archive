---
title: "problem that cannot connect to WIFI"
date: 2018-11-11
forum: Networking &amp; Wireless
---

### Post by jackhu0119 on 2018-11-11
Hi all, this is my first post here, I just install the ubuntu for the first day, before I use windows. thanks for the amazing knowledge information here!

I'm having an issue with my wireless connection, I can connect to the hot-spot wifi but I cannot connect to the WIFI named   ''ZenEtudes" . It is a web-login wifi, it need to login in a pop out webpage. I can login in before when I use the window 7 and with my mobile.

when i try to connect via the . ''ZenEtudes" , the infomation say " Connection failed".

There is another WIFI named "FreeWifi". The chrome can navigate to the login page. I donnot know why I cannot connected to the WIFI named   ''ZenEtudes" .

Pastebin of the wireless script: [http://paste.ubuntu.com/p/pgXC5FwV9p/](http://paste.ubuntu.com/p/pgXC5FwV9p/)

Thanks for your help ! Really really thanks everyone!

---

### Post by praseodym on 2018-11-11
Check the output of
```

sudo iwlist scan
```
There are several networks named ZenEtudes which are unsecured. Chose the "unencrypted" option in the network manager and add the MAC address of THAT TO CONNECT network with

 * the strongest connection and add

 * that MAC address into the field "BSSID"

reconnect

---

### Post by jackhu0119 on 2018-11-11
Thanks for your help. this is the output after the command [COLOR=#000000][FONT=&quot]sudo iwlist scan.   [/FONT][/COLOR]https://pastebin.com/ThYuPBMN
In the network manger I didnot find the [COLOR=#000000]"unencrypted" option,can you tell me where is it?[/COLOR]

---

### Post by jackhu0119 on 2018-11-11
also i didnot understand what you mean:
[COLOR=#000000]Chose the "unencrypted" option in the network manager and add the MAC address of THAT TO CONNECT network with[/COLOR]

[COLOR=#000000]* the strongest connection and add[/COLOR]

[COLOR=#000000]* that MAC address into the field "BSSID"

this sentence
[/COLOR]

---


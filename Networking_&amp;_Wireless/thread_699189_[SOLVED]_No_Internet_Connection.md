---
title: "[SOLVED] No Internet Connection"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Rangi01 on 2008-02-17
I have just installed Ubuntu and am very new to Linux (originally installed Kubuntu, had the same issues described here so thought I'd try Ubuntu) and cannot get an Internet connection.  The weird thing is it seems to recognise my ethernet card however the ip address comes back as 192.168.1.3, when I check my ip address through my windows connection it is 222.154 97.165!?!  Now comes the really strange part, every now and then if I set the static ip address, subnet mask etc in the connection settings but leave it on roaming I can connect but not every time , in fact only about 10% of the time.
I reallylike the idea of Ubuntu and this is the first stage to setting our server up with it as well but am really having second thoughts as it seems rather buggy (sorry if I'm being harsh but after reading a few other posts others seem to be having similar issues but seems to be no resolution)
Please help if you can.
Thanks Shane.

---

### Post by jan quark on 2008-02-17
some input first

run these commands in terminal and post the output 
thank you


use the code brackets to make the output more readable

```
iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```

```
sudo lshw -C network
```

```
lspci
```

```
cat /etc/network/interfaces
```

---

### Post by Rangi01 on 2008-02-20
Thanks Jan for that quick reply, sorry that I haven't replied sooner.
Just an update I took the computer into work and it connects there fine so I'm guessing it has something to do with the interface between my home modem and Ubuntu.
Once I can get it home I'll get those numbers.
Thanks again
Shane

---

### Post by Rangi01 on 2008-02-28
Thanks for your help.  Managed to solve this using other posts.  As stated earlier it turned out to be my modem causing the issue (D-Link DSL 504T).  I had internet connection all along it was just that Firefox couldn't work with the old D-Link programme.
To solve it open Firefox type in about:config in Firefox's address field.
Type in ipv6 in the new Filter: field.
right click on the line left in the display window to toogle it's boolean value to true.
Close & restart Firefox.

Mint :) :KS :)

---


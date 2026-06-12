---
title: "connection established but not browsing"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by rakel on 2009-09-09
Hi!!  I´m completely new to Linux and ubuntu, and I´m not a computer sciences expert either, so I hope you´re patient with me :KS

I established a wired internet connection.  My internet provider says it´s transmitting but I cannot browsed.... I keep getting the Server not found message.  Any idea what it can be or what can I do? 

Even thought I have a DSL connection, my internet provider guided me through the steps for the wired connection.  Does it have anything to do with it?

Thanks so much for all your help!!

Rakel

---

### Post by KIAaze on 2009-09-13
First of all, since you are completely new to GNU/Linux, read this:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Check the stickies of this forum section too:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

This should make it easier for us to help you.

==============

Now, here are some networking troubleshooting guides:
[https://help.ubuntu.com/9.04/internet/C/troubleshooting-lan.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-lan.html)
[http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html](http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html)
[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

If you have any problems following them, just ask again here.

==============

My own quick troubleshooting tips:

First things to check:
1) Can you ping the router?
The router is the thing where you plug in your cable.
The IP address of the router should be written on the router itself or in its manual.
Your ISP should also be able to give it to you.
Usually, it's something like 192.168.1.1 or 192.168.2.1 .
To test the connection, open a terminal and enter
```
ping xxx.xxx.xxx.xxx
``` where xxx.xxx.xxx.xxx is the router's IP address.

2) Can you ping a website/server by IP?
Try one of google's IPs for example:
```
ping 74.125.67.100
```
You can look up IP addresses here: [http://www.ip-adress.com/whois/sef.net.ru](http://www.ip-adress.com/whois/sef.net.ru)

3) Can you ping a website by its URL?
Try:
```
ping ubuntu.com
```

==============

Also, to help us help you, please post the output of the following commands here:
```
ifconfig
lspci -vvnn

```
You can put the output of the commands directly into text files (ifconfig.log and lspci.log in this case) the following way:
```
ifconfig > ifconfig.log
lspci -vvnn > lspci.log

```

Also post the contents of the file /etc/network/interfaces.
This requires root permissions, so you should run nautilus like this:
```
gksudo nautilus
```

---

### Post by mapes12 on 2009-09-13
Hi and welcome to the forum.

If you right click the Network Manager icon in the right hand side of your grey panel bar (it should look like 2 computer monitors) then click on "Connection Information" a window will open up. Next go Applications>Accessories>Take Screenshot will put a screen shot image on your desktop. Move it to the machine that you are accessing this forum from. You can then post back and attached the screenshot to your post. It's the option in "Additional Options" called "Attach Files". 

It sounds like you're not getting an IP address from your router.

---


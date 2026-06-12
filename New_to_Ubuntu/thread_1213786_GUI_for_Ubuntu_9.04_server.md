---
title: "GUI for Ubuntu 9.04 server"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by gtaplah on 2009-07-15
Hello Everyone,

I am new and trying out Ubuntu Server edition. Initially in installed 8.04 server and got IBM Domino 8.5 installed, things worked out well with both servers. I got some start up scripts to enable domino start up as a service in Ubuntu 8.04 and to install Lotus client for remote administration, but i had difficulties moving around. I had to uninstall 8.04 and install 9.04 (hoping to upgrade the current code (8.04)), no such option! Now I have 9.04 at fresh and I am still stucked with the console. I move around much quickly in GUI. i have applied chvt 7 and other combinations but the b/w screen (console) is still with me. can anyone assist me to switch between GUI and console. I actually want to install some GUI app, like the domino client (lotus notes 8.x all client). i promise after going through the ubuntupocketguide, i will learn much more about the console with available resources.

Thanks for your patience,

George

---

### Post by wojox on 2009-07-15
There is no gui on the server. You have to install it. If you want bare bones:

```
sudo apt-get install x-window-system-core gnome-core
```

If you want the full package:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Tibuda on 2009-07-15
You can install the Gnome desktop or KDE in a server using apt-get.

---

### Post by AbtZ on 2009-07-15
Hello George,

How are you administrating your server? Remotely through SSH or do you have a screen connected directly to it?

In any case, if you want a GUI the easiest way is to do
```
sudo apt-get update; sudo apt-get install ubuntu-desktop
```
in the terminal.

This will install the regular Ubuntu Gnome desktop environment on your computer.

Afterwards, if you want to be able to access the server GUI remotely, you could go set VNC up through System->Preferences->Remote Desktop.

Hope it helped. :)

---

### Post by gtaplah on 2009-07-15
Thanks for the support. I think i still have one problem, we have have a proxy server managing internet access, during the initial setup, i inputted xxx03-xxxx:8080 (x represents letters). Issuing the commands in your replies, it responds "failed to fetch http:us.archive.ubuntu......" cannot initite the connection to 8080:80(0.0.31.144). - connect (22 invalid argument)...couldn't find package ubuntu-desktop. question 1: was something wrong with the proxy configuration? q2: how can i rectify this using the console.

Cheers,

points:

"host yahoo.com" yields yahoo.com has address 69.147.114.224, yahoo.com mail is handled by 1 a.mx.mail.yahoo.com. - DNS seems to be working well.

server currently uses DHCP address

I have a screen attached the the server

---

### Post by bodhi.zazen on 2009-07-16
You have to configure apt-get to use your proxy :

[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy)

---


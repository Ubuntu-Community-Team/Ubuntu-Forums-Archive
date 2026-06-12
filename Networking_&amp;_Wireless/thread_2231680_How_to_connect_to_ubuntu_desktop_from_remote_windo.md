---
title: "How to connect to ubuntu desktop from remote windows 7?"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by keymoo on 2014-06-27
Seems like a simple problem, but I've yet to find a solution.

I have a Windows 7 desktop machine and I need to connect over the LAN to an Ubuntu 14.04 desktop. I installed xrdp but all I got was this:

[IMG]http://i.imgur.com/CJJi2eK.png[/IMG]

Any other ideas?

---

### Post by keymoo on 2014-06-30
So, noone knows how to connect to Ubuntu from Windows? Hasn't anybody done this?

---

### Post by steeldriver on 2014-06-30
There are several solutions - VNC, FreeNX and so on - although these require you to install a (free) client program on the windows machine. Alternatively you can try to get xrdp working - it looks like you have basic connectivity, but need to specify a desktop session in place of the default gray root window.

---

### Post by Martin_Hansen on 2014-06-30
Hi,
The problem is that gnome and ubuntu-2d doesnt work anymore, so you have to use an alternative, such as xfce.
how to setup.
go to terminal then in the terminal write: **sudo apt-get install xfce4** or **sudo apt-get install xfce4-session **(I dont remember which one)
after that go to your .xsession file and write this in instead: xfce4-session and then try to connect.
Hope it helps :) .

---

### Post by gordintoronto on 2014-06-30
Another alternative is to use Teamviewer, free for personal use.

---


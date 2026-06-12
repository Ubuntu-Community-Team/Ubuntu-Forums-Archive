---
title: "[SOLVED] KDE black screen"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by joshmuffin on 2009-01-08
Hello, and thanks in advance.

I just recently install KDE using
```
sudo apt-get install kubuntu-desktop
```
I tried to select KDE as my session through "options" during login
It asked me if I want to make it my default blah.
Then I got a screen with just a background an a rectangle with a hard drive inside. I clicked the hard drive icon then it went to a black screen with my mouse and nothing. It was just stuck there.

P.S. I noticed my default session was "run Xclient script"

---

### Post by cmnorton on 2009-01-09
You may need to reconfigure your X server.

1) Boot into recovery

2) dpkg-reconfigure xserver-xorg

3) Take default answers, but consider other resolutions and perhaps using another driver.

Also, using CTRL+ALT+F1 would allow you to log in non-graphically, and you might be able to find something of interest in your logs (/var/log*) paying particular attention to syslog and messages.

---

### Post by joshmuffin on 2009-01-10
Thanks a re-configure did it.

---

### Post by BSAB_80 on 2009-02-22
I'm having a similar problem. Some packages upgraded during the night, didn't notice which ones, and at one point an hour ago the system froze up and I had to restart. First I re-encountered the same problem I have after some updates where the log-in text is enormous, so I had to edit /etc/kde4/kdm/kdmrc to -dpi 96 in the server command line, which solved the problem, but now when I log in to kde I only get the same black screen with the mouse pointer that the previous poster had.
Tried to reconfigure the xserver as advised but to no avail.
Anyone can help?
I'm running KDE4 (.2, maybe? Not sure)

---


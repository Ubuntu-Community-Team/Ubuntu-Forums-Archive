---
title: "Got my Linksys WPC11 v.2 (RTL8180) card working"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by midtoad on 2006-11-23
I got my Linksys WPC11 (version 2.0) card working. It is automatically detected by Ubuntu Edgy Eft's RTL8180 driver.  I was quickly able to get it to connect to unsecured networks, but for the life of me couldn't get it to connect to my WEP-secured network.  (The series of posts on Broadcom cards has lots of good tips).  

Finally I saw a [post on getting a WEP key 2 to be recognized]("http://www.ubuntuforums.org/showthread.php?t=291293&highlight=wireless+network+applet").  Since I had a question as to whether my key is hex or ascii, I decided to read that post. I saw that the forum helper suggested how to specify key 2 in the /etc/network/interfaces.  I use key 1 and haven't specified the number of that key (none of the various posts suggest doing that), but I decided to give it a try.  Here's what I put in /etc/network/interfaces:
```
iface wlan0 inet static
    address 192.168.1.97
    netmask 255.255.255.0
    gateway 192.168.1.2
    wireless-essid midtoad
    wireless-key1 ABCDEAABABCDEAABABCDEAAB01
    wireless-defaultkey 1
auto wlan0
```

I then brought up the interface with:
```
sudo ifup wlan0
```
and I was connected!

I can't tell you how many hours I've spent on this... [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)  I actually gave up on my other wireless card, a Netgear WG511 v.3.0, as I could never get the ndiswrapper-loaded Windows drivers to light up the card.

---

### Post by Titus A Duxass on 2006-11-24
My linksys WPC11 ver. 4 and my edimax EW-7126 (pci) both use the RTL8180 and like yours mine are running perfect and have done since dapper.

WEP is also no problem.

---

### Post by locura2584 on 2007-03-18
I have a WPC11 ver 2.1 and I can't find out how to make it work.
Any help would be appreciated

---


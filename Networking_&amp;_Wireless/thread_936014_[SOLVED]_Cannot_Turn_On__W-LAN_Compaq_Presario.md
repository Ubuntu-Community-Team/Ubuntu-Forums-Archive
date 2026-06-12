---
title: "[SOLVED] Cannot Turn On  W-LAN Compaq Presario"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Batsmasher on 2008-10-02
Hey everyone, I have a Compaq Presario C700 and can't connect to the internet.  The laptop has a LAN Button to turn on and off Wi-Fi LAN, but when I press it, it doesn't turn on my LAN.  I do have all the specs here: [http://paste.ubuntu.com/53199/](http://paste.ubuntu.com/53199/). The drivers are installed for the Atheros, so I don't think that is the problem, but I think it's because I can't turn my card on.  The W-LAN works in Vista and automatically turns on. 
Thanks in advance ~Batsmasher

---

### Post by superprash2003 on 2008-10-02
in your terminal type lshw -C network and post output

---

### Post by Batsmasher on 2008-10-02
Here it is: [http://paste.ubuntu.com/53338/](http://paste.ubuntu.com/53338/)

---

### Post by superprash2003 on 2008-10-03
hope this helps [http://ubuntuforums.org/showthread.php?t=766169&page=2](http://ubuntuforums.org/showthread.php?t=766169&page=2)

---

### Post by Batsmasher on 2008-10-07
I've tried most of the tutorials by now, none of which are working, is it true that Hardy doesn't do well with inbuilt WLAN cards?

---

### Post by willca on 2008-10-07
Can you do this.

iwconfig 
sudo iwlist wlan0 scan or sudo iwlist ath0 scan

sudo dpkg -l | grep -i atheros

---

### Post by Batsmasher on 2008-10-08
Awesome guys, got it working, it was as easy as truning the card back on in Vista.  I did need ndiswrapper to get the driver though, thanks for the help :) \o/

---


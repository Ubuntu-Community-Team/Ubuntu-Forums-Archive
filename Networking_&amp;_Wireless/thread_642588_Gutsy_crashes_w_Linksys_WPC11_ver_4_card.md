---
title: "Gutsy crashes w/ Linksys WPC11 ver 4 card"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by kanh on 2007-12-16
I just did a clean install of Gutsy 7.10 and am having a problem w/ my wireless card Linksys WPC11 Ver 4.  Before the clean install I was  running Feisty 7.04 and the wireless was working fine (I had installed ndiswrapper and windows drivers).  I upgraded from 7.04 to 7.10 and everything seemed to work OK except whenever I tried to log into my network Gutsy crashed (froze) and the cap and scroll lights started blinking on and off.  I then tried a clean install from the alternate CD for Gutsy 7.10 and the install went fine except, again,  when I tried to activate my wireless card (inputting my security info)  the system crashed and the cap lock and scroll lock lights started blinking on and off.  Gutsy recognizes the card which is neat and a lot easier, with Feisty I had to go through the ndiswrapper install etc.  Anyone have any ideas?  I'm new to Linux but am having a great time learning and enjoy working w/ the OS a lot!  Thanks

---

### Post by NotTheCommonDose on 2008-01-09
I have the same problem :(

---

### Post by NotTheCommonDose on 2008-01-09
FIXED! I hope this reaches you well. I had the same problem, my laptop would freeze whenever I used the WPC11. ver4 wireless pcmcia card. The caps lock would blink and I would have to restart. However, if you go here;
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)
and install the 98 version of the driver with ndiswrapper or system>administrator>windows wireless drivers you should be a-ok!

I hope this helps!
James

---

### Post by rawirth on 2008-01-19
Card is the same. Downloded driver, installed ndiswrapper, utilities and ndisgtk, installed tried to blacklist free drivers but keyed in ' twice so the command is bad and I cannot edit the blacklist file because it says it belongs to the root. Either way it says the 8180.inf driver is not a valid driver. Took these steps from the WifiDocs/Driver/Ndiswrapper documentation. The system says the 8180 is loaded when i try to reload it but when I look for list after having installed the driver, 'sudo ndiswrapper -i ~/drivers/drivername.inf' ( using proper names and files),when I list drivers, 'ndiswrapper -l', i get the not valid driver.

---

### Post by Sam Lars on 2008-03-23
You need to use sudo to edit files that are owned by root.
```
sudo nano
```
in a command line or
```
sudo gedit
```
if you have a GUI.
Try the XP drivers.

---


---
title: "Wireless not working in 7.10 but did in 7.4"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by lmohdlp on 2007-10-20
I've upgraded to 7.10 and it is awesome but my wireless is not working persay....... it sees my nlinksys network (it's unprotected) shows the signal strength but it is not conecting it just sits there..... then stops, I am using a  linksys b network adapter (the usb type) on my laptop and before I upgraded it worked fine and right away on feisty. Right now I am running the live cd of feisty, if anyone could please help I would love you forever lol. I am a noob and I reallly like ubuntu just can't use it if my wireless isn't going to work and will have to revert back to windows xp (not vista... that thing is horrid)

---

### Post by lmohdlp on 2007-10-20
Please Help!

---

### Post by Architeuthis on 2007-10-20
I think you have just the same issue as many others (like me) are having, check out this thread: [http://ubuntuforums.org/showthread.php?t=582033](http://ubuntuforums.org/showthread.php?t=582033)

---

### Post by kevdog on 2007-10-20
Got to supply more info about chipset and driver you are using with any possible errors you are getting .. I cant read your computer's mind

---

### Post by lmohdlp on 2007-10-20
there are no errors or anything poppng up it isn't connectng and thanks for that thread up there i've been keeping a close eye on it now.

---

### Post by Trueno22 on 2007-10-20
Add this to your sources.list
> deb [http://wicd.longren.org](http://wicd.longren.org) gutsy all

then go to terminal and type:

> sudo apt-get install wicd

It will automaticlly remove the Network Manager which is the problem with your connection and use Wicd as the default.

To get it to pop up automaticaly at bootdo the following
> In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For a command, enter "/opt/Wicd/tray.py". In KDE, run the following command from a terminal:

    sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py

You can open the main window by left clicking on the tray.


---

### Post by lmohdlp on 2007-10-20
So this will make it work?

---

### Post by lmohdlp on 2007-10-20
this is the most annoying thing in the world someone please help?

---

### Post by james957 on 2007-10-20
I'm having the same problem.  I can see the wireless networks, but can't connect.

I enabled the restricted drivers (before I did that, I couldn't see the wireless networks) and rebooted.

>> sudo iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:1B:6C:BD
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-60 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 6856ms ago
          Cell 02 - Address: 00:0F:B5:EC:62:54
                    ESSID:"shakedown st"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-74 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 68ms ago


------------------------------

What the heck?  I tried Wicd, but same problem. It could see but not connect.

---

### Post by james957 on 2007-10-20
More info:

>>  lspci | grep Broadcom
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by jardo on 2007-10-21
i think the problem is that u have that wireless card...i have your similar problems....see the network but can't always connect to it...and if connected not always a stable speed....
try to use ndiswrapper...if u want to know more about that card and problem i had type bcm94311mcg in the search field

---

### Post by james957 on 2007-10-21
Jardo,

Can you use roaming mode with Ndiswrapper?

Thanks,
James

---

### Post by jardo on 2007-10-22
sure you can

---

### Post by raananb on 2007-11-05
The solution posted earlier by Trueno22 (Wicd) solved my problem on ASUS F5V laptop with an integrated Atheros AR5006EG wireless card.

---


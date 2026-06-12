---
title: "connecting internet"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by shrimpboi13 on 2009-01-21
i'm completely new to linux and chose ubuntu to evade impending vista. i have installed linux succesfully but i have not the faintest idea how to connect the internet. I'm using a toshiba satellite with an inbuilt modem and have a dail-up plan with an ISP working on my windows PC. any basic guidance would be greatly appreciated.

---

### Post by mjheagle8 on 2009-01-21
use network manager. its in the notification area (defaults to the top right of your screen). just select a network off the network list there.

---

### Post by shrimpboi13 on 2009-01-21
thankyou for your help i tried this suggestion to no avail everything is blacked out except vpn connections i fiddled with this for a little while but couldn't make anything happen. do i have a problem with my modem?

---

### Post by Shazaam on 2009-01-21
Network Manager no longer has a dial-up config feature.
Here you go if your modem is detected...
1. Open terminal (Applications>Accessories>Terminal)
2. When it opens type this in and hit enter...
```
gksudo gedit /etc/wvdial.conf
```
it will ask for a password, use the password that you use to log into Ubuntu.
3. When it opens you will see this...
```
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes
```
Enter your info, go up to "File>Save" and then close it.
4. Type this into terminal...
```
wvdial
```
DON'T CLOSE TERMINAL!
5.If your modem is detected it should connect. If connected go to System>Administration>Synaptic Package Manager and click "Reload".
6. When it is done reloading/updating find gnome-ppp in Synaptic and install it.
7. Once gnome-ppp is installed open it and go to "Setup" and add your info.
8. Reboot and try Gnome PPP (Applications>Internet).
If wvdial doesn't connect you may need proprietary drivers for your built in modem. Post back with your results.

---

### Post by mjheagle8 on 2009-01-21
nvm, didnt read that last post.

---

### Post by shrimpboi13 on 2009-01-22
thanks for the reply
i think your right about the propriety drivers because when i typed wvdial the response was 

"cannot open /dev/modem: no such file or directory"

If it helps at all; in windows the modem shows up as a "toshiba software modem" and the toshiba site says the laptop comes with an "international v.92 data modem" 
the laptop itself is a toshiba satellite m110 psmboa-oilood

---


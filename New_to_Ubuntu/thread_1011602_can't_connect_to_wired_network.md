---
title: "can't connect to wired network"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by sameer.india on 2008-12-14
I am using ibex and am unable to connect to wired network

---

### Post by frankleeee on 2008-12-14
So have you right clicked on the icons in the notification area and clicked on edit connections.

---

### Post by sameer.india on 2008-12-14
yes

---

### Post by frankleeee on 2008-12-14
Okay, so is it a DHCP connection and is it set to connect automatically, you need to give more information as to what you have tried. For example do you need a password, and have you contacted your provider. Also if you right click on connection information is it showing the IP addresses.

---

### Post by sameer.india on 2008-12-14
my interfaces file reads 

auto lo
auto lo inet loopback

---

### Post by sameer.india on 2008-12-14
I have been using the wireless network successfully in the past

---

### Post by ja660k on 2008-12-15
try open terminal and type
```

sudo dhclient eth0

```

where eth0 is the name of your network port.
that will hopefully "force" connect your computer

---

### Post by frankleeee on 2008-12-15
That is just what your computer is using what we need is the IP and broadcast showing up in the connection information when you right click on the two tiny computers in the notification area. These should be the same as the number sequences if you run ifconfig in the terminal. Open the edit connections as well and take screen shots of the three tabs in edit auto etho if you want. I suspect that you have the 802.1x in the edit auto or etho ticked on and don't have the needed information included, I just do a direct connect personally and have this off.

---

### Post by Poyntz on 2008-12-15
1. also, try unplugging the power cord from your router. 
Wait about 15 seconds.
Plug it back in. 
Ensure you're getting an ADSL reading on your router. And possible port readings as well (these should hopefully be displayed on the router).
If the port readings fail check your cord to see if it's plugged in to both the router port and your computer port.
If that fails the cord may be damaged, do you have a spare?
2. Now on a ubuntu level try typing in a terminal **ifconfig** and see what appears.
if you see something that resembles **eth0** it's probably your ethernet card.
3. open /etc/network/interfaces in a text editor with admin privs
eg, ```
sudo vim /etc/network/interfaces
```
4. make a backup of the file
5. now, add the lines:
[B]auto eth0
iface eth0 inet dhcp[/B]
- that's providing of course that your router uses dhcp and eth0 is the name of your ethernet card. 
also, make sure that the lines:
[B]auto lo
iface lo inet loopback[/B] are present in the file. 
(They should be there by default)
6. once you've made the changes, save the file and exit the text editor.
7. now in terminal type:
```
source /etc/network/interfaces && sudo ifup -a
```
8. When it's finished try plugging in your cable.

---

### Post by sameer.india on 2008-12-15
I can't give you ip addresses unless it connects
in windows xp it is
Ip: 116.72.81.184
and the 802.1x is disabled
ifup gives 
Ignoring Interface eth0=eth0
if down gives 
eth0 not configured

---

### Post by Poyntz on 2008-12-15
open a terminal and type **sudo NetworkManager**
You may be able to add eth0 before trying what was listed above

---

### Post by frankleeee on 2008-12-15
Thanks for helping fellow posters' I have never had a problem here and am not a geek.

---

### Post by sameer.india on 2008-12-15
the network is added as auto eth0 under wired networks but just doesn't connect
and when I tried 'all that'
the left click on the network icon shows unmanaged device under wired network

---

### Post by Poyntz on 2008-12-15
is there any way to switch it to managed? see if you can.

---

### Post by sameer.india on 2008-12-15
yes i.e going back to the original interfaces file

---


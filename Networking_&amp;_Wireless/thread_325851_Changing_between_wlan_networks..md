---
title: "Changing between wlan networks."
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Shack on 2006-12-26
Hey there. 

I've installed my DWL-G122 usb adapter and RT73 driver. 
Now if I wan't to change between wlan networks what is the best software for it?

At work we use WPA but at home I use WEB and Mac-filtering. My adapter is working fine at home, but how can I manage it at my workplace? **Is there any good software for controlling different wlans? And does RT73 driver support WPA encryption or do I have to install some more packets?**

---

### Post by raldz on 2006-12-26
install:

connection-manager
and
connection-manager-systray

then add connection-manager-systray to System>Preferences> Session>startup

---

### Post by Shack on 2006-12-26
> **raldz said:**
> install:

connection-manager
and
connection-manager-systray

then add connection-manager-systray to System>Preferences> Session>startup

Thanks. I'll try this later on and will post my comments.

---

### Post by Shack on 2006-12-26
Ok. 

I downloaded connection manager but when I click .dev file I get: 
"error: Depency is not satisfiable: libwxgtk2,6-0"

When I try to install libwxgtk2.6-0 it gives me same kind of error about some other depency. 
Which packets should be installed to make connection manager install succesfull.

I didn't find any help or readme files about connection manager, if there is any?

Thank.

---

### Post by raldz on 2006-12-26
check out this thread for installation issues:

[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

---

### Post by jml on 2006-12-26
You didn't mention the version of Ubuntu you are using.  Assuming its 6.10, I would recommend downloading and installing two applications.  network-manager and network-manager-gnome.  This application supports WPA encryption and it makes switching between different access points easier.  Hope this helps.

Joe

---

### Post by fredj on 2006-12-27
The problem with network-manager and network-manager-gnome is that they are very unstable
and drop the connection at random under both Dapper and Edgy. Try them if you want to and
see how they perform for your wireless card.

---

### Post by Shack on 2006-12-27
I have network manager installed, but it doesn't appear to my software list? 
I know I have to uninstall it if I wan't to use connection manager, but I have problems with both.

I'll check that installing issues thread later.

Thank you.

---

### Post by robbie75 on 2006-12-27
Connection-manager worked well for me but
the issue (to me) was that it does not manage
static ip settings....only dhcp sigh sob

I think that the real solution would be a new
gnome network-admin wich cares about wpa....

To me network-admin is perfect since it's able to
manage every interface along with resolv.con and
hosts files...but the wifi support is too poor :-|

---


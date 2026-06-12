---
title: "Cannot get the &quot;connect button&quot; to work."
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by Fabyfakid on 2007-11-27
Hi, I'm using a wireless connection in my campus. My laptop's an HP Pavilion ze2000, that has a button that starts that connection. I haven't been able to access it using Linux, so I went to the system administrator, who told me it had to do with the OS not recognizing that function (although it does recognize the card). I don't know what drivers to get as I don't know what sort of components are involved in that (it's not like it's just a problem with a modem or a broadband card). What do you suggest? thanks in advanced...

EDIT: lol, forgot to mention that I'm using Feisty.

---

### Post by mellowd on 2007-11-27
Could you open up a terminal and type this:

```
less /etc/network/interfaces
```

What do you see there?

---

### Post by Fabyfakid on 2007-11-27
This is what I got:

> auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





auto eth0

---

### Post by Fabyfakid on 2007-11-27
*bump*

I really need help with this, guys.

---

### Post by mellowd on 2007-11-28
I'm a bit confused here. You say there is a button that starts the connection. Can you go into a little more depth? Is that just your standard wireless link? is it some sort of vpn? is it some sort of local software thats installed for a special type of link? Whats the name of this software?

---

### Post by Fabyfakid on 2007-11-28
Check out these pics:

[IMG]http://img.fj007.com/news/2007/3/20073221783980670.jpg[/IMG]

[IMG]http://www.notebookreview.com/assets/7110.jpg[/IMG]

Do you see that top right button that's illuminated (the **[COLOR="Cyan"]"I"[/COLOR]** one)? That's the one that must be pressed in order to turn on the wireless internet. Under Feisty, that button doesn't work apparently. I really don't know what sort of program's involved in that function (I'm a pretty big newb to Linux, and have VERY little knowledge of networking tech).

---

### Post by mellowd on 2007-11-28
Aha, I see.

For this to work you'll need a driver. You could have a look at the hp website to see if they have a drivers for this model and linux.

If not you'll need to find a hacked driver that someone has made, I'm not sure if this has been done.

---


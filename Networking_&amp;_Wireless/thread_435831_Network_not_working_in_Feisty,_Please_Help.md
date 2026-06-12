---
title: "Network not working in Feisty, Please Help"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by JordanII on 2007-05-07
My Ubuntu Feisty computer is networked to a Windows XP computer for internet. It was working fine until this morning. The network applet on the Gnome panel had a little red error circle over it. I tried to use the internet and it didn't work. I clicked on the applet and I got this message:

```
Please contact your system administrator to resolve the following problem:

Could not find information on interface 'eth0:avahi' in /proc/net/dev
```

I don't really understand the message because I am an administrator. Or am I supposed to log in as root? If so I have no idea what the root password is. Does anyone know how to take care of this? Thanks!

~Jordan

---

### Post by JordanII on 2007-05-07
This is really weird because I tried it in XFCE and it worked fine. It does not work in Gnome though.

---

### Post by VolvoPunch on 2007-05-07
I don't even think you can network another computer to an xp box because it can't give out ip to my knowlage. You will need a router for this. 

Go into your menu system > networking and type in your user password when the window pop up. Then make sure the conection is actovated and that dhcp is turned on.

---

### Post by JordanII on 2007-05-07
> **VolvoPunch said:**
> I don't even think you can network another computer to an xp box because it can't give out ip to my knowlage. You will need a router for this. 

Go into your menu system > networking and type in your user password when the window pop up. Then make sure the conection is actovated and that dhcp is turned on.

After I restarted Gnome (after using XFCE) the error was still there but the internet works fine. Actually, believe it or not I didn't even have to setup the network, all I did was plug in the cable and it worked. Maybe it's something new in Feisty.

~Jordan

---

### Post by VolvoPunch on 2007-05-07
> **JordanII said:**
> After I restarted Gnome (after using XFCE) the error was still there but the internet works fine. Actually, believe it or not I didn't even have to setup the network, all I did was plug in the cable and it worked. Maybe it's something new in Feisty.

~Jordan

Glad to hear you fix the problem. :guitar:

---


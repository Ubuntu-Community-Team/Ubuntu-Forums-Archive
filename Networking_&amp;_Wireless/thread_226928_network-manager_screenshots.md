---
title: "network-manager screenshots"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by krypto_wizard on 2006-07-31
Hi all,

I had trouble setting up network-manager in my Dapper for some reasons.
I have installed network-maanger and network-manager-gnome, but I don't see an icon in the tray.

Can you please post some screenshots of network-manager so that I will be able to visualize how it looks.

Thanks

---

### Post by crmanski on 2006-07-31
> **krypto_wizard said:**
> Hi all,

I had trouble setting up network-manager in my Dapper for some reasons.
I have installed network-maanger and network-manager-gnome, but I don't see an icon in the tray.

Can you please post some screenshots of network-manager so that I will be able to visualize how it looks.

Thanks

These are the steps I used to setup my laptop after installing network-maanger and network-manager-gnome...

```
sudo gedit /etc/network/interfaces
```
Put a # in front of everything except the part that says...
auto lo
iface lo inet loopback
Save the file.

Go to the System menu->Preferences->Sessions.
Put this under startup programs (if it is not there)
```
nm-applet --sm-disable
```

Reboot and you should see it.

---

### Post by krypto_wizard on 2006-08-01
I already have it in my start up. I modified the file as you said. But it didnt come up.
```
nm-applet --sm-disable
```

One green icon comes up but it doesnt give me any choices....to change network I have to open the network windows change network there which again takes 2 minutes to update....there is nothing like an icon on tray.

Where am i going wrong ?

Thanks

---

### Post by krypto_wizard on 2006-08-01
```
nm-applet --sm-disable
```

If I just type on console the above command the icon comes on to the tray but even though its in start up program it never shows up...or may be gets killed by some program.

What should I do ?

Whats the difference between
```

nm-applet and nm-applet --sm-disable

```

Thanks for help

---

### Post by crmanski on 2006-08-01
I'm not certian what it would be. I would look at this thread in the forum and see if something there helps...
[http://www.ubuntuforums.org/showthread.php?t=156319](http://www.ubuntuforums.org/showthread.php?t=156319)

---


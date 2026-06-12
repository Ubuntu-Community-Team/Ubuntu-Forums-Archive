---
title: "Jaunty: lost my wireless tray applet AND application panel menu"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by hoink on 2009-09-02
1) I installed wicd then uninstalled it and now I have no wireless networking or applet in the tray/notication area.

2) In a stupid, unlucky twitch of my finger, I just deleted my app launcher panel.  SOLVED: Right click on panel, "Add to panel...", "Main Menu"  (seems obvious when not insanely frustrated)

What a night.

Lil help?

---

### Post by hoink on 2009-09-02
I still have the panel, just not the menu system that was there.  GAH!

---

### Post by nothingspecial on 2009-09-02
Right click on the panel, choose add to panel. I think notification area is the one you want.

---

### Post by tgeer43 on 2009-09-02
Actually it's called 'Menu Bar'.

Then you could try reinstalling 'network-manager-gnome' in Synaptic Package Manager as that is the package which contains the network panel applet.

tgeer

---

### Post by hoink on 2009-09-02
Nah, I still have my notification area.  I "just" lack the wireless connection applet that use to live there.

Thx though.

---

### Post by nothingspecial on 2009-09-02
Missunderstood.

Type ```
nm-applet
```

---

### Post by hoink on 2009-09-02
> **tgeer43 said:**
> Actually it's called 'Menu Bar'.

Then you could try reinstalling 'network-manager-gnome' in Synaptic Package Manager as that is the package which contains the network panel applet.

tgeer

Well, wicd obliterated my net connection too.  And (I just checked) uninstalled network-manager-gnome.

Can you advise on how to get my wifi back up without a net connection?  (I'm currently typing on my non-LAN-but-net-connected Windows box.  Connecting to the net via that is... not a good idea.)

---

### Post by nothingspecial on 2009-09-02
```
sudo ifconfig wlan0 up
```
```

sudo iwconfig wlan0 essid [COLOR="Red"]networkname_here[/COLOR]
```

```

sudo iwconfig wlan0 key [COLOR="Red"]passphrase_here[/COLOR]
```
```

sudo dhclient
```
```

sudo apt-get install network-manager
```

---

### Post by hoink on 2009-09-02
GOT IT.  Got my connection back up and reinstalled network-manager-gnome, rebooted and felt IMMENSE relief.  

Thanks, nothingspecial.

---

### Post by nothingspecial on 2009-09-02
No problem :D

---


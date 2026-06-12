---
title: "Can't right-click to view properties on panel"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by kristine12 on 2009-11-30
My sister is playing with our computer then suddenly I've notice that the content of the pop-up menu when right-click to the panel have been change. Then I can't anymore modify the panel using its properties.

Before: 
[IMG]http://i303.photobucket.com/albums/nn152/x_x312/Before.png[/IMG]
I only downloaded this image from the web but the point is the pop-up menu. From that kind of pop-up menu it change to:
[IMG]http://i303.photobucket.com/albums/nn152/x_x312/After.png[/IMG]
I really want to customize my panel. I have read that panel can be modified from gconf-editor but there is a risk the I can also modify other things unwanted. So I just want to modify it using the right-click pop-up menu.
Please help me to return that kind of pop-up menu...
Using Ubuntu 9.04...
Thanks in advance!!!!

> Please just try to understand my English because I'm not good at it. Constructing of sentences. ^_^

---

### Post by ukripper on 2009-11-30
In terminal do following to restore back to default panel:
```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel

```

logout and log back in again.

---

### Post by kristine12 on 2009-12-01
> **ukripper said:**
> In terminal do following to restore back to default panel:
```
gconftool-2 --shutdown
``````
rm -rf ~/.gconf/apps/panel
``````
pkill gnome-panel

```logout and log back in again.


Don't take me wrong but...
Can you please **explain your code**.
Just trying to be safe.

---

### Post by ukripper on 2009-12-01
Sure.

This will shutdown curently running gconf editing daemon (**gconfd** service) temperorly for the user.
```
gconftool-2 --shutdown
```

This will get rid of your current panel for your username only from your home
```
rm -rf ~/.gconf/apps/panel
```

This will kill(stop) all currently running panels for your user account
```
pkill gnome-panel

```

Once you log back in again, panels will be recreated and restored to default settings.


Hope that helps

---


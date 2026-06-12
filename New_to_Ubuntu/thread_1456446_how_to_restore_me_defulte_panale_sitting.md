---
title: "how to restore me defulte panale sitting ??"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by subsam on 2010-04-17
yesterday i can't log in to my two disks and i have a massage 
unable to mount file system authentication is required
after this i use this solution to log in to my partions 


[http://rayslinux.blogspot.com/2009/12/authentication-is-required-to-mount.html#comment-form](http://rayslinux.blogspot.com/2009/12/authentication-is-required-to-mount.html#comment-form)


and it succeded to let me inter my partions ,,but now :-
1. I am not able to see Battery notification and Network notification and sound 
2. I am not able to lock my screen

---

### Post by Aquatic Fist on 2010-04-17
Right click on the panel and press "Add To Panel"

Add "Notification Area". Network, Battery, Sound should be there by default I think. If it's not you can start them by doing this.

Alt + f2 and type:

For Battery:  gnome-power-manager
For Network:  nm-applet
For Sound: gnome-volume-control-applet

For the Lock. Add "Indicator Applet" or "Lock Screen" in the "Add to Panel" window. Or you can quickly press Ctrl + Alt + L and it locks the screen. :)

Hope this helps!

---

### Post by d3v1150m471c on 2010-04-17
you can delete .gconf and .gconfd and it will restore ALL of gnome back to it's defaults and then recreate the two files after loging in again.

---

### Post by philinux on 2010-04-17
```
sudo debconf gnome-panel
```

Should do the trick.

---

### Post by subsam on 2010-04-17
> **philinux said:**
> ```
sudo debconf gnome-panel
```

Should do the trick.


(gnome-panel:2318): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2318): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

---

### Post by subsam on 2010-04-17
> **Aquatic Fist said:**
> Right click on the panel and press "Add To Panel"

Add "Notification Area". Network, Battery, Sound should be there by default I think. If it's not you can start them by doing this.

Alt + f2 and type:

For Battery:  gnome-power-manager
For Network:  nm-applet
For Sound: gnome-volume-control-applet

For the Lock. Add "Indicator Applet" or "Lock Screen" in the "Add to Panel" window. Or you can quickly press Ctrl + Alt + L and it locks the screen. :)

Hope this helps!

not working :(

---

### Post by theozzlives on 2010-04-17
You want to add the notification area and the indicator applet session.

---

### Post by philinux on 2010-04-17
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Make sure to copy and paste the commands.

Instead of using thr rm command which can be bad is used incorrectly you can use nautilus to delete the folder mentioned.

---

### Post by subsam on 2010-04-17
> **philinux said:**
> [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Make sure to copy and paste the commands.

Instead of using thr rm command which can be bad is used incorrectly you can use nautilus to delete the folder mentioned.

i'm sry 
ur link not working :(

---

### Post by sisco311 on 2010-04-17
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

You may have to start the panels manually:
```
gnome-panel &> /dev/null &
disown

```

---

### Post by subsam on 2010-04-18
> **sisco311 said:**
> ```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

You may have to start the panels manually:
```
gnome-panel &> /dev/null &
disown

```

nothing happened Dear :(

---


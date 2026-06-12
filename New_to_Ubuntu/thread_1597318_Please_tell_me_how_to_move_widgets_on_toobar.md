---
title: "Please tell me how to move widgets on toobar"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by metalaxesucks on 2010-10-15
See how all my widgets are on the left hand side
[https://sites.google.com/site/blahblahoinkoink/home/hot](https://sites.google.com/site/blahblahoinkoink/home/hot)
As you can see I tried dragging them to the right, & they always spring back to the left.
It started when I was trying to add widgets to the toolbar & I clicked on something,I don't know what happend!
Thanks

---

### Post by JohnHeikkila on 2010-10-15
Right-Click on the empty space on the right. You may be able to delete the empty space, the separator.

---

### Post by kio_http on 2010-10-15
Firstly I would like to state that I think you are making a mistake. A toolbar in general is this
[IMG]http://upload.wikimedia.org/wikipedia/commons/b/b7/Application_toolbar.png[/IMG]

What you want to do I assume is make your taskbar be like the default KDE?

To achieve that, add a widget called Taskmanager to the **taskbar**. Then move that widget (called taskmanager) to right after the Desktop icon. Now everything should come back to normal.

Or reset KDE to defaults.

To do this.
Press ALT + F2
type ```
konsole
```
press enter
type in konsole
```
rm -rf .kde
```
press enter

Logout and Login

---

### Post by metalaxesucks on 2010-10-15
> **kio_http said:**
> Firstly I would like to state that I think you are making a mistake. A toolbar in general is this
[IMG]http://upload.wikimedia.org/wikipedia/commons/b/b7/Application_toolbar.png[/IMG]

What you want to do I assume is make your taskbar be like the default KDE?

To achieve that, add a widget called Taskmanager to the **taskbar**. Then move that widget (called taskmanager) to right after the Desktop icon. Now everything should come back to normal.

Or reset KDE to defaults.

To do this.
Press ALT + F2
type ```
konsole
```
press enter
type in konsole
```
rm -rf .kde
```
press enter

Logout and Login

Thank you so much kio_http, I added the taskmanager and everything went back to normal.
I usually use Ubuntu, but I had problems with the latest version (10.10) so I'm giving Kubuntu a shot.
Thanks again

---

### Post by kio_http on 2010-10-15
> **metalaxesucks said:**
> Thank you so much kio_http, I added the taskmanager and everything went back to normal.
I usually use Ubuntu, but I had problems with the latest version (10.10) so I'm giving Kubuntu a shot.
Thanks again

No problem. Enjoy using KDE. Note: Unfortunately due to cd disk space restrictions, you will notice that Kubuntu comes with a plain KDE, one wallpaper etc.

However since KDE has great customisability, you have to change it to your likings. Look for the missing kde wallpapers, themes etc in the repositories.

---


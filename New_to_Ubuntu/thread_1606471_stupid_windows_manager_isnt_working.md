---
title: "stupid windows manager isnt working"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by RIPwindows on 2010-10-26
hello guys i  was just tweaking my system and then removed some of those games that  come with ubuntu so then i restart and now whenever i open a program i  cant close resize or minimize (it does not show up). i presume it is a problem with my windows  manager and now when i open it from preferences this is what i get  ~Cannot start the preferences application for your window manager
 
Window manager "gnome-screensaver" has not registered a configuration  tool~ please help me i dont wanna go and install windows 7 again. Ihave ubuntu 10.10 hope you can help me with this problem


it also says disk mounter has not registered a configuration tool

---

### Post by duruttye on 2010-10-26
nautilus is the windows manager in ubuntu, try to launch it from a terminal. Maybe you removed more than you wanted...

In case you removed it also by mistake, install it back again.

terminal:

sudo apt-get install nautilus

then type in your password.

---

### Post by RIPwindows on 2010-10-26
nautilus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. that is what it says after i do what you said

---

### Post by duruttye on 2010-10-26
> **RIPwindows said:**
> nautilus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. that is what it says after i do what you said

what if you type ```
nautilus
``` in the terminal?

---

### Post by d3v1150m471c on 2010-10-26
backup your data then:

```

sudo apt-get --reinstall ubuntu-desktop

```

tom cruise only knows what dependency got flushed with your games so we'll try to heal your sick computer with a broad spectrum Tx.

---

### Post by duruttye on 2010-10-26
> **d3v1150m471c said:**
> backup your data then:

```

sudo apt-get --reinstall ubuntu-desktop

```

tom cruise only knows what dependency got flushed with your games so we'll try to heal your sick computer with a broad spectrum Tx.


classy :)
won't that bring back the games, also?

---

### Post by d3v1150m471c on 2010-10-26
if it does and you delete them again at least you'll know what's getting removed with them when you "sudo apt-get uninstall". see apt-oops on my signature. it's not a fancy program but it's saved me a load of grief. if not you can always
```

sudo apt-get remove yourgames -y > output.txt

```

---

### Post by sandyd on 2010-10-26
> **RIPwindows said:**
> hello guys i  was just tweaking my system and then removed some of those games that  come with ubuntu so then i restart and now whenever i open a program i  cant close resize or minimize (it does not show up). i presume it is a problem with my windows  manager and now when i open it from preferences this is what i get  ~Cannot start the preferences application for your window manager
 
Window manager "gnome-screensaver" has not registered a configuration  tool~ please help me i dont wanna go and install windows 7 again. Ihave ubuntu 10.10 hope you can help me with this problem


it also says disk mounter has not registered a configuration tool

nice. you removed metacity wm
```

sudo apt-get install metacity metacity-common
metacity --replace
```

---


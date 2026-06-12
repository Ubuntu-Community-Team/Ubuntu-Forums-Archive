---
title: "nvida config"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by davellew69 on 2009-05-15
hi, is anyone able to help? i need to run nvida as a root, then restart x server? any pointer in the right direction would be gratefully  revived

---

### Post by Gausian on 2009-05-15
```
sudo nvidia-settings
```

---

### Post by davellew69 on 2009-05-15
thanks i`ll give it a go

---

### Post by Kosimo on 2009-05-15
> **Gausian said:**
> ```
sudo nvidia-settings
```

Shouldn't be necessary to run it as a root

---

### Post by NightwishFan on 2009-05-15
Nvidia Settings needs to be run at login for it to take effect, as it only applies settings once it was run. I believe that running it as root will not accomplish anything. Just add this to your GNOME-Session (Startup Applications).

```

nvidia-settings -l

```

The -l means 'Load config only' which will not start a GUI and just apply the custom settings for your user.

---

### Post by davellew69 on 2009-05-15
sorry nothing happend all i get is a nivda box????

---

### Post by davellew69 on 2009-05-15
what do i do from here?

---

### Post by NightwishFan on 2009-05-15
Press alt+f2 and type:

```

jockey-gtk

```

It says you currently are not using the Nvidia driver, this will check to see if it is installed or enabled.

---

### Post by davellew69 on 2009-05-15
im grateful for the help but im lost in what to do?

---

### Post by NightwishFan on 2009-05-15
The restricted drivers application (jockey-gtk) should tell you if you have Nvidia drivers available or activated. Show me a screenshot of that.

---

### Post by davellew69 on 2009-05-15
does this help

---

### Post by NightwishFan on 2009-05-15
It appears you do not have a compatible or a detected Nvidia card. Do you know what kind of graphic hardware you own? If not, install this little utility. In a terminal type:

```

sudo apt-get install sysinfo

```

Then press alt+f2 and type:

```

sysinfo

```

There should be a hardware tab, and a drop down menu that shows your graphics hardware.

---

### Post by davellew69 on 2009-05-15
nothing?

---

### Post by NightwishFan on 2009-05-15
You are running another package manager I think. Close it, and try again. If you are not, save your work, and log out and back in. Then try my command again.

---

### Post by Ericj1186 on 2009-05-15
Misread the image.

---

### Post by davellew69 on 2009-05-15
what next ?

---

### Post by davellew69 on 2009-05-15
screenshot

---

### Post by davellew69 on 2009-05-15
?

---

### Post by NightwishFan on 2009-05-16
Sorry I was offline, though I am back until a bit before 9:00AM Eastern.

I need to know your model, please click the drop down arrow. I can at least say it is likely not a Nvidia card.

---


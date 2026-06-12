---
title: "I need a meter in XFCE"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by psycosmyth on 2006-08-19
In gnome and kde the wireless tools' strength meter can be put in the taskbar but I had to go back to xfce for cleanliness and all I need now is a meter bar in my taskbar, how??:confused:

---

### Post by LKRaider on 2006-08-19
Did you try xfce4-wavelan-plugin available on Synaptic?

I am not using it because my wifi card doesn't report signal strength anyways, so I am just using Netswitch (and now trying Wifi-Radar) to manage my network profiles right now.

---

### Post by psycosmyth on 2006-08-19
it's no longer in the archives.

---

### Post by LKRaider on 2006-08-19
What are you talking about? Sure it is: [http://packages.ubuntu.com/dapper/x11/xfce4-wavelan-plugin](http://packages.ubuntu.com/dapper/x11/xfce4-wavelan-plugin)

Did you enable the Universe repository there? :?

---

### Post by psycosmyth on 2006-08-19
dogh!
I got it but it does'nt show up. The space for it does. I'm missing a lib file???

---

### Post by psycosmyth on 2006-08-19
it shows but doesnt detect the card? weird. all libraries are up, :confused:

---

### Post by LKRaider on 2006-08-19
How so? Do you have the icon showing there at least? (see my attachment below)


If not, when adding it to the panel, did you select the autohide option? (don't!)
Did you select the correct interface for your wireless card?

---

### Post by psycosmyth on 2006-08-20
i deselected the auto hide, the icon is there. no report on activity.
thank you for helping me btw:o
I at least still have the LEDs on my card to tell me if I have a link.
I'm a classic War-bum;)

---

### Post by LKRaider on 2006-08-20
Maybe the driver for your card doesn't support reporting the link quality.

I have a Lucent Orinoco Silver card here, and I don't get any signal info from the driver. Granted, I am using the card in ad_hoc mode but even using the iwspy utility and setting the other card's MAC there, nothing is reported :\

Too bad the wifi drivers for linux are still incomplete. I wish the companies would disclose/opensource their hardware information/drivers (or at least for their old cards...)

---

### Post by psycosmyth on 2007-01-07
In case this was searched out


just use wireless assistant
you have to install some KDE base libs but het it works for me:rolleyes:

---


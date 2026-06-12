---
title: "Just installed Ubuntu 9.10, can't edit wireless"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by HelloPossum on 2010-03-23
I'm trying to edit my wireless connection.  I entered my SSID and the MAC address but the "Apply" button isn't active.  When I take out the MAC address, the button becomes active but nothing happens when I click it.  I just installed Ubuntu 9.10 on my laptop today.  I'm on my old desktop now because I can't get online with the laptop.  I've never used anything but Windows before.  I called RoadRunner but they only deal with Windows/Mac.  Can anyone help?

---

### Post by wojox on 2010-03-23
Probably needs a driver. Open your terminal and post back:

```
lspci | grep -i net
```

---

### Post by zeroseven0183 on 2010-03-23
How did you enter the MAC address? It should be in the 11:22:33:44:55 format and not 11-22-33-44-55 as the tooltip says.

By the way, the command above will look for the manufacturer of your network controller.

---

### Post by abbaazaabba on 2010-03-23
what type of notebook are you using?

---

### Post by the_jermz on 2010-03-23
Are you showing wireless networks when you click the icon on the top bar?  If not you need to find out what wireless card you have and install the driver.  I loaded my drivers right from the livecd.  Just go into synaptic package manager, select cd as a source, reload, and look for your driver.  Hope this helps, I'm still new myself... but had this same problem when I first installed.  Good luck!

---


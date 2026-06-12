---
title: "can't find network manager!"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by brimorse on 2010-08-08
Ok- I recently had to redo my wireless router and lost the wireless settings in ubuntu.  Tried to open network manager to detect the new wireless router, and network manager is nowhere to be found!  The top right of my screen has an icon for connection manager but it won't show available networks.  Went through package manager to make sure it is installed, which it was, but reinstalled it anyway.

Any idea how I can find network manager to open it?  

Thanks!

Bri

---

### Post by cariboo on 2010-08-08
Have you right-clicked on the NM icon and disabled and then enabled wireless networking?

---

### Post by brimorse on 2010-08-23
Yes, I did try that.  After I do that I still don't see any wireless networks to connect to.

Btw, I know the network works because if I log into Windows it works fine.

So is there another way to detect and connect to a wireless network in Ubuntu?

Thanks again.

---

### Post by gandaran on 2010-08-23
> **brimorse said:**
> Yes, I did try that.  After I do that I still don't see any wireless networks to connect to.

Btw, I know the network works because if I log into Windows it works fine.

So is there another way to detect and connect to a wireless network in Ubuntu?

Thanks again.

can you right click the network manager icon in the panel, choose edit network, go to the wireless tab and edit the old connection or just remove it and add a new one? all you need to fill in is the SSID and password!
it should connect then if all is well with the wireless card drivers,

---

### Post by brimorse on 2010-08-24
Thanks gandaran- I am trying that right now.  Just to clarify too- the SSID is simply the name of the network device, is it not?

---

### Post by Flimm on 2010-08-24
> **brimorse said:**
> Just to clarify too- the SSID is simply the name of the network device, is it not?
That's what it tends to be by default, but it could be anything.

---

### Post by brimorse on 2010-08-24
Eureka!

I knew it had to be something simple.  The advice I received was entirely accurate as far as setting up the connection.

However, I happened to check under System- Administration- Network Tools and sent a ping to the IP address, which it readily did.  So I changed the network device to wireless, closed the window and it worked!  Dumb luck I reckon...

Thank you again to all those posted!

Brian

---

### Post by kroq-gar78 on 2010-08-24
good. maybe you should mark this as solved so more people don't stumble by here (sorry if that was a little harsh-sounding)

---

### Post by brimorse on 2010-08-25
thank u for the reminder, my bad!

---

### Post by TheMadGeneral on 2010-08-30
> **gandaran said:**
> can you right click the network manager icon in the panel, choose edit network, go to the wireless tab and edit the old connection or just remove it and add a new one? all you need to fill in is the SSID and password!
it should connect then if all is well with the wireless card drivers,

I have spent days and days and countless hours trying to get my network card to connect to the router and you have just provided the solution to me.  My problem was that I was trying to connect through the settings on the wired tab (I know don't say it).  I thought that because I was using a network cable to the router that it had to be the wired tab.  I should have tried the Wireless tab.  Many many thanks.

---


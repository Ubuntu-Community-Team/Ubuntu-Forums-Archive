---
title: "How to take NetworkManager Applet away from panel"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by pzico on 2010-09-14
Good morning. NetworkManager Applet is showing the animation "searching for networks", however I have no problem in my connections. That animation is starting to be very annoying. How can I remove that applet from Gnome Panel?

I don't want to uninstall it, just remove from panel.

---

### Post by cjv8888 on 2010-09-14
> **pzico said:**
> Good morning. NetworkManager Applet is showing the animation "searching for networks", however I have no problem in my connections. That animation is starting to be very annoying. How can I remove that applet from Gnome Panel?

I don't want to uninstall it, just remove from panel.

Right click on the icon at the panel then click remove from panel.

---

### Post by pzico on 2010-09-14
When I right click it, I have following options:

- Enable networking
- Enable mobile broadband
- Enable notifications
- Connection information
- Edit connections
- About

All other things in panel seem to have option for removal, but not this. :confused:

---

### Post by coffeecat on 2010-09-14
You need to remove the notification area, which is the three little horizontal lines to the left. **But don't do this.** You may have problems connecting to anything if you do, and you won't be able to configure your network if you need to.

Far better is to fix the problem. How are you connecting? Ethernet or wireless, or something else? If ethernet, is there an active wireless nic? If you present network manager with two NICs, it will happily make two connections. Perhaps you're connected with one and it's trying to connect with the other. You might need to disable one in NM.

Post back with details and someone will tell you how.

---


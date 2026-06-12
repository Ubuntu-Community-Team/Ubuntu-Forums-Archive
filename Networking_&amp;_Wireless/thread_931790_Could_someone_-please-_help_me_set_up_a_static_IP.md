---
title: "Could someone -please- help me set up a static IP?"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by EvilDaemon on 2008-09-27
Can someone help me set up a static IP? I need to enable port forwarding so I can ssh in and out of my computer, and I need a static IP for that. I know how to do the port forwarding on my router, so can anyone help with the IP?

Thanks ahead of time.

---

### Post by sredhar on 2008-09-27
Hello -

Are you trying to use the computer from outside and not just your home network? If so you need to do port forwarding at your router.

Also, to set up static IP you need to edit the /etc/network/interfaces file. Please check the following link.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by caljohnsmith on 2008-09-27
So are you using ethernet or wireless? How about opening System > Admin > Network, press "unlock", type password, click on your interface, press "properties", and under "connection settings" and "configuration", you should be able to set up a static IP. Have you tried this yet? If not, give it a go and let me know how it goes.

---

### Post by EvilDaemon on 2008-09-28
> **sredhar said:**
> Hello -

Are you trying to use the computer from outside and not just your home network? If so you need to do port forwarding at your router.

Also, to set up static IP you need to edit the /etc/network/interfaces file. Please check the following link.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Thanks, I'll try that. It's wired now, but hopefully will be wireless in the future.

> **caljohnsmith said:**
> So are you using ethernet or wireless? How about opening System > Admin > Network, press "unlock", type password, click on your interface, press "properties", and under "connection settings" and "configuration", you should be able to set up a static IP. Have you tried this yet? If not, give it a go and let me know how it goes.

This won't work, as in Intrepid Alpha 6, there isn't a network option.

---

### Post by Iowan on 2008-09-29
If you're running Intrepid, you may find better support in the Development and Programming Forum.

---

### Post by mdurham on 2008-09-30
> **EvilDaemon said:**
> Thanks, I'll try that. It's wired now, but hopefully will be wireless in the future.

This won't work, as in Intrepid Alpha 6, there isn't a network option.

It might work by right-clicking the network applet and selecting "Edit connections..."
Seems to work okay for me.

---


---
title: "Can I configure networkmanager applet to prefer LAN over WIFI connections?"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by holr on 2007-10-10
Hi,
   I am using a fixed IP address on my LAN connection (editing /etc/network/interfaces by hand, as the GUI tool doesn't work well for me), at a site where I also have wireless internet setup also. My problem, rather, niggle, is that, when I boot up the computer with the LAN plugged in,  the gnome networkmanager applet prefers to connect to the WIFI even though the LAN is inserted! I have to right click the applet, and uncheck the "wireless" option (leaving "networking" enabled though) to get the computer to use the LAN.

   I know that under linux, most things are configured using user-editable txt files, is there a configuration file somewhere for networkmanager applet that I can set a preference to use LAN over WIFI if both exist in a location?

Thanks!

---

### Post by bvanaerde on 2007-10-10
That's really weird.
At my laptop, it choses it correctly: it only tries to connect to wireless connections when there's no network cable inserted.

---

### Post by holr on 2007-10-12
> **bvanaerde said:**
> That's really weird.
At my laptop, it choses it correctly: it only tries to connect to wireless connections when there's no network cable inserted.

Do you have a static IP configured for the lan, or dhcp?

---

### Post by bvanaerde on 2007-10-12
I don't use a static IP for my laptop... not sure if this matters though.
edit: This page might have interesting information about [Network Manager - preferred networks]("https://answers.launchpad.net/ubuntu/+question/12327"). I don't have the time to read it now, but it seems to me it might be what you're looking for.

---


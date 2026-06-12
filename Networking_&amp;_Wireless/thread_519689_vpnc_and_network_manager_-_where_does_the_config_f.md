---
title: "vpnc and network manager - where does the config file live?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by greavette on 2007-08-07
Hello,

I'm creating a Live CD (using UCK first and then  reconstructor - awesome tools!) so that I may remote into my work from the CD.  I've successfully installed vpnc and network manager and using a usb key, I can import my vpnc config file so that I can connect.  My next step is to build the Live CD with my config file already available in the correct folder..the problem is that I can't seem to figure out which folder my config file lives in?  I've searched my system folders to no avail and I've searched these forums but cannot find anyone else looking for this information.

I've created a config file and saved it to /etc/vpnc/myvpn.conf so that I may use the terminal to connect my vpn but it didn't look to me like network-manager uses this path for it's config file?

Does anyone know where I can save my config file so that when I start the Live CD, network-manager-vpnc already sees the config file?

Thanks,

greavette.

---

### Post by iver2435 on 2007-08-07
I have a vpnc setup on my laptop, unfortunately, it's at home in it's case.  If you don't get an answer soon, I'll fire it up when I get home and post it's location.

---

### Post by greavette on 2007-08-07
Hello iver2435,

Thanks very much!  Like I said I did a search, but then I am quite new to Ubuntu and may not have searched properly.

Thanks,

greavette.

---

### Post by Unconscious on 2007-08-13
Your default connection information should be in /etc/vpnc/default.conf. However, it's only readable by root so you need to use sudo to see it.

---

### Post by GrammatonCleric on 2007-08-14
I'm running feisty with network manager and vpnc.... and the networkmanager vpnc config file is not located in the /etc/vpnc directory.  I too would like to where NetworkManager keeps it.  Oh, it's not in /etc/NetworkManager either....

-GC

---

### Post by glhewett on 2008-02-08
This may be a little late, but I wanted to tie a box on this thread.  The configuration for the VPN is located in gconf.  The path is system/networking/vpn_connections/

---


---
title: "Total NOOB needs help with WPA2!"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by spentc on 2007-02-20
Hey guys, 

I'm new to ubuntu, know a little of Linux but not enough to help me here I am afraid!!  My wireless adapter is an ar5005g, and can connect to a neighbors unsecured network just fine, however our network uses WPA2, and I can't get online.  I can figure out the connection quality, etc, however it tells me the connection is dissconnected, I don't get it, can anyone help?

---

### Post by gradedcheese on 2007-02-21
The easiest way to use WPA is probably to switch to Network Manager.  There are how-to guides about this, but basically you install the packages:

```

sudo apt-get install network-manager network-manager-gnome

```

(if you haven't used apt-get yet, run "sudo apt-get update" first) and then once that's installed, you need to remove your wireless interface from /etc/network/interfaces -- this is done by editing the file and placing a '#' in front of lines that have to do with your wireless interface:

```

sudo gedit /etc/network/interfaces

```

save the changes, restart networking ("sudo /etc/init.d/networking restart") and then log out of Gnome and log back in.  There should now be a Network Manager applet running, you can use that to connect to your WPA-secured network.  

Check for how-to guides in case I missed something though...

---

### Post by tokyo on 2007-02-21
if you have the link for the guide, that'd help me out a lot.

---

### Post by gradedcheese on 2007-02-21
here's one:
[http://www.ubuntuforums.org/showthread.php?t=341357](http://www.ubuntuforums.org/showthread.php?t=341357)

---

### Post by strmchaxsr on 2007-02-24
Thanks this helped me too. I am new and trying both Kbuntu and ubuntu. I found the WPA2 stuff for network manager there right away was real easy to setup, now in ubuntu i had to find these steps first and wpa2 works great

Chris

---


---
title: "Fresh install: no wifi or network manager??"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by qix on 2007-05-26
Hi

I'm rather frustrated atm. This is such a simple thing (at least i'd think it is), and it just doesnt work. This is exactly what bothers me most at Ubuntu, although I completely skipped windows recently. Besides these annoying things, I love Ubuntu.

Oh well, to the point: I've had Ubuntu and Kubuntu on my laptop (Thinkad x60s). They both worked with Gnome-NetworkManager and KNetworkManager and my wifi (intel 3945 chip) was working flawlessly with WAP etc.

Now I did a clean install of Xubuntu (I have Ubuntu on my main computer, and want to try out xfce), and there is simply no networkmanager installed. I want to get my wifi to work, so I hook my laptop up on a LAN cable, and go to synaptic and install NetworkManager.
However it still doesn't come up, and then I remember that I need to install a frontend for it. So I load up synaptic againd and find NetworkManager-gnome and install that. I reboot again, and there are still no networkmanager - neither in systray or in the applications-menu.
I then load up the normal add/remove app, and find NetworkManager, which is installed it says. Then I remove it and install it again, and in the end it pops up and tells me that I can launch the NetworkManager from "Applications --> Internet --> NetworkManager". Oh yes I think, and I quickly press the Applications menu to find it. However there are no "Internet" menu in applications. There are Network however, but in that menu I only find Firefox, Gaim and Thunderbird (which are lovely apps for sure, but right now I want NetworkManager).

So this is where I am now. Having installed NetworkManager and NetworkManager-gnome twice, but still dont having any systray app so I can configure the network.

What to do? Can I launch it from a commandline? What is the name of the app? NetworkManager doesn't launch the systray.

I'm a complete newbie here on this thing, so I probably just need to do some simple thing, but I don't know what it is.

It frustrates me that such simple stuff like this just doesn't work out of the box. However, I'm not gonna leave for any other OS in the near future, I still like Ubuntu and it's derivatives too much :>

I hope for some help. Thanks in advance!

---

### Post by qix on 2007-05-26
Bump bump.. shouldn't be that hard to answer? My questions sums up to:
How do I start NetworkManager gui in Xubuntu? Command?

---

### Post by ugm6hr on 2007-05-26
In Terminal:

nm-applet

Done.

If you have multiple icons - look here:

[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

---

### Post by qix on 2007-05-26
Thanks. It works now...!

---

### Post by VirtualEntity on 2007-05-27
> **ugm6hr said:**
> In Terminal:

nm-applet

Done.

If you have multiple icons - look here:

[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)


Suppose you're running WindowMaker or some other non-KDE or GNOME-based windowmanager?  I cannot seem to get nm-applet to start at all--all I get is 

(nm-applet:11405): Gtk-CRITICAL **: gtk_tooltips_set_tip: assertion `widget != NULL' failed

(nm-applet:11405): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `GTK_IS_IMAGE (image)' failed

(mysql-query-browser:9903): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed


and nothing further happens at all...

---


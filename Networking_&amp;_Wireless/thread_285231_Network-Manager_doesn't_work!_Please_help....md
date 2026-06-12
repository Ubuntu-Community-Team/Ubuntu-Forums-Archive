---
title: "Network-Manager doesn't work! Please help..."
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by billis on 2006-10-26
Hello too all!

I've installed today the new Edgy final.
Worked everything fine so far I think, except of my WLAN.
I got an Intel 3945ABG WLAN adapter and want to use WPA2.
So I've installed the Network-Manager-Gnome with Synaptic-PM.
Now, when the Network-Manager is starting, i get this error Message:

(nm-applet:5134): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

So, can somebody help me, how to fix this? Or maybe how I get my WPA2 to work?

Thank you!

bill

---

### Post by Antman on 2006-10-26
See this thread: [http://www.ubuntuforums.org/showthread.php?t=285139]("http://www.ubuntuforums.org/showthread.php?t=285139")

---

### Post by billis on 2006-10-26
First of all, thank you!
I did the things posted in the mentioned thread, but there is no change. I still get the rror message

> (nm-applet:5134): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

:( :(

---

### Post by RomanW on 2006-10-26
I'm experiencing similar problems. I also followed the instructions in the thread that was mentioned before. This is the exact error message I get:

> (nm-applet:14270): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

According to rwconfig I have a R2500 Wireless Card. It's built in in a EasyNote Packard Bell R3400.

---

### Post by hugmenot on 2006-10-27
There&#8217;s an icon missing. After I placed the correct icon into /usr/share/icons/hicolor/22x22/apps it worked.

Someone file a bug please. No time.

---

### Post by pirast on 2006-10-27
whats the name of the icon missing?

---

### Post by hugmenot on 2006-10-27
> **pirast said:**
> whats the name of the icon missing?

nm-vpn-lock.png (at least). I just copied the whole nm-* series from another machine.

---

### Post by pirast on 2006-10-27
thanks,

running gtk-update-icon-cache -f /usr/share/icons/hicolor/ also fixes the problem..


i reopened the dapper report here: [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37128](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37128)

---

### Post by billis on 2006-10-27
You are my heroes :mrgreen: ! Thank you!!
I just installed the network-manager-dev packet, too, and hoped that the icon is in there. Everything is working fine now...WLAN up-and-running!

Greets,
bill

---


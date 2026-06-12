---
title: "I cannot connect to some wireless networks"
date: 2014-12-19
forum: Networking &amp; Wireless
---

### Post by alphhan on 2014-12-19
Hello,


I've installed Xubuntu on my netbook about a week ago. Since then, I managed to connect to the internet over my home router, over my IPhone's personal hotspot, and to my university network. Yesterday I tried to connect to Wi-Fi at work, but no success. My first problem was, not being able to find the little Wi-Fi icon on the taskbar. I managed to solve it, by following instructions I found online, though I'm not quite sure what function what I have done had. I've done the following:


1. I opened /etc/NetworkManager/nm-system-settings.conf. It was empty. I wrote managed = true and saved it. Then I rebooted. That didn't bring the icon back. So I reverted this change.


2. I changed the line "Exec: nm-applet" to "Exec: dbus-launch nm-applet" in /etc/xdg/autostart/nm-applet.desktop
also the line
That file contains the stuff between @'s, without the @'s.


@[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=dbus-launch nm-applet
Terminal=true
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-UsesNotifications=true
AutostartCondition=GNOME3 unless-session gnome
X-Ubuntu-Gettext-Domain=nm-applet
@


And in between these, some command line meddling, mostly harmless stuff like "man NetworkManager".


As I'm composing this post, I am connected via my personal hotspot. I couldn't connect to my university network. But maybe that's just the signal strength. The real problem is, no matter how powerful the signal, I couldn't connect to work network.


"lsb_release -a" gives:


No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


Also, I get the following output on terminal after I reboot and my desktop loads:

nm-applet-Message: using fallback from indicator to GtkStatusIcon



And then, when I do stuff with my WiFi, I get stuff like:

(nm-applet:2002): GLib-CRITICAL **: Source ID 131 was not found when attempting to remove it


(nm-applet:2002): GLib-CRITICAL **: g_hash_table_iter_next: assertion 'ri->version == ri->hash_table->version' failed


(nm-applet:2002): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed






"Stuff like" is rather ambigious, I apologize. However, I am new to this. I also managed to get (nm-applet:1704) as well, though I don't know what that means.

I never had any problems with WiFi when I was on WinXP. So I am pretty sure it is not hardware related. Besides, I don't have any problems connecting to my personal hotspot. (side note: I realized how much WinXP sucked after a week of Xubuntu)

As a last comment, I downloaded a cacert.der file. It was some certificate required to connect to my uni network. I followed the instructions on the uni webpage, but I might have messed something up, I don't know.

Thank you all

---

### Post by slickymaster on 2014-12-19
*Moved to the ***Networking & Wireless*** sub-forum*

---


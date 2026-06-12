---
title: "no nm-applet"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by jworr on 2008-11-10
When I try to run nm-applet I get the following error:

** (nm-applet:6791): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWireless' / 'ssid' invalid: 2



After looking around online, it appears that this bug was supposedly solved by an update, however it is still an issue for me.  Does anyone have any idea how to fix this?


the link to the bug report I found:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/288528](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/288528)

---

### Post by TenPlus1 on 2008-11-10
I had to disable network manager in sessions, reboot and load nm-applet manually in terminal to get it running...

---

### Post by jworr on 2008-11-12
I followed your advice but now I get the following error:

** (nm-applet:6654): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6654): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by jworr on 2008-11-12
Also, the option to add the network manager applet to my gnome panel is no longer available.  How do I fix this?

---

### Post by izm81 on 2008-11-12
For me, it seemed like network-manager or nm-applet didn't like something in my interfaces file.  What worked for me:

[LIST=1]
[*]install network-manager and network-manager-gnome
[*]copy your /etc/network/interfaces to /etc/network/interfaces.old
[*]copy just the ```
auto lo
iface lo inet loopback
``` lines to a new, fresh /etc/network/interfaces file.
[*]Restart the computer
[/LIST]

If it works, you can fill in the details of your interfaces using the nm-applet.  If not, you can uninstall NM and revert to your old interfaces file.  :)

---

### Post by jworr on 2008-11-12
Thanks, that did the trick

---


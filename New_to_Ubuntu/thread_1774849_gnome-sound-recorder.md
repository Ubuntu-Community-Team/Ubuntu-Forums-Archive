---
title: "gnome-sound-recorder"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-06-03
mm@xxxxxxxx:~$ sudo gnome-sound-recorder
Home directory /home/mm not ours.
Home directory /home/mm not ours.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Home directory /home/mm not ours.

I am having problems getting my gnome-sound-recorder to work so I though I would open it in a terminal and see what happened.

That was on the second profile on this machine.

The first profile without the sudo gives the following message.

(gnome-sound-recorder:16004): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed

Can somebody please suggest how I can over come these problems.

Thanks in advance.

---

### Post by Wobblybob on 2011-06-06
I had this problem a few das ago on Mint and tried all sorts of fixes but the one that worked was to remove the package completely and install again.

---


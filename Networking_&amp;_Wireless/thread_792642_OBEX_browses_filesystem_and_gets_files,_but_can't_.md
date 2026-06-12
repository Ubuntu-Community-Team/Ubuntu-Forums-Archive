---
title: "OBEX browses filesystem and gets files, but can't send"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Reactor5 on 2008-05-13
The title pretty much describes my trouble, but here are the specifics:

Lenovo/IBM T61 built-in bluetooth adapter running 8.10, sony w580i phone.  Bluetooth works for other things (like mice) but hasn't been tested with OBEX under Ubuntu.

If I try to drag and drop a file, it gives me the error below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69851&stc=1&d=1210667289[/IMG]

If I try and use the send to context menu item, it says connecting eternally and never transfers.  I've looked at all sorts of things this evening on the forums to no avail.  Curiously enough, the phone will function as an input device (it has a remote control feature) so it looks like OBEX object push is the only thing that doesn't work right.  Anyone care to take a guess at what's wrong here?

---

### Post by Kevbert on 2008-05-13
There have been problems with Obex for a while now (if you look at launchpad you'll see quite a few bugs).  Probably the best software for this is blueman ([http://blueman.tuxfamily.org/]("http://blueman.tuxfamily.org/")). You'll also need the gnome-bluetooth package via synaptic (if you haven't already got it).  Drag and drop should now work.
To receive an item on the phone you may need to set the phone up to receive a file (via it's menus).
Hope this helps.

---


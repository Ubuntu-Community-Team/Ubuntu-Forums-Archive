---
title: "WPA works but WPA2 doesn't"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Endolith on 2008-06-22
I just upgraded my router to DD-WRT v24, and I can't get my Ubuntu laptop to connect to it with WPA2 with nm-applet.  It works fine with WPA, but WPA2 doesn't ever get past the swirling connection icon.  It asks me for the key, I give it the key, it swirls around a while, then asks for the key again.

---

### Post by hexanol on 2008-06-22
Are you sure you entered the correct key ? :p I'm also using WPA2 on my network and never had any problem with connecting to it (with nm-applet). So I can't help you more than that (I'm using Hardy).

---

### Post by Endolith on 2008-06-22
> **hexanol said:**
> Are you sure you entered the correct key ? :p I'm also using WPA2 on my network and never had any problem with connecting to it (with nm-applet). So I can't help you more than that (I'm using Hardy).

Yeah I used the same key for both.

---

### Post by kevdog on 2008-06-22
Are you sure your driver to your wireless card supports wpa2?  An easy way to check would be to reboot your computer and then take a look at dmesg

dmesg | more

Look for something regarding your wireless device or interface name (such as wlan0).  It should list the modes its capable of supporting.  Another way to do this without rebooting would be to remove and then reinsert the kernel module (ie driver) for your driver -- the catch with this is that you need to know the name of the kernel module.

---

### Post by Endolith on 2008-06-22
> **kevdog said:**
> Are you sure your driver to your wireless card supports wpa2?

It worked completely fine until I upgraded my router and changed the key.  The only things that have changed are:

[LIST]
[*]Router version changed from DD-WRT v23 to v24
[*]Key changed
[/LIST]

Yesterday it worked just fine with WPA2.

---

### Post by Endolith on 2008-06-22
Something fixed it.  I had rebooted a few times with no luck, bt this time it worked.  I don't know why.

---


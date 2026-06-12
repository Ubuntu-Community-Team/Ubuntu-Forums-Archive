---
title: "NetworkManager doesn't show wireless networks"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by budhe888 on 2007-05-11
I apologize if this question has already been answered somewhere, but I
couldn't find it after a lot of searching.

I have an hp nc8430, with an Intel 3495ABG wireless adapter.  The
wireless connection works just fine using the built in network tools.
However, I wanted to use NetworkManager, since it is a much
better interface for changing wireless networks quickly (and WPA
support).  I installed it using:

```
sudo apt-get install network-manager-gnome
```

but the icon for the applet only shows a greyed out 'Wired Network', and
it doesn't even show an option for any wireless networks... even though
I am connected to one through the standard network manager.

I am running Edgy... anyone have any thoughts?

Thanks.

---

### Post by budhe888 on 2007-05-11
Problem solved!

After following what Praill suggested on this post:

[http://ubuntuforums.org/showthread.php?t=413071&page=3](http://ubuntuforums.org/showthread.php?t=413071&page=3)

it works now.  I also renamed the connection to wlan0 from eth1, but I don't think that matters...

---


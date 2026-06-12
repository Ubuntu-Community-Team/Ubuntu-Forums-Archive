---
title: "WiFi occasionally fails to start at boot/login for 16.04"
date: 2016-05-11
forum: Networking &amp; Wireless
---

### Post by vishalrao on 2016-05-11
Hello,

Has anyone else noticed with 16.04 (various flavours/distros, including Ubuntu, Neon, Kubuntu, elementaryOS) sometimes the wifi (network manager applets in UI) fails to get detected/enabled but then running "sudo systemctl restart network-manager" in a terminal fixes it?

This is happening to me on both my PC with Atheros wifi pci card and laptop with intel wifi card with various distros/desktops like KDE, elementaryOS etc. so it looks like a kernel/systemd issue.

I'm not sure what log outputs to post here, because it only occasionally happens, and when it happens I look at the dmesg output and note that the wifi modules seem to load and detect the hardware properly.

Thanks!

---

### Post by jeremy31 on 2016-05-11
Network Manager bug from Gnome and it has been fixed.  Everyone just waiting on the fix to show in the normal Ubuntu repositories after verification

Seems the issue involves the renaming from wlan0 to whatever iwconfig shows

---

### Post by kurt18947 on 2016-05-11
> **jeremy31 said:**
> Network Manager bug from Gnome and it has been fixed.  Everyone just waiting on the fix to show in the normal Ubuntu repositories after verification

Seems the issue involves the renaming from wlan0 to whatever iwconfig shows

That's good news. I see that problem periodically though not as frequently as earlier in 16.04's development.

```
sudo service network-manager restart
```

fixes it for me.

---

### Post by vishalrao on 2016-05-12
@jeremy31 can you link to the fix checkin location? i'd be interested to see what they fixed and where...

---

### Post by jeremy31 on 2016-05-12
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576726](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576726)

The upstream bug report at Gnome [https://bugzilla.gnome.org/show_bug.cgi?id=764803](https://bugzilla.gnome.org/show_bug.cgi?id=764803)

---


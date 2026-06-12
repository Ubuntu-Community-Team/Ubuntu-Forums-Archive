---
title: "How to disable a wireless network?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-11
Hello,


Because my built in wireless card didn't work well, I attached a usb wifi dongle which connects like a charm. While I am connected through the usb-dongle, my built-in wireless card also tries to connect to the same wireless network and constantly asks for the wep-key (which is quite annoying).

Is there a way how I can disable the network from my built-in wifi card, but still automatically connect to it through the usb-dongle?

---

### Post by mbzn on 2010-05-11
It has something to do with 'ifdown' and then the network interface. read the man's for ifconfig and ifdown to be sure...

---

### Post by dearingj on 2010-05-11
> **mbzn said:**
> It has something to do with 'ifdown' and then the network interface. read the man's for ifconfig and ifdown to be sure...

@mbzn: Don't forget, people posting in Absolute Beginner Talk might not know how to read a man page :)

@kramer65: To read a man page, you open a terminal (Applications->Accessories->Terminal) and enter the 'man' command followed by whatever you're trying to look up. In this case, "man ifconfig" or "man ifdown". Press Q when you're done reading to exit man.

---

### Post by pastalavista on 2010-05-11
Many Notebooks also have a physical switch built in, either on the case or in the BIOS setup. Also you can right-click the Network-Manager icon in the panel and uncheck the box beside "Enable Wireless".. or you can select "Edit Connections" and under the Wireless tab delete all 'auto' connections except the one for your USB dongle if there is one.

edit: more options. If you have proprietary drivers for the built-in wireless card, disable them with the System>>Administration>>Hardware Divers tool. You can also blacklist it. To do that, post  the output from terminal (with the dongle attached) of the command```
sudo lshw -C network
```

---

### Post by kramer65 on 2010-05-11
He Guys,

I had indeed never heard of a "man page", and to be honest, that's a bit too much for me. I did some things with the command line, but only when very detailed instructions were given. I do prefer a GUI.

Unfortunately I am not on a notebook, so there is no physical wifi-switch. I do not want to uncheck "enable wireless" since I do want to use wireless, but just not through the built-in wifi card, but through the usb-wifi-dongle. I also had a look under "edit connections", but it only lists one connection. This connection is indeed the one I need to disable through the buil-in card, but it is the same network that I do want to connect to via the usb-dongle..  :/

---

### Post by pastalavista on 2010-05-11
> **kramer65 said:**
> He Guys,

I had indeed never heard of a "man page", and to be honest, that's a bit too much for me. I did some things with the command line, but only when very detailed instructions were given. I do prefer a GUI.

Unfortunately I am not on a notebook, so there is no physical wifi-switch. I do not want to uncheck "enable wireless" since I do want to use wireless, but just not through the built-in wifi card, but through the usb-wifi-dongle. I also had a look under "edit connections", but it only lists one connection. This connection is indeed the one I need to disable through the buil-in card, but it is the same network that I do want to connect to via the usb-dongle..  :/I believe (not totally sure) the USB dongle does the conversion from wireless back to wired and it might appear in another tab besides Wireless. it comes in on the USB bus (my Atheros notebook wireless uses the USB bus) so it shouldn't hurt to delete the one showing in the Wireless tab. But it couldn't hurt anything to try. You can always add it back easy enough.

---

### Post by iponeverything on 2010-05-11
If you add an entry to /etc/network/interface for the internal device -- Network manager will leave it alone.

Say its wlan0 for instance add something like this:

```

iface wlan0 inet dhcp

```

---

### Post by kramer65 on 2010-05-11
Ah, thanks for the tip. How would I find out if it is wlan0?

---

### Post by QLee on 2010-05-11
[QUOTE=kramer65]
Because my built in wireless card didn't work well, I attached a usb wifi dongle which connects like a charm. While I am connected through the usb-dongle, my built-in wireless card also tries to connect to the same wireless network and constantly asks for the wep-key (which is quite annoying).

Is there a way how I can disable the network from my built-in wifi card, but still automatically connect to it through the usb-dongle?[/QUOTE]

Well kramer, I almost didn't read your post because the subject made me think that someone was asking for help with some terrorist plot, asking how to bring a network down. Glad I was wrong about that.

The system BIOS probably has an option to disable the onboard wireless interface.

Another thing to try would be right click on the Network Manager icon and choose the wireless tab, select the connection and choose edit, untick connect automatically.

---

### Post by 3rdalbum on 2010-05-11
> **kramer65 said:**
> Ah, thanks for the tip. How would I find out if it is wlan0?

Use it to connect to something and then right-click Network Manager's applet and choose Connection Information. It will be shown alongside the Interface line.

---


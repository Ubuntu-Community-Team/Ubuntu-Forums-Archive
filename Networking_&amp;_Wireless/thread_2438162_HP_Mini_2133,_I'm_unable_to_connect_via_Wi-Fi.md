---
title: "HP Mini 2133, I'm unable to connect via Wi-Fi"
date: 2020-03-06
forum: Networking &amp; Wireless
---

### Post by yaveton on 2020-03-06
Hi. 

I'll start with saying I'm really. really. new to Linux, but I know about the terminal.

I went to the networking settings in the bottom right corner, and wanted to connect via wifi, but I didn't find anything, apart from "Edit connection".

The slider-button that enabled Wi-Fi is now orange, and no matter how many times I slide it, it won't turn blue.

I'm reinstalling Lubuntu as for now, as I think I didn't do everything right, but I'll see.

---

### Post by guiverc on 2020-03-06
You haven't said what release of Lubuntu.

The Lubuntu manual can be found at [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

The 'stable' release refers to 19.10 (the latest release of Lubuntu), as this manual started with 18.10 or the first release using the LXQt desktop, so if you're using the older Lubuntu 18.04 LTS with LXDE it won't match your system.

Some details relating to wifi can be found at [https://manual.lubuntu.me/stable/3/3.1/3.1.5/nm-tray.html](https://manual.lubuntu.me/stable/3/3.1/3.1.5/nm-tray.html) (assuming 19.10), a GTK GUI front-end has replaced it for 20.04 (still in development) as there a good Qt based GUI wrapper hasn't been found/developer yet.

I won't provide more, as it'll vary on release (you may not be using Lubuntu 19.10 for example).

If your problem relates to wifi card/chipset not recognized, the following will be more useful though [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

(*Sorry the blue/orange detail is probably useful, but I can't picture it as I'm used to seeing only white icons and not color; but your release is the first detail I need*)

---

### Post by pcfan1234 on 2020-03-07
Show the output of ```

lsb_release -a
uname -a
lspci -nnk
lsusb
ip a

```

---

### Post by yaveton on 2020-03-07
I'm sorry to all of you for lost time. All I had to do was update the lubuntu via ethernet, and install aditional driver. Have a good one!

---


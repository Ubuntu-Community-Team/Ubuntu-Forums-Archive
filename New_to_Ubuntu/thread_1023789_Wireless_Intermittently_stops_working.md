---
title: "Wireless Intermittently stops working"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by appi2012 on 2008-12-28
There is an odd, annoying problem with my computer. Every once in while, my wireless connection simply dies, and can't reconnect. I can still see the name of my network, but it keeps asking for the password, and even after giving it the password, it doesn't work. Luckily, I figured out how to fix this: just unplugging my usb network adapter (linksys WUSB54Gv2, working with ndiswrapper), and then plugging it back in. But I don't want to keep doing this time consuming process when I am actually doing something productive, but it happens quite often on gmail and google docs. Even so, I haven't found a pattern to these occurrences, and it doesn't happen to all windows and mac computers on the network. 

This isn't a critical problem, but it is quite annoying, and help would be greatly appreciated.

---

### Post by emecas on 2008-12-28
Hi.. I am not expert about your problem, but maybe that post can help you to get a diagnostic: [http://ubuntuforums.org/showthread.php?p=4097278&page=2](http://ubuntuforums.org/showthread.php?p=4097278&page=2)

---

### Post by Crooksey on 2008-12-28
I take it you are using the GUI netwrok interface to connect?

You could try making a script..

```

$ gedit netwrok_script

```

Now copy and paste this in (changing the peramaters)

This script assumes you have a wifi device in eth1 slot, just changed eth1 to youe device, to find the name of your wifi device

```

$ iwconfig
```

```

sudo iwconfig eth1 essid "yourEssid"
sudo iwconfig eth1 key YOUR-WEB/WPA-KEY-HERE
sudo dhclient eth1
```

Save the script, then make it executable..

```

$ chmod +x network_script
```

Then run it..

```

$ sudo ./network_script
```

That *could* sort it out, as the network manager has been known to cut out every now and again.

---

### Post by appi2012 on 2008-12-28
Can you explain to me what that script does?

---


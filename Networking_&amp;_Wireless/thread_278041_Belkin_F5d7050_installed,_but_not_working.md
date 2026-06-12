---
title: "Belkin F5d7050 installed, but not working"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by tophat_grendel on 2006-10-15
I have a Belkin F5D7050 v4000 wireless USB card. I installed ndiswrapper version 1.8 from my Ubuntu disk, and used the blkwgu.inf file as the driver. My computer says that both the driver and the hardware are present, and when I first installed the driver the little light started to blink and the card showed up in network tools, though it had a hexadecimal ip adress and wouldn't connect. After I rebooted, unplugged the card and plugged it back in, it didn't show up as a network connection.
If I type ndiswrapper -l, it still says that the hardware and driver are present, but the light has stopped blinking.
I have no other internet connection for the box, so any solutions have to be remote. Any ideas?

---

### Post by bithika_mookherjee on 2006-10-16
hi tophat_grendel

I've got exactly the same problem, ubuntu reports the driver present and the hardware present, but no network connection.
I'm pretty much a linux newbie, especially when it comes to network connections, but as far as I can tell the next step is to get wlan0 to be recognised when you do ifconfig.

I have read that adding the following lines to your /etc/network/interfaces file might work, but I already had these lines in there - so I'm not so sure that's my solution - it might work for you however.

```
auto wlan0
iface wlan0 inet dhcp
```

Let me know how you are getting on!

best wishes
Bithika

---

### Post by tophat_grendel on 2006-10-16
I got the card to show up under network tools list of connections by adding ndiswrapper as a module to start whenever the computer does.

```
sudo gedit /etc/modules
```

after the file pops up, just add ndiswrapper on a new line, save, and reboot.

Still can't figure out how to get the card communicating yet, but it's a step.

---

### Post by bithika_mookherjee on 2006-10-17
Hmmm. It looks like we have a similar set up - I've had ndiswrapper at the end of the file /etc/modules for a while now, and I have been assuming that ndiswrapper was being loaded on boot up. But now I'm not so sure.

Is there any way to verify that ndiswrapper is successfully loading at startup?  Or maybe somewhere ndiswrapper itself is failing to load the driver.

By the way, I have been checking for wlan0 via Admin->Networking and via "sudo ifconfig" at the command line. Did you say that you are looking at Admin->Network Tools - or did you mean "Admin->Networking"?

That's one place I haven't checked, I will when I get home tonight.

---

### Post by tophat_grendel on 2006-10-17
The clues I got that ndiswrapper is loading is that the light on my usb is blinking, and it shows up under connections when I go to Admin -> network tools

---


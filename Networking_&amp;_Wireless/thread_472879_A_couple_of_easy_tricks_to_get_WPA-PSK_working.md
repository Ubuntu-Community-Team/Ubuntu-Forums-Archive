---
title: "A couple of easy tricks to get WPA-PSK working"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Chris Williamson on 2007-06-13
I just spent the morning trying to get Feisty working with WPA-PSK (a.k.a. WPA Personal) enabled on my wireless router. For what it's worth, I finally did manage to do it, via the standard Network tool in the System menu, without having to edit any text configuration files or installing a different network management tool.

There were a couple of tricks I found.

One was to click on the network icon at top-right, and even though my network was already listed from earlier connection attempts, I needed to ignore it and choose **Connect to Other Wireless Network**, then enter my network name, choose **WPA Personal** and enter what my router calls a passphrase in the **Password** box.

After many fruitless attempts, the thing that finally seemed to get it working was to enable my router to broadcast the network ID (SSID). I found another post that suggested the network manager tool has an issue with WPA when the ID is not being broadcast.

Hope this helps someone save a few hours.

---

### Post by scrooge_74 on 2007-06-23
It took me a while to master also, sometimes I had to set the card in roaming, other times I have to make the password visible while I was typing.

But mostly I had to set the /etc/networks/interface file to put all cards in auto for it to work properly.

---


---
title: "No Network Connection"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by dg06042 on 2008-09-05
I loaded the latest Ubuntu code I downloaded Wednesday.  I can not connect to the internet.  I have a DSL wireless router/modem I am trying to connect to.  I have the Ethernet cord plugged in to try and get a wired connection.  I clicked on the network manager icon and see " No network devices have been found” Everything I have read looks like it should detect and automatically configure for a wired connection, but it is not.  There are lights on the modem/router side indicating a connection, but there are no lights on my laptop side.  To me it appears that the port/connection of the laptop must not be on.  I'm very naive and have never used anything other than windows before. Please help with any suggestions of what to do and please give step by step directions 5-yr-old could follow.

Thanks.

---

### Post by dudude on 2008-09-05
Try typing "ifconfig" into the terminal. If it shows eth0 or eth1 or something, then all you need to do is configure the settings to connect.

If nothing shows up, then it could be that Ubuntu does not have the driver for your network card.

You could also try using the Ubuntu live CD to see if the network card is working on there. If it is, then I do not know how to fix it, but it does mean that the card can work with Ubuntu.

---

### Post by dg06042 on 2008-09-06
Thanks dudue.  I got the internet to work with a USB wireless adapter.  It must be that the internal laptop network card is not recognized.  I was going to check and then load a driver.  I looked under help and found the following:

3.2.1.&#8195;Check for device recognition

   1. Open Device Manager (System &#9656; Preferences &#9656; Hardware Information).
   2. Check to see the hardware is recognized if it is then Section 3.2.2 &#8213; Check for driver
   3. If your device is not displayed then there may be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.

I can not find the Device Manager.  I don't seem to have Hardware Information located under System>Preferences>Hardware Information.

Does anyone no where to find the Device Manager? Or how to check what network card I have so I can find a driver.

Thanks

---

### Post by dudude on 2008-09-06
I think that help entry is a little old now because the Hardware Information/Device Manager screen was removed in Hardy (or was it Gutsy?)

But to find out information about your particular network card, try typing
```
lspci
```
and then
```
lspci -n
```

The output of the first command should give you the names of all of the devices inside the system.
The second command should output the PCI ID of all of the devices. 

For my network card, the two commands gave me...
```
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:19.0 0200: 8086:104b (rev 02)
```

The PCI ID of my card is shown to be 8086:104b. The network card should show up if it is detected by Windows.

For reference: [[IMG]http://img137.imageshack.us/img137/7699/screenshotrobertrobertdnr1.th.png[/IMG]](http://img137.imageshack.us/my.php?image=screenshotrobertrobertdnr1.png)

Try googling the PCI ID of the card to see if anyone else has had problems too.

For me, I would search for "8086:104b linux" in Google.

Good Luck

---


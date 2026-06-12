---
title: "Bluetooth Applet clear device list"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by metchebe on 2008-05-18
Hey

I would like to know if I can clear the device cache in the Bluetooth Applet > Browse Device list. There are mice and phones that I have connected to and no longer have, and I don't want them appearing on that list.

Thanks,
Marco

---

### Post by metchebe on 2008-05-31
I found a bug report related to this:

[Bluetooth (OBEX Push) should remove devices not in range]("https://bugs.launchpad.net/nautilus-sendto/+bug/138834")

Anyone find a workaround?

Thanks,
Marco

---

### Post by blagger on 2008-12-29
I had to remove devices manually. The gnome applet asks hcid daemon for known devices.

hcid database is on /var/lib/bluetooth/[YOUR-DONGLE-MAC-ADDRESS] . There are several text files for several purposes: remove the line matching the mac address of the old bluetooth device on each file and you're done.
I had to remove lines from the files sdp, manufacturers, features, classes, lastused, lastseen, names.
If you don't know what mac addresses to remove, the names file can help you because associates a mac address with a device name.
Remember: these files must be edited as root.

---

### Post by metchebe on 2008-12-29
Thanks! :)

---

### Post by HendyIrawan on 2011-03-20
> **blagger said:**
> I had to remove devices manually. The gnome applet asks hcid daemon for known devices.

hcid database is on /var/lib/bluetooth/[YOUR-DONGLE-MAC-ADDRESS] . There are several text files for several purposes: remove the line matching the mac address of the old bluetooth device on each file and you're done.
I had to remove lines from the files sdp, manufacturers, features, classes, lastused, lastseen, names.
If you don't know what mac addresses to remove, the names file can help you because associates a mac address with a device name.
Remember: these files must be edited as root.

OMG! Your post is GOLDEN!!!

Thanks!!!!!! :popcorn:

If you're here I'd buy you a burger rightaway

---

### Post by lifeluvr on 2012-05-28
There is another way that I found. Using this method will require a  fresh 'pairing' of all your devices but, it was fast and pretty easy to  do. First I opened a root terminal and used cd to mount the bluetooth directory
[COLOR=RoyalBlue]
 [COLOR=Black]$ [/COLOR]cd /var/lib/bluetooth[/COLOR]

Then I used the rm -rf +(MAC file located in /var/lib/bluetooth) command to delete the file..like this

$ [COLOR=RoyalBlue]rm -rf 00:12:AA:EE:01     [/COLOR][COLOR=Black]<---fake MAC address but, that's what the command looks like.[/COLOR]

Finally, I let the bluetooth device wizard rebuild the file for me. :guitar:
This was done using Ubuntu 12.04.

---


---
title: "Unable to recieve files from my N95 via bluetooth."
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by Marcboy on 2008-08-19
Im running ubuntu hardy on an eee pc and having some trouble with bluetooth. 
I can connect to my Nokia N95 and browse the files thought bluetooth on my laptop but i am unable to send a photo from my phone to my laptop. Every time i hit send it says "connecting" and the immediately says "sending failed". But nothing comes up on my laptop to say it even tried. 
All the bluez applications are installed, as is gnome-bluetooth and the device is set to visible and connectable. 

Anyone have any idea on how to solve this problem? Or what i might be missing?

---

### Post by ukblacknight on 2008-08-29
I'm having the same problem!  Any help would be greatly appreciated.

---

### Post by Sub101 on 2008-08-29
I have an N95 and it works. Have you paired the device?

---

### Post by solitaire on 2008-08-29
Same is happening with me too:

Sending FROM N95 to Ububtu 8:04 = Sending Fails
Sending FROM Ubuntu 8.04 to N95 = Sending Works

Phone is paired and set as trusted. 
Laptop Bluetooth options:
Receive files from remote devices = Ticked
Automatically authorise incoming requests = Ticked

---

### Post by Yathi on 2008-10-27
Same problem here but wid a different phone. Nokia 5700. Any suggestions??? I read somewhere something tat this bluetooth version in 8.04 is at fault n should rollback but i m new n dunno how to do a rollback of the bluetooth software.

---

### Post by solitaire on 2008-10-27
I got a solution workaround.

Install "Bluetooth File sharing" it's a separate App in the repos (gnome-obex-server 0.11.0).
Install that and start it, you should now be able to receive files sent from a bluetooth phone.

---


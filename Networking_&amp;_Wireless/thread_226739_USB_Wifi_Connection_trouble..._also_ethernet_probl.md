---
title: "USB Wifi Connection trouble... also ethernet problem"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by XA04 on 2006-07-31
OK, I decided to install Ubuntu on my laptop last night. Basically I have a wireless USB stick, it appears linux can find it, and can find my wireless station (brings the SSID up), I enter my passkey... and it doesn't seem to connect (I don't think... I can't access the network or internet anyway). I'm 100% sure I'm using the correct pass key.

Any ideas on what is wrong?


My other problem... decided to use the ethernet cable after I gave up with the wifi, it connects to the network fine - but it doesn't connect to the internet (whilst other computers on the network can).

Any ideas?



I'm a bit of a linux noob so any help is appreicated,
Thanks


PS: The new distro of Ubuntu looks really great, I love all the eye candy! - Hopefully will be able to move permanently to Linux on the laptop!

---

### Post by XA04 on 2006-08-01
bump

---

### Post by secunda007 on 2006-08-01
Firstly, what make is your wireless stick? I have had various problems getting a Belkin USB Wireless stick to work with Ubuntu - enabling the stick caused GNOME (the desktop) to crash. Try using the solutions below, to get your PC connected.

1a) Try putting spaces in the correct place in the passcode.
 b) Try using small + CAPS letters in the correct place.
 c) In the worst case, Ubuntu may not be natively compatible with your wireless stick. In this case, use Ndiswrapper to get the stick working - search the forums to help you do this. Ndiswrapper uses a Windows driver to get the device working - so you may need your original Wireless Stick driver on hand.

When connecting your PC to a wired network via ethernet:
2a) I had a similar problem - make sure that the ethernet card is deactivated + disabled in the network settings before connecting your PC to the network. Once the ethernet cable has been inserted into your PC's ethernet slot, enable + activate the ethernet card.
 b) Your router may be incompatible with IPv6. This is known to degrade network performance, so search the forums for a cure.

---

### Post by XA04 on 2006-08-01
Hi secunda007, thanks for replying.


The wireless stick is made by Safecom, and it uses the zd1211 chip.

I haven't managed to get this to work on any other Linux distros (all though drivers are available for it, I just haven't).

However, in Ubuntu, it is detected, and shows up if you type "ifconfig" in the terminal, and it shows up in the networking options.



1a) What do you mean try putting spaces in the correct places? (no spaces in the password I am using),
b) Still a bit confused... I'm definitely using the correct passkey.
c) Cool, will have a look at that

2a) Interesting, I will try that.
b) Will look into that.



Thanks for your help, will let you know how it goes! :)

---


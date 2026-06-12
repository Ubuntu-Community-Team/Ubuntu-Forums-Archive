---
title: "BT Home Hub"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by PriceChild on 2006-07-19
Hey there, just got the new home hub, and windows pcs all over the house are now sharing the net perfectly.

However... i can't get my ubuntu box on there :(

I've used the ESSID name, and the 64bit Hex passcode, but nothing will let me connect, whether I use gnome-network-manager or in administration>system>networking

Any Ideas?

---

### Post by jasil on 2006-07-19
If you use NetworkManager to manage your connections I believe you should comment out all the lines from /etc/network/interfaces except those referring to lo interface. After that you should be able to connect to your access point using the GUI from NetworkManager applet.

I'm using NetworkManager and it works very well. Now I event got rid of the annoying keyring application asking password every time I login (see thread [187874]("http://ubuntuforums.org/showthread.php?t=187874"))

---

### Post by PriceChild on 2006-07-19
Yeah, its always worked for me before to connect to other access points.

Not working with this one though :(

Anyone got any experience with the home hub?

---

### Post by PriceChild on 2006-07-19
Ok all sorted... just a matter of entering the settings in system>administration>networking, no need for gnome-network-manager.

Then rebooting.

All is good :)

---

### Post by eiffel on 2006-08-23
I've just recieved my BT Home Hub and tried installing it on my machine.

My machine dual boots Windows2k/Ubuntu and connects to the hub via and ethernet cable - the hub installed fine on windows.

I thought it would be just a case of copying some settings across.  Is that the case?  If so where are they in windows?  I can't seem to see them - everything looks like the defualt 'Use DHCP' and no IP addresses etc in the standard network settings properties bit.

Any ideas? (Much appreciated)

---

### Post by PriceChild on 2006-08-23
I didn't bother installing on windows... It will work by wired or wireless without their annoying software by just connecting the cables or entering the wireless passkey.

Under linux, the only annoyance i had was remembering to set the wireless passkey to hexidecimal.

---

### Post by eiffel on 2006-08-24
ahh yeah cheers

think the problem was that my machine had some settings from work - setting properties in the network admin to 'DHCP' did it :D

---

### Post by ahaslam on 2007-02-17
Has anyone successfully connected a usb printer to one of these?

Tony.

---

### Post by Lex-Man on 2008-06-15
Can you explain this in a little bit more detail I'm trying to connect to a BT Home Hub from my Ubuntu install but I can't seem to connect.

I have gone to the network setting and manually set up the information and my wireless dongle can see the router.  But on reset it doesn't seem to connect.

---

### Post by PriceChild on 2008-06-15
Don't do it manually... set things back to roaming, then use the network manager applet near the cloak.

---


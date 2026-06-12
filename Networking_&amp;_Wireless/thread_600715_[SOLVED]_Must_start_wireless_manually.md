---
title: "[SOLVED] Must start wireless manually"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by a__l__a__n on 2007-11-02
I'm migrating over from Sidux to Ubuntu 7.10 on a Thinkpad 600x with a D-Link Atheros-based wireless card.  Right after installing Ubuntu (on a blank hard drive),  I attempted to configure the card for my WPA network using the System->Administration->Network gui, but it was failing to remember the key that I entered.  So I edited /etc/network/interfaces and added the key there as it had been in my sidux configuration.  

Now, during boot, the wireless card appears to connect and then disconnect.  After logging in, I am not connected to the network.  I can start the network with

   /etc/init.d/networking restart

and everything works from that point forward.  But surely there is a better solution!  What am I doing wrong?

Thanks

---

### Post by jnorthr on 2007-11-02
could you please post a copy of 
**sudo cat /etc/network/interfaces **
file, there are several options using the **pre-up** keyword that might help

---

### Post by a__l__a__n on 2007-11-02
here's my /etc/network/interfaces (yes, that's the correct ssid):

auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid 1062651115
wpa-psk XXXXXXXXXXXXXXX
auto ath0

---

### Post by a__l__a__n on 2007-11-05
If anyone can help me solve this issue I would be most appreciative!

---

### Post by a__l__a__n on 2007-11-05
For the benefit of anyone who might search and find this thread, here is how I have resolved my problem.  I installed WICD according to these instructions:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

It wasn't an immediate solution however.  I had to go through a few cycles of running the gui:

sudo python /opt/wicd/gui.py

and configuring the connection, setting the WPA key and marking it to be automatically started on boot, and then rebooting.  I am not sure exactly which sequence of steps got that working but after going through that a few times it is now connecting during bootup and it seems to be reliable now.

The claim to fame for Ubuntu is that things "just work".  Obviously Ubuntu's wireless support does not currently deserve that reputation.  Anyway mine is working, and I am sticking with Ubuntu for now.  I anticipate that this will get plenty of attention and will be fixed by the next release.  Please...

---

### Post by rasmusbp on 2007-11-30
Thanks for that tip, alan. Worked perfectly for me, even in first shot. 

I had the exact same problem with network manager after swithcing from WEP (which worked out of the box in 7.10) to WPA-PSK. I had to restart the network manually after each reboot.

---


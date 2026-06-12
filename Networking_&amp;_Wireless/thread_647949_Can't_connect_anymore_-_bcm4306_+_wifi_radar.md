---
title: "Can't connect anymore - bcm4306 + wifi radar"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by NHansen on 2007-12-22
Ok, so I got my broadcom 4306 finally working with fwcutter and wifi radar (Gutsy). All has been fine, but now all of a sudden it can't acquire the ip address anymore. I'm connecting in winblows, so I know i can connect..
I'm pretty sure I read once or twice that bcm43xx wireless starts to diminish in it's capabilities of working in linux over time. But really, this makes no sense to me (and it's been like 2 days).
Is there some sort of fix? What can I try to do?
OI vey....
Thanks!

---

### Post by ubutufan on 2007-12-23
Edit the contents of the file interfaces
The file is in /etc/networks
Post the data here

---

### Post by NHansen on 2007-12-23
ok so it still connects, just rarely. The strength of the network seems fine, I just have to click "connect" about a million times and hope it connects...
anyway, here is the interfaces contents:

auto lo
iface lo inet loopback



iface eth1 inet dhcp
wireless-key s:518750b733
wireless-essid Newcom



auto eth1

---

### Post by ubutufan on 2007-12-23
Try the following in the interfaces file
--------------------------------------------
auto lo
iface lo inet loopback



#iface eth1 inet dhcp
#wireless-key s:518750b733
#wireless-essid Newcom



#auto eth1
---------------------------------------------
In reality you are commenting out any previous connection attempts, making a fresh-one when you try to reconnect.
Let us know the results

---

### Post by kevdog on 2007-12-23
Can you connect from the command line just to simply possible reasons why the connection is dropping?? Instructions are in my signature.

---

### Post by coldstatue on 2008-04-30
does that mean it;s solved?

No disrespect if I'm missing something, but isn't the excellent support in these forums worth a couple of clicks?


So what if my interfaces file only has

auto lo
iface lo inet loopback

I have been having a hard time with ndiswrapper for my atheros card. It will connect to some wireless networks, but not others. It just keeps wanting to connect to the last one it successfully connected to, even if i reboot in the new location. (All open networks) I've been booting into win when i can't connect, and it's no problem, so i installed wifi-radar. it will connect, but can't get an ip address.

This is mostly at hotels, where you only get local access until agreeing to something when you first open your browser, but i can't even get that. 

*sometimes* I get the ' could not get an ip address' message

thanks for your time.

---


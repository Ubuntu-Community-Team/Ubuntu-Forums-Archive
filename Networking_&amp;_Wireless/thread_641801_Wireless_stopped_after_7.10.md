---
title: "Wireless stopped after 7.10"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by iamah on 2007-12-15
Hi, I have used Ubuntu on an Acer notebook, but since I've installed 7.10 it doesn't find the network... windows still working so the problem is 7.10, but I'm not willing to downgrade my Ubuntu...

I noticed it has wifi0 an ath0 interfaces... but the upper right network icon doesn't list any wireless network... I tried adding manually with several options, but nooo success... 

I've just updated with wired connection but still the same problem... according to windows my chip is Atheros 5005G... seems to be problematic, but it worked just fine in previous Ubuntu release... now I upgrade to new Ubuntu and this happens, it gave me a bad impression about how things are going wiht my favorite distro... :(

---

### Post by almax00 on 2007-12-16
what is in your /etc/network/interfaces?  comment out everything except:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

---

### Post by iamah on 2007-12-16
there was only the first two lines... but I'll attach more information on commands I ran yesterday... if anyone can help, maybe its a more serious problem, because it used to work...

---

### Post by iamah on 2007-12-20
problem solved, indeed it was a problem with /etc/network/interfaces file... i've just added the wireless interfaces with auto option and rebooted

this thread is very good
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---


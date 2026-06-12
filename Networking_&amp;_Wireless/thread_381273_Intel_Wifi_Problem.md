---
title: "Intel Wifi Problem"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by canclan on 2007-03-10
Hello!
First, I would like to say that I love the support that Ubuntu has and the work that the community puts into helping those in need!  Also, I am very impressed with Ubuntu and its ease of use!  My only previous experience (minimal though it was) was with Mandrake and I ended up leaving it!

So now to my problem.  I have Edgy (dual boot with windoze) on a Dell C610 with a 2915abg mini-pci wireless card.  I have a Netgear FWAG114 router using WPA-PSK.  I am using the latest Network Manger, WPA Supplicant, and now even the Pam Keyring package.  After spending about 50 hours (!) on trying to get the dell to hookup to the router wirelessly (and learning a great deal about ubuntu/debian in the process!),  I have finally managed to hook up - but *only if* I go to terminal, and type:

```
sudo /etc/init.d/networking restart
```

and then

```
sudo /etc/init.d/dbus restart
```

in that order.  If I do not type that, I will end up connecting to a wireless router near my house which has no security at all.  Furthermore, before I type the above,  the only router I can see in the list is the open one.  After I type it, I see all the neighbourhood routers (including my own).  More info/outputs are available upon request.

My question is:  does anyone know what the heck is going on?

Thank you in advance for any and all assistance!

PS  Has anyone successfully gotten a 2915abg to hook up to a 802.11a network?  I can not find any documentation on it.

---

### Post by spd106 on 2007-03-10
Can't help with 802.11a network as I don't own any 5GHz band capable equipment.

Network Manager stores network information in gconf, so if you look in the .gconf/system/networking/wireless/networks/ directory and see the essid of any networks you don't want to connect to, then delete that directory.

You might want to read this faq [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

### Post by canclan on 2007-03-10
Thanks for the reply!  And thanks for the Network Manager  info website!  I will go through the gconf file when I get my laptop back (my wife is using it right now!).

I am not surprised that you don't have 11a equipment - there is definitely not much around about 802.11a!

Any idea why I have to restart networking and dbus every time to get it to see all the routers?

Thanks again!

---

### Post by hardyn on 2007-03-10
having the same trouble after a 6mo of working flawlessly... i think something got broken...
please visit:

[https://launchpad.net/bugs/90896](https://launchpad.net/bugs/90896)

if it sounds like the same problem, leave a note, and will see if we cant get this fixed.

---

### Post by canclan on 2007-03-10
Thanks for the heads up!  I just posted my bug there under yours.

---

### Post by canclan on 2007-03-15
So I deleted the directory in gconf as spd106 (and the website) recommended but it still is doing the same thing.  Any other ideas?  Anybody have any idea why restarting 'networking' and 'dbus' (usually) gets it to work?

---


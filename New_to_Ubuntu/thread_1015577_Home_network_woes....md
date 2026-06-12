---
title: "Home network woes..."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mikeserv on 2008-12-18
Boy, this is totally aggravating me.  Ok, so here goes.

I have an Ubuntu computer with no keyboard.  It is setup to accept desktop control (VNC) automatically, this is how I usually access it.  But I've just moved, and I'm on a neighbor's wireless network, so I can't access the machine.  All I need to do is 1) connect a keyboard to the machine (which I don't have) or 2) vnc into the machine JUST long enough to type in the vnc password or 3) (if anyone knows of this) I could use a soft keyboard on screen that I could click with a mouse (which I have, but I'd have to transfer the keyboard package with a USB stick and STILL need to enter the sudo password just to install it so I guess that is out)

Luckily, I have this laptop that IS connected to the network via wireless (nic ath0) AND a crossover cable.  Now I know that it is possible to setup internet connection sharing because I did it from the XP install on my laptop and was able to pull up a webpage on the keyboard-less ubuntu machine.  But I couldn't figure out the ip address that Windows XP assigned the Ubuntu machine so I couldn't VNC into it.

Basically, I need to VNC into my machine, and if that means setting up ICS from Ubuntu to Ubuntu I'll do it, but if anyone else knows the first IP address that XP assigns to its DHCP client machines through auto internet connection sharing that would be much easier.

Recap: Need to go Internet > Wifi Card (ath0) > laptop > Ethernet (either loopback0 (maybe l0?) or eth0 > crossover cable > eth0 > Keyboardless Ubuntu machine.  And I need to VNC from laptop to Ubuntu machine.

Confusing enough?  It's making me crazy.

-Mike

---

### Post by mikeserv on 2008-12-19
Oops...  Must have double posted.  So I deleted this message.  Read the one below.

---

### Post by mikeserv on 2008-12-19
Ok, so, as it turns out, Ubuntu comes with an onscreen keyboard in assistive technologies.  I just enabled it, punched in the wifi encryption passcode, looked up my new ip address on the other computer in the router's dhcp client list, and vnc'd in.

But this doesn't solve the fact that I am STILL going to have to set up a crossover cable internet connection sharing network between my keyboard-less Ubuntu computer and my XBMC hacked XBOX with the Ubuntu machine as the host.

Basically it will work like this:

   Wifi Router > Laptop
   Wifi Router > Keyboardless Ubuntu > XBMC XBOX

(The two wifi routers listed above are really just the same one, but I the forums kept pulling my whitespace out.)

But will the Xbox be able to share files with the Ubuntu machine?  Will it be able to share with the laptop?  I can always install an SSH service on the laptop and mount the laptop's drive on the Ubuntu machine to share with the XBox if I must, that is if the XBox will only be able to share within its local network between itself and the Ubuntu machine.  

Any clues anyone?

-Mike

---

### Post by Kellemora on 2008-12-19
Hi Mike

I'm responding to which IP number your machine might have.

ALL of the computers here are in the 192.168.1.101 upward range, because I let the default IP numbers be used.
My Router is NOT in that range of numbers!
If your's is, you may try 192.168.1.10 or 11 and upwards.

TTUL
Gary

---


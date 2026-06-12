---
title: "Overnight bluetooth keyboard/mouse dropout.  Logitech MX1000, Logitech MX5000."
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2007-12-13
What has been happening is that if I connect the mouse and keyboard with sudo hidd --search, they work fine.

Then after extended time not using the computer, say overnight, they won't reconnect in the morning. I have to go get the wired keyboard out, push the connect buttons, and run sudo hidd --search again.

This is most annoying, and others in my family can't use the computer because they don't know how to do that.

How can I fix this? I leave my computer on 24/7.

I have, on other (K)Ubuntu installations, tried editing some config files.  They didn't work on Kubuntu or Ubuntu.  It was where you enter the mac address of the device.  I don't really remember..

I have to go remove the trust from the devices and go though the whole connect process again.  How do I fix this?  Any ideas?

---

### Post by Mysticle31 on 2007-12-15
Anything, Anything?  I hate to shameless bump. 

I have no new news as to my problem :P

---

### Post by lenticular on 2007-12-16
No answer, but I've been having the same problem with my Logitech DiNovo mouse and keyboard since upgrading to Gutsy.  No problems in Feisty.

After some period of time (an hour or more) with no activity, the mouse and keyboard no longer respond.  Since I have a wired mouse and keyboard as well, I can go to Bluetooth Manager->Preferences and see that it believes both devices are connected.  Next, I set both to be NOT trusted, and then click disconnect.  As soon as I type a key or move the mouse, a dialog box comes up and asks me if I want to connect, and I'm good until they time out again.  Earlier, I tried leaving the devices as trusted, but then disconnecting them would never give me the reconnect dialog.

I've also tried stopping and starting the bluetooth daemon:
sudo /etc/init.d/bluetooth restart
and had good, but still temporary results.

This looks like a bug in Gutsy to me, since Feisty was fine with the same hardware.

Good luck.

-John

---

### Post by Bleifrei on 2007-12-17
Exact same problem here.  Thanks for the hidd lead to get it at least working for a bit though.  

But this is definitely one of those things that is keeping the other members afraid of Ubuntu :(   I'm almost tempted to try to kron the connect command, except I'm guessing it won't wake the devices from their sleep modes.

---

### Post by lenticular on 2008-01-01
I have found an almost effortless workaround for this problem.  Now, when inevitably and eventually, my DiNuvo mouse or keyboard is dropped by my Ubuntu desktop, I just pull the crummy Logitech BT dongle out.  Instantly, the BT Manager icon disappears. Next, I just plug the dongle back in and I have immediate connectivity with the mouse and keyboard that never drops out. The BT Manager icon never comes back. I guess my next step is to delete the BT manager from my system and see what that does.  

-John

---

### Post by ice_dm on 2008-01-11
I have the same problem too.  
Unplugging and replugging the dongle drops it into usb mode and shuts off bluetooth which is why your bluetooth icon doesn't reappear.  I've called tech support for issue in windows, but aside from this it's working fine in ubuntu.

Dan

---

### Post by jeffbski on 2008-02-22
My wife has same problem only we are using the built-in bluetooth with her laptop Dell 1420n with Ubuntu. When the keyboard or mouse go to sleep they act like they are not connected and only by turning them off and on will it usually start working again. The keyboard and mouse sleep to save battery power so this is bad since it can happen right during a working session if you don't do anything for a short period of time. 

The devices still show up in the bluetooth preferences as being trusted, but they show up as not being connected.

I'd appreciate any help in this as well. 

Thanks,

Jeff

---

### Post by mediamind on 2008-03-13
I'm also suffering from this problem (after an hour or so of inactivity) though only with my bt keyboard (apple). My bt mouse (logitch) almost never drops. i either have to reboot or drag out my wired keyboard and restart bluetooth in a terminal: sudo /etc/init.d/bluetooth restart

---

### Post by jeffbski on 2008-03-14
Yes, sudo /etc/init.d/bluetooth restart usually gets things working again too, but would love to figure out why it goes away or how to work around.

---

### Post by j4r3d6o1d3n on 2008-04-11
I'm having the same problem with Kubuntu gutsy....  Any word on a solution?

---

### Post by Jabone on 2008-04-14
I'm having same issue with MX5000 desktop set. Mouse stops working for certain amount of time and I have to restart gdm to get it working again. Keyboard works, but on every boot I have to do the hidd --search to get it working.

I'm using Hardy heron.

---

### Post by jeffbski on 2008-04-14
No word on a solution. It appears to be something related to the Logitech MX1000 MX5000 mouse and keyboard, because if I use my logitec v220 bluetooth travel mouse it works great and never has issues with timing out or not reconnecting. So its something specific to how Gutsy interacts with these devices.

---


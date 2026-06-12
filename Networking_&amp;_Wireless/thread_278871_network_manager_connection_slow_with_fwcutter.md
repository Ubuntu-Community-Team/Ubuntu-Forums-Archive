---
title: "network manager connection slow with fwcutter"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by joergenlie on 2006-10-17
After I tried fwcutter instead of ndiswrapper I managed to get network manager to work, BUT the conection is really slow.(nm says it's 100% though) I went back to using ndiswrapper and now network manager doesnt allow me to connect to wireless networks.

I have hp pavilion 9074 with broadcom chip. iwconfig ususally call it 4311, but grep says 4310. I use the wl_apsta.o driver with fwcutter.

Is there a workaround for connection speed in network manager?
I feel I'm getting close now. Network manager is a nice app and I really want it to work properly.

Edit: I got network manager to work properly in edgy with a compiled ndiswrapper 1.26. Stable connection. I tried fwcutter too, but here, still only 11M. No I'm gonna try it on my school network with PEAP.

---

### Post by joergenlie on 2006-10-22
This is a issue of 11M. NM wont't maintain connected if i switch to 54M through iwconfig. Why?](*,) 

Jørgen

---

### Post by joergenlie on 2006-10-24
I'm really working on this! Anyone with solutions?
Connection is slow, iwconfig says 11M, bur iwlist scan says 54M?
Is this a driver, hardware or both, problem?

In my opinion the linux wireless hassels should really be the number one priority. We live in a wireless world.

Why can nm pick up the net with the bcm43xx driver and not ndiswrapper?

I know it will be solved someday. In the meantime I'll be without wireless at campus.

Jørgen still](*,)

---

### Post by squibT on 2006-10-24
sudo iwconfig eth0 rate 54M works for me ...no disconects..seems faster.

---

### Post by joergenlie on 2006-10-24
> **squibT said:**
> sudo iwconfig eth0 rate 54M works for me ...no disconects..seems faster.

This makes the connection go down. The only rate that works is 11M ](*,) 

Jørgen

---

### Post by joergenlie on 2006-10-24
Now strange things are happening:rolleyes: I think I managed to fool network manager, twice.

i booted into ubuntu using the bcm43xx with fwcutter. This makes NM work, but only with the rate 11M.This is what nm says too, driver: bcm43xx Rate 11Mb/s. My interfaces file are commented out. then I did a rmmod bcm43xx and the internet connection went down. I did a modprobe ndiswrapper and connected to my network again through network manager. Bang! now I get connected at 54 Mb/s. NM says the driver is still bcm43xx though.

Have I fooled nm? Of course when i reboot with ndiswrapper I can't get nm to connect at all.

Does anyone understand this?

Jørgen

---

### Post by hurrikane on 2006-10-29
I'm having the same problems with connection speed.  I'm a newb...but the only way I can seem to get my connection up is with this method, I've been unsuccessful with ndiswrapper up to this point.  There is a very noticeable difference from this connection and the windows connection (dualboot).

NM says the connection is 11M, but the card is a Dell 1390 (E1505 Laptop) and it normally works as 54M under windows.  I've tried changing the speed with iwconfig, but this doesn't seem to make a difference.

---

### Post by Bastanteroma on 2006-10-30
Do any of y'all know how to switch from ndiswrapper to the firmware cutter approach?  I'm willing to run at 11mbps if I can get network manager, but I'm not sure how to undo ndiswrapper.  I know I blacklisted the bundled firmware, but beyond that I'm worried about breaking things.

Sorry to cut in, but it seemed like you were capable of switching.

---

### Post by joergenlie on 2006-10-30
you can blacklist ndiswrapper by writing "blacklist ndiswrapper" at the end of /etc/modprobe.d/blacklist 
If you have blacklisted bcm43xx this should show in the same file. Delete the line "blacklist bcm43xx" if you see it.

search the forum for broadcom wireless cards. This should give answers.

I have had no problems with both drivers installed. You switch by changing the blacklist file. This requires a reboot, or if you are familiar with unloading and loading drivers in terminal try the following commands after you have changed the blacklist file.

To remove one driver : sudo rmmod bcm43xx (or ndiswrapper)
to load driver : sudo modprobe ndiswrapper (or bcm43xx)

jørgen

---


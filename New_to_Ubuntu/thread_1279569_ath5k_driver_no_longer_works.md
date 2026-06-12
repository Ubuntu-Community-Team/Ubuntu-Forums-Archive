---
title: "ath5k driver no longer works"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by physics 1150 on 2009-10-01
hi everyone,

My laptop's wifi no longer works. I edited a movie with kino, came back to my browser, and no internet. Just an openDNS message saying google.com doesn't exist. I tried pinging google. nothing, no "server not found", nothing at all showed up in terminal. 

So I did the usual:
```
sudo ifconfig wlan0 down
sudo ifconfig pan0 down
sudo /etc/init.d/networking stop
sudo rmmod ath5k 
sudo modprobe ath5k 
sudo ifconfig pan0 up
sudo ifconfig wlan0 up
sudo /etc/init.d/networking restart
sudo /etc/init.d/gdm restart
```And....my wifi is now permanently trashed. When I try to start pan0, I get "no such device".

What gets me is that I've done this procedure a thousand times and never had trouble. 
My computer wouldn't respond after I modprobed ath5k, so I had to manually restart it. 

Could this be what is wrong? If so, how do I correct this? Why does ath5k randomly decide not to connect every couple weeks?

thanks!

---

### Post by physics 1150 on 2009-10-01
any suggestions???

cmon someone here probably knows. I know this isnt a normal problem but there are really smart people on this forum who probably know exactly what's wrong.

---

### Post by ptn107 on 2009-10-01
System -> Administration -> Hardware Drivers.  Enable any network adapters there.  This will blacklist 'ath5k' and allow the system to fall back on 'ath_pci'.

---


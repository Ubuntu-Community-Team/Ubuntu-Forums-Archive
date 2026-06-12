---
title: "wg511v3, yet another problem"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by benzap89 on 2008-05-21
alright, i've read a lot of guides now on setting up the netgear wg511 on earlier releases of ubuntu. however i can;t seem to get it to work with ubuntu 8.04. I blacklisted prism54, since it is unsupported by this chipset. I did this by going to /etc/modprobe.d/blacklist and adding the lines:
```
blacklist prism54
blacklist p54pci 
blacklist islsm_pci
blacklist islusb
blacklist isl3886
```

however when i do:
```
ndiswrapper -i 2802w.inf
ndiswrapper -l

```
it says
```
2802w : driver installed
        device (1260:3890) present (alternate driver: prism54)
```

nothing lights up when i do:
```
sudo modprobe ndiswrapper
```

so it isn't working. What am I doing wrong?

---

### Post by scotartt on 2008-05-22
sudo modprobe -r prism54 

#removes the prism54 driver, and only then

sudo modprobe ndiswrapper

I've got the opposite problem. I've got a 'made in taiwan' prism card (netgear WG511) that worked perfectly well out of the box in previous versions, but now i upgraded to 8.10 I have to manually 'sudo modprobe prism54' to make it work every time I restart (!!!). which it then does right away, old configuration and everything?!

---

### Post by benzap89 on 2008-05-31
wow thanks, I got activity on the card :guitar:

Well i'm gonna be using the crappy comp to host a server so it'll be on all the time (i know, wireless is  a bad choice) 

thanks again

---


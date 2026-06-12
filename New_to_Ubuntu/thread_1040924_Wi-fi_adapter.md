---
title: "Wi-fi adapter"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by natedogg23 on 2009-01-16
i have the wi-fi adapter for the nintendo wii and the windows install disc but that of course isnt going to work. is there a way to get get the wii to recognize it thru linux with out a router or something like a virtubox program? i dont think id need anything else but a substitute for that damn windows disc but i dont know what it would be

---

### Post by nhasian on 2009-01-16
wait i'm confused.  doesnt the nintendo wii already have wifi built in?  why do you want to add an ethernet to wifi bridge?

the manual for the wifi bridge probably lists the default ip address of the device.  if you plug it into your linux computer with a crossover ethernet cable and put your linux computer in the same subnet, then you can access the configuration settings via the web browser.  once you've configured the bridge you can connect it to your wii or any other ethernet device you want to make wifi enabled.

---

### Post by natedogg23 on 2009-01-16
yes it has wi fi and they sell an a usb adapter for it but the disc for install is only for windows but i know theres gotta be a way around that for linux. i think eternet would be for a wireless router which i dont have or need to get the wii online. i just need to get the wii to recognize the usb adapter thru linux instead of windows i believe

---

### Post by nhasian on 2009-01-16
first please dont double post.

If i understand correctly, this wifi adaptor doesnt physically connect to the wii at all right?  it just allows the wii to access the internet through another (windows) computer?

I understand you dont have a router.  So your linux computer is accessing the internet via an ethernet port?  Does your linux computer also have a wifi adaptor built in?  If so, then you dont need the nintendo-wifi adaptor at all.  you could just share the internet via your computer's wifi adaptor and the wii will pick it up.

if your computer does NOT have a wifi adaptor then we can try to install the nintendo-wifi adaptor.  after plugging in the nintendo adaptor, please give us the output of

```
lsusb
lshw -C network
```

---


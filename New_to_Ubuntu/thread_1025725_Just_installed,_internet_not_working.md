---
title: "Just installed, internet not working?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by vootpig on 2008-12-30
Hi, i just installed Ubuntu Intrepid Ibex on a laptop. When I booted into the new system, all was well, but after a split second the internet connection said "disconnected".     In the readouts of ifconfig and iwconfig everything looks pretty normal, and the wireless was working fine in Windows before installation. Can anyone lend me a hand in fixing this?

Thanks

---

### Post by Michael.Godawski on 2008-12-30
hi, 
have a look at this guide for the basic procedure when dealing with wlan issues: 

[LIST]
[*][http://www.godawski.oxyhost.com/solvingwireless.html](http://www.godawski.oxyhost.com/solvingwireless.html)
[/LIST]
We need the outputs from iwconfig and ifconfig.

Additionally can you please post the output from:

```
sudo lshw -C network
sudo iwlist scan
```

---


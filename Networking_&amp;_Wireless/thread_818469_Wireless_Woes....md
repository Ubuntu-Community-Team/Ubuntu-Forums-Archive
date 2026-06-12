---
title: "Wireless Woes..."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by joey-elijah on 2008-06-04
Using Ubuntu Hardy 64bit if that makes any differences, anyway. I have a USB Wifi stick thing that my desktop uses to connect to the wireless hub. It's a "ez connect N SMCWUSBS-N2" affair.

I installed ndiswrapper and installed windows xp drivers like so: -

```
ndiswrapper -i xpdrivercode.inf

ndiswrapper -m

ndiswrapper -l
```

which happily told me:

```
xpdrivercode : driver installed
        device (XXXX:XXXX) present
```

Awesome.

```
sudo modprobe ndiswrapper

sudo ndiswrapper -m
```

Somewhere along the lines i got an error that said 

> module configuration already contains alias directive

And going into system>admin>network - everything was greyed out.

Help?

---


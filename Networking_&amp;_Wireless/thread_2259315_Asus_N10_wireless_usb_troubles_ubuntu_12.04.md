---
title: "Asus N10 wireless usb troubles ubuntu 12.04"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by olivia3 on 2015-01-03
So I've recently purchased an Asus N10 wireless usb adapter because my toshiba laptop was having trouble connecting while using ubuntu. When I try to run the install.sh file found on the install cd, I get the following error.

```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308.tar
USB-N10 Linux Driver Quick Start.txt
install.sh: 25: cd: can't cd to rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308.tar
Authentication requested [root] for make clean:
install.sh: 38: [: unexpected operator
make: *** No rule to make target `clean'.  Stop.
Authentication requested [root] for make driver:
install.sh: 48: [: unexpected operator
make: *** No targets specified and no makefile found.  Stop.
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```

I can see the usb when I run lsusb

```
Bus 001 Device 003: ID 0b05:17ba ASUSTek Computer, Inc.
```

and I'm running terminal as administrator (if that makes any difference?). I've gone through many of the other N10 threads, but none of the solutions there seem to help. I'm sure it's something very simple that I'm missing, but I'm a ubuntu newbie so everything is going right over my head!

---

### Post by chili555 on 2015-01-03
Your device uses the tricky driver rtl8192cu. There is a fix here: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

---

### Post by olivia3 on 2015-01-03
Wireless now shows as being connected through my wifi adapter, thank you!

---

### Post by chili555 on 2015-01-03
> **olivia3 said:**
> Wireless now shows as being connected through my wifi adapter, thank you!Awesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---


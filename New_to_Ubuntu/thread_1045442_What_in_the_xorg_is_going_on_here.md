---
title: "What in the xorg is going on here?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by burtzacarach on 2009-01-20
I've just installed Ubuntu on a laptop, and everything is working quite well. Except for the monitor's resolution. My monitor itself supports 12XX x 7xx resolution, but when I adjusted the monitor's settings in gnome, the screen went haywire. I can't see the bottom and right sides of my desktop, and I am wondering if there is an adjustment I can make in /etc/X11/xorg.conf to permanently adjust my monitor's settings?
Thanks brewers.

---

### Post by taurus on 2009-01-20
Which graphic card do you have and have you installed a driver for it?  Look in System -> Administration -> Hardware Drivers to see if your graphic card is on the list.

---

### Post by burtzacarach on 2009-01-20
Hardware Drivers

"No proprietary drivers are in use on this system"

I'm not sure what graphics I'm using, it being an onboard chip on my laptop's mobo. It's a Gatewat MX3231 with a VIA VN800 chipsetand a Celeron M processor, and if I'm not mistaken I think it's Nvidia graphics.

---

### Post by taurus on 2009-01-20
Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by burtzacarach on 2009-01-20
"01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)"

---

### Post by burtzacarach on 2009-01-20
and "lspci" is the command that lists all pci port connections?
what does "grep" do?
I'm trying to learn as I go.

---

### Post by Terl on 2009-01-20
> **burtzacarach said:**
> and "lspci" is the command that lists all pci port connections?
what does "grep" do?
I'm trying to learn as I go.

grep searches for a string...in this case it looked for VGA.  The | is called a pipe, the command of lspci was "piped" through grep and filtered

---

### Post by burtzacarach on 2009-01-20
So now how do I find a video driver that works with my graphics card?
I'll have to browse the packages on a separate computer because I haven't yet gotten my PCMCIA internet modem to work.

---

### Post by Terl on 2009-01-20
You might have some luck [reading this thread]("http://ubuntuforums.org/showthread.php?t=636368&highlight=via+openchrome")

---


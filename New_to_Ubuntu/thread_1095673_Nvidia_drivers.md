---
title: "Nvidia drivers"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by The-IRS on 2009-03-14
I tried to install the Nvidia drivers for my  GTX 260 and after wrestling through some post installation problems I was left with a computer that has iffy graphics. When I run nvidia-xconfig, this is what I get:

```
stewart@Stewarts-desktop:~$ sudo nvidia-xconfig
[sudo] password for stewart: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

sh: pkg-config: not found
sh: pkg-config: not found
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

any Ideas? 

and when I try to run the Nvidia X server settings it says:

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

---

### Post by brettg on 2009-03-14
This is your clue;

"Device section "Configured Video Device" must have a Driver line."

Open /etc/X11/xorg.conf and find the section "Configured Video Device"

In that section add;

Driver "nvidia" (include the quotes)

If that doesn't work it means you haven't installed the drivers properly.

Go back and change "nvidia" to "nv" and you should get a non accelerated gui back

---

### Post by The-IRS on 2009-03-14
okay it says:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

where do i put it?

---

### Post by brettg on 2009-03-14
Once you have done that reboot your PC

---

### Post by hobo on 2009-03-14
Download EnvyNG. It detects your card type and installs it all for you.
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by isbjorn1 on 2009-03-23
Did you find suitable drivers for your GTX260? I'm struggling with a similar problem.

---


---
title: "Startup stalls at &quot;Configuring Network Interface&quot; when network cable is unplugged"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by spidermagicat on 2008-12-02
I've only noticed this problem now I have started moving my laptop around again

I started with an ubuntu-minimal install and built up gnome from there to avoid having to remove programs I don't want and also to allow me to install from the internet directly. Everything is perfect now apart from this.

The startup stalls at "Configuring Network Interface" when network cable is unplugged.

It will stay there for about 2 minutes or I have to use Ctrl Alt Delete to continue the boot but I loose the network services and have to start them myself.

Is there a way to stop this happening, I would prefer it if the network management was running on boot as that way I can still use the internet without gui when I have reason to do so.

Basically I'm asking if I can have it continue booting regardless of the status of the network, but still have it trying to connect as it does now.
Any other suggestions and compromises are welcome but this is just the ideal :-)

---

### Post by umechanism on 2009-03-18
I'm having a similar problem with my desktop.  Did you ever find a solution?

tks.

---

### Post by spidermagicat on 2009-03-18
I did in fact :-), erm... what was it

I believe I disabled the configuring of the network at this point and let nm-applet do it a few seconds later

---

### Post by spidermagicat on 2009-03-18
Aha, I remember properly now

run "sudo gedit '/etc/network/interfaces' " (or a using a different text editor) 

comment out all the lines with #

Mine looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto lo
# iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

then setup a network applet to configure for you and you should be fine, if you ever need to switch back to the previous configuration you can just remove the "#" and go back to where you are now

---

### Post by umechanism on 2009-03-20
By setting up a "network applet", do you mean to use Gnome's Network Manager?

Thanks!

---

### Post by spidermagicat on 2009-03-20
I do yes :-)

---


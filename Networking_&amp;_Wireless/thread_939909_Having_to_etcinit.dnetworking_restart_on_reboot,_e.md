---
title: "Having to etc/init.d/networking restart on reboot, etc"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by Phases on 2008-10-06
Hey all. Please bear with me, I'm sorta new to Linux. 

I'm having some trouble with various things getting this Ubunutu install to do what I need it to do. I'm hoping I can get a little advice here, as this has been kickin' my butt all day. Basically, here's the short story.

In /etc/network/interfaces I have this:
```

# The loopback network interface
auto lo
iface lo inet loopback
# An entry for eth0 is no longer needed
auto eth0
iface eth0 inet dhcp
# Create the bridge (with the regular IP address of the host)
auto br0
iface br0 inet dhcp
        bridge_ports eth1
#        bridge_fd 2.5
```

Reason being, I want to have VirtualBox run off the bridge that's attached to one card (eth1), and have my host, Ubuntu, run off another. (eth0)

On reboots it does fine, creates br0 and attaches it to eth1 and everything gets an ip. The problem though, I have to run /etc/init.d/networking restart to get connectivity?? 

So, I did some googling around and found this:

[http://ubuntuforums.org/showthread.php?t=798231](http://ubuntuforums.org/showthread.php?t=798231)

And it looked like what I needed, so I tried it, but it still does the same thing, I log in and have no internet, do the restart and I do. 

It is baffling me. Between this a couple other things I've been at it for a couple days now.

Any advice appreciated. 

Oh, anothing quick thing while you're here - when Ubuntu is loading up (grub i guess?) it hangs for a minute, which is a new thing - and also after I log in it hangs for even longer on that pale screen before loading everything up. This wasn't happening until recently. How can I watch what services etc that it's loading up instead of the graphical, to perhaps find what it's hanging on? 

Thanks again.

---

### Post by nixscripter on 2008-10-06
If eth1 is only going to be used for VirtualBox, I would suggest making it use a TAP device instead. It acts like a fake interface, thus not messing with your other settings.

It's in the directions here: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---


---
title: "Headless Install Ubuntu Server"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-10
Dear Forum,

I've not found anything in the search so I'm guessing it isn't possible.

I'd like to reinstall my server with Karmic server, including a reformat. I've got the USB disk ready and am ready to roll.

The server doesn't have a monitor or keyboard at the moment. I use SSH to control it from the desktop.

Is there a way to make the live USB install automatically, load Open SSH by default and create the correct administrator user?

The router is already configured to give the server the same IP address based on the adapter MAC (by DCHP) so I can be sure to know which internal network address I'm looking for.

Seems like this should be basic, I guess hundreds of folks must install this kind of server daily. I can't believe they are all plugging a monitor and keyboard in for the install. What if the server didn't have a graphics card (as was the case with my old NAS).

TIA


Rich

---

### Post by spiderbatdad on 2009-11-10
you're talking about a network installation or a PXE installation There is a lot of information available to help you. You will need to at least make a netboot usb or cd img. consider reading a couple of tutorials and seeing which approach you want to try. Here is one example 
[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)
[https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

---

### Post by RichardCL on 2009-11-10
> **spiderbatdad said:**
> you're talking about a network installation or a PXE installation


Many thanks spiderbatdad. I've been so hung-up in SSH/auto generate user/install remote should have thought of searching for "network"!

---

### Post by RichardCL on 2009-11-10
Actually, I realise now that the netboot is not what I need.

I want to install without keyboard and monitor. It is fine to get sources from a liveUSB.

What I need is a way to pre-select all of the options:
```

partion: guided, use entire disk, LVM
language:en-uk
keyboard:de, nodeadkeys
package-sel: openSSH, lamp
createuser: rich, password


```
etc. etc.

I should be able to configure the USB such that I insert (the bios already boots from USB if available) and wait for the server to reboot then login from puTTy.

I've googled for a good hour and not found anything except a utility that works with Redhat. It is way over my head to try and recompile that for Ubuntu.

---


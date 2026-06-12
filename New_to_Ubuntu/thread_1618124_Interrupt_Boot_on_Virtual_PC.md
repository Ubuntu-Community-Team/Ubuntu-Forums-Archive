---
title: "Interrupt Boot on Virtual PC"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by brand_noobian on 2010-11-10
Hi Ubuntu dudes

I've created a /etc/X11/Xorg.conf file to increase the resolution size on my MS Virtual PC install of Ubuntu and now it doesn't boot at all. sigh

Stupidly I followed this link [http://helpdeskgeek.com/virtualization/fixing-screen-size-resolution-in-virtual-pc-running-ubuntu/](http://helpdeskgeek.com/virtualization/fixing-screen-size-resolution-in-virtual-pc-running-ubuntu/)

What can I do to revert back as my distro doesn't even boot now :( and also how do I correctly increase my res? 800x600 is no use to anybody!

Cheers for any help.

---

### Post by toekneewood on 2010-11-10
Have a go with 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by brand_noobian on 2010-11-10
nice one but how do I get to a command line if I can't boot? sorry for the daft question

---

### Post by brand_noobian on 2010-11-11
> **toekneewood said:**
> Have a go with 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg

```

thank you, but how do I interrupt the boot so I can enter a command, my screen just stays black?

---

### Post by Mark Phelps on 2010-11-11
Hold down the SHIFT key while booting.  That should force the display of a GRUB menu, then select Recovery Mode.  That will get you into a command line eventually.

Sorry ... missed that part about this being Virtual PC.  This will only work if you're running Ubuntu natively.  Don't have any idea how to force a boot in a VM environment.

---

### Post by brand_noobian on 2010-11-12
> **Mark Phelps said:**
> Hold down the SHIFT key while booting.  That should force the display of a GRUB menu, then select Recovery Mode.  That will get you into a command line eventually.

Sorry ... missed that part about this being Virtual PC.  This will only work if you're running Ubuntu natively.  Don't have any idea how to force a boot in a VM environment.

oh no does anyone know how to force a boot in Virtual PC?

---


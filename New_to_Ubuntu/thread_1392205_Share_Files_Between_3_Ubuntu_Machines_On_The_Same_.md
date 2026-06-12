---
title: "Share Files Between 3 Ubuntu Machines On The Same Wireless Network?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Monrizzy on 2010-01-27
I'd like to share files between 3 Ubuntu 9.10 machines on my wireless network and I'm afraid I don't know where to start.  Does any one have any suggestions?  Thanks!

---

### Post by nhasian on 2010-01-27
lots of ways to do it but the easiest way may be to just right click on the folder you'd like to share and select "Sharing Options" then "Share this folder"

then the other computers will see the shared folder from Places->Network

---

### Post by Monrizzy on 2010-01-27
I went to the folder and enabled the share option and now the computer that actually physically has the files on it is behaving strange.  I've got an info panel screenlet up and it shows that one core of my dual core processor is constantly at 90% causing my machine to run very slow.  Any idea's why that would be?

---

### Post by Monrizzy on 2010-01-27
It was a very large folder that I shared.  I also noticed that my upload indicator is at about 130-200 KB/s while one of the other machines is accessing the shared folder.

---

### Post by Monrizzy on 2010-01-27
Something has caused my system to slow down tremendously.  Does anybody have any clues to fix this?  It happened after I shared a very large folder across my network for the first time.

---

### Post by Monrizzy on 2010-01-27
it appears that Xorg is taking 91% of resources.  Please help!

---

### Post by dearingj on 2010-01-27
> **Monrizzy said:**
> Something has caused my system to slow down tremendously.  Does anybody have any clues to fix this?  It happened after I shared a very large folder across my network for the first time.

Are you sure that's all that's changed? I don't see why sharing files would have any significant effect on your system's speed.

---

### Post by Monrizzy on 2010-01-27
That's the only thing I did to it.  I choose the folder that I wanted to share and then it prompted me to install what appeared to be samba.  Then it required me to restart the session and when I logged back in it was running very slow. I've rebooted several times.  I've even logged in to a kde session and didn't notice the same amount of lag.

---

### Post by nhasian on 2010-01-29
> **Monrizzy said:**
> it appears that Xorg is taking 91% of resources.  Please help!

check to see what graphics drivers your using.  that may be the culprit...

```
lshw -C display
```

---

### Post by Monrizzy on 2010-01-30
> **nhasian said:**
> check to see what graphics drivers your using.  that may be the culprit...

```
lshw -C display
```

The problem went away after a system update. The computer was working fine and then I attempted to use the Istanbul Desktop Session Recorder and had to lock out of the session because that application apparently didn't want to respond.  When I logged back in to the gnome session my Xorg problem had returned.

> *-display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 2600 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:26 memory:e0000000-efffffff(prefetchable) memory:fdde0000-fddeffff ioport:de00(size=256) memory:fddc0000-fdddffff(prefetchable)


---


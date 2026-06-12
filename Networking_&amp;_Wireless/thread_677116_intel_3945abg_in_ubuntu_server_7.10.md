---
title: "intel 3945abg in ubuntu server 7.10?"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by stairwayoflight on 2008-01-24
Hello,

I recently decided to whittle things down a bit to ubuntu 7.10 gutsy server base install.

I have got X and a wm working but need to use my intel 3945abg wireless card, its a centrino laptop.

I thought there was a package called ipw3945d or thereabouts, but I'm having trouble finding it. I'm not familiar with the cli package commands, other than the basics like updating, installing, etc. I can't find it, even after uncommenting all repos in my sources.list.

Sorry if this is listed in another place, but I don't know if its my dreadfully slow, dying connection or what by the "before posting try these similar threads" links have disappeared.

Thanks in advance for any help,
stwy

---

### Post by stairwayoflight on 2008-01-24
Actually,

I managed to install the extra kernel modules necessary with linux-386, but even though I can see the ipw3945.ko file in the directory tree for the "386" kernel modules, the correct version reported by 'uname -a', I can't modprobe it, I don't know why.

I tried installing restricted-manager, that doesn't help either. Any suggestions?

---

### Post by chili555 on 2008-01-24
What happens when you try to sudo modprobe ipw3945? What is the output of ```
lsmod | grep 3945
```

---

### Post by stairwayoflight on 2008-01-25
> **chili555 said:**
> What happens when you try to sudo modprobe ipw3945? What is the output of ```
lsmod | grep 3945
```

Nothing, its not loaded.

---

### Post by stairwayoflight on 2008-01-27
Ok,

I'm regrouping, I reinstalled from the gutsy server cd. It had the module with the kernel installed already. I can modprobe it and lsmod shows its loaded. What I don't have is the interface ubuntu desktop gave me before. (ifconfig gives me lo and eth0, my ethernet card, but not eth1, which was the interface my 3945abg card used to have.)

---

### Post by sdlvx on 2008-01-27
I have the same problem.  I want the server version, because I want 64 bit and to install KDE4 on my own.  eth1 doesn't show up when I do ifconfig, but when I do lsmod | grep 3945  like you said, I get

ipw3945 139680  0
ieee80211 45512 1 ipw3945

---

### Post by stairwayoflight on 2008-01-28
Ahh,

(problem solved)

So for some reason it seemed like the -server- kernel had the module for the device but didn't provide me with an interface?

Maybe I made some error and didn't check the output of 'iwconfig' when the wireless switch was set to on? I know I checked it, but as my previous experience has always been that I get an interface reported from *both* iwconfig and ifconfig, perhaps I saw the interface missing from ifconfig output (which I am sure I checked with the switch in the correct position) and assumed it wasn't recognized. THIS WAS ALL AFTER I REINSTALLED GUTSY SERVER AND STILL HAD THE 'SERVER' KERNEL.

But as I didn't want the 'server' kernel anyways, I installed 'linux-386' and after a reboot iwconfig shows the interface. Obviously you've got to get it up and set the channel, etc, from the command line unless you install the network manager, but its a relief. What surprised me is to see ifconfig still doesn't show it, but that makes sense if it wasn't added to the boot scripts on install.

I hope this helps somebody.

---

### Post by helpdeskdan on 2008-01-31
Wait, you did what now?  I've got linux-image-generic installed and I see the drivers & not the interface just like you, but I'm not running server - I have linux-image-generic in gutsy.  What image are you using?  Thanks - I really don't want to have to manually disable these drivers and compile new ones from sourceforge.

---

### Post by helpdeskdan on 2008-01-31
Ah, you mean linux-image-i386.  Tried it, didn't work.  I have the same problem as sdlvx.  ifconfig iwconfig - NOTHING.  Note - you do need the restricted modules, but that didn't fix my problem.

If anybody has found a solution, please post

---

### Post by helpdeskdan on 2008-02-05
Bah!  Never mind.  There is this little button the laptop you have to press to turn on the wireless card.  It can only be turned on via this button - you can try to set kill switch manually, but it won't work. Find the button.

---


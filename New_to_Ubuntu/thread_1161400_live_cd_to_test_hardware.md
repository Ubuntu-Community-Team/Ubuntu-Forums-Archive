---
title: "live cd to test hardware?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by beyondhuman on 2009-05-16
Hello everybody,

I am considering switching to ubuntu but have read that my computer model (acer aspire 3680) is kind of a toss up as far as compatibility is concerned (they have various wifi cards).

If I pop in the live cd and everything works fine does that mean it's a go?  

Or is there still a chance my hardware might not be compatible (namely the wifi)?

And if it will be an acturate test does this apply to other distro's live cd's as well? If I pop in the DSL cd will it be an acurate representation of hardware compatibility?

Thanks

---

### Post by Kimm on 2009-05-16
Pretty much. But if the hardware doesn't work on the Live CD that doesn't mean you cant get it running on the full install

---

### Post by whoop on 2009-05-16
I would pretty much use the livecd from the distro you are planning to install.

---

### Post by whoop on 2009-05-16
> **Kimm said:**
> Pretty much. But if the hardware doesn't work on the Live CD that doesn't mean you cant get it running on the full install
Wouldn't that be if you can't get it running on the livecd you will probably not get it running on the machine? This because you can install drivers & configure away on a running livecd as long as you don't have to reboot.

---

### Post by mikewhatever on 2009-05-16
> **whoop said:**
> Wouldn't that be if you can't get it running on the livecd you will probably not get it running on the machine? This because you can install drivers & configure away on a running livecd as long as you don't have to reboot.

Sometimes, you can install, and then apply fixes, or manually install stuff you need, ndisrapper for example. It's not always easy, but can be done.

---

### Post by mc4man on 2009-05-16
> configure away on a running livecd as long as you don't have to reboot.

While I'm not sure about wifi drivers you can test things that normally require a reboot on a live cd by logging out and then back in .
That's how I see if the restricted nvidia video drivers are going to work

---

### Post by mikewhatever on 2009-05-16
> **mc4man said:**
> While I'm not sure about wifi drivers you can test things that normally require a reboot on a live cd by logging out and then back in .
That's how I see if the restricted nvidia video drivers are going to work

I don't think that's correct. By logging out you reload xserver, while in the case of nvidia driver, the kernel needs reloading.

---

### Post by mc4man on 2009-05-16
I just did it the other day on my little m1330 laptop, will double ck. though (I was surprised)
I was able to enable  'extra' desktop effects, make changes in Nvivia X server Settings, ect.


Maybe I was still on nv, now I'm curious...?

---

### Post by mc4man on 2009-05-17
from the laptop
Really don't know what to think, one of my 'issues' with the live cd has always been you can't test video drivers.

It's certainly acting like they're being used, though if I go to system -> restricted drivers it says I still need  to reboot (I'd like to believe it

On the other hand, 'extra'  effects have been enabled, first attempt downloaded and install the 180 drivers, second attempt before logging out wouldn't allow setting, now they're set
(**no ccsm installed**, have desktop wall, wobbly windows ect.

Nvidia setting's let me change things, lshw shows nvidia, so really don't know
> configuration: driver=nvidia latency=0 module=nvidia

> 
ubuntu@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4


> ubuntu@ubuntu:~$ dkms status
nvidia, 180.44, 2.6.28-11-generic, x86_64: installed 


Any other way to tell for sure (will leave live cd up for a while

Edit ( everything posted is the same thing my nvidia desktop reports other than driver version (185.13,......

re-edit
Had ocassion to boot to live cd this morning, I'm inclined to say you can test and use restricted video drivers on the live cd

Before and after installing the drivers but before logging out and in 

> ubuntu@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI

After logging out and in as previously posted
> ubuntu@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation


---


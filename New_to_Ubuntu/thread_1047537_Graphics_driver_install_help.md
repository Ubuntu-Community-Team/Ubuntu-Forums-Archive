---
title: "Graphics driver install help"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by WU8V on 2009-01-22
I have just installed Ubuntu on an older machine. the Video card is a GFX5200 (Nvidia) with 128M ram.

The "restricted drivers screen says that it recomments NVidia driver V173

I have no internet access on that machine yet, and need to install from a flash drive. Where do I get this driver so that I can get the screen to 1024x768?

Exactly how do I install this driver once I get it.

Thanks for any help.
Regards,
Kurt

---

### Post by Ben Page on 2009-01-22
Not really shure, but, download the linux driver from nvidia site, and then do
 "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" to install
There are instructions there, too, might check it out...

---

### Post by bsharp on 2009-01-22
64-bit:
[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

32-bit:
[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

Press Ctrl+Alt+F1 to switch to another terminal, log in, and:
```
sudo /etc/init.d/gdm stop
cd /directory/with/driver/file
sudo chmod +x NVIDIA*
sudo ./NVIDIA*
```

And follow the onscreen instructions.

---

### Post by WU8V on 2009-01-22
bsharp, 

Thanks, got that going, but then it wants a precompiled kernel module...
I don't have one, so I tell it to compile.... Error

since the machine has no internet connection yet, I need to find where to get this module, and where to put it once i find it.

Thanks again,
Kurt

---

### Post by bsharp on 2009-01-22
Put in your install disk and

```
sudo apt-cdrom add
sudo apt-get install build-essential

```
Then install the drivers like before.

---

### Post by WU8V on 2009-01-22
bsharp,

No joy yet... this last one... I still need to compile kernel module, and it still fails....

Ideas?

Thanks again
Kurt

---

### Post by bsharp on 2009-01-22
Oops, try this:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

and then run the installer

```
sudo ./*.run
```

---

### Post by WU8V on 2009-01-22
I think that the get-update is an internet thing?

unfortunatly, I do not have that fixed up either still having problems getting connected

is there something that i can get on a jump drive an transport over.... and where would it go if I could?

thanks
Kurt

---

### Post by WU8V on 2009-01-22
sounds like I beter get my network working first so I can get the packages that I need

TO BE CONTINUED......

regards,
Kurt

---


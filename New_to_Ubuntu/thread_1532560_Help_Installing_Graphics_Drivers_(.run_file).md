---
title: "Help Installing Graphics Drivers (.run file)"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Demolition Man on 2010-07-16
I am trying to install graphics drivers for my NVIDIA GeForce 6150 SE. I right-click on the drivers package I downloaded from NVIDIA's website, select "run in terminal," the installer runs but then I get an error message saying "nvidia-installer must be run as root." What do I need to do? TIA

---

### Post by emoguitarist06 on 2010-07-16
FIRST I recommend installing the propriety Nvidia drives included in Ubuntu
System > Administaration > Hardware Drives
Activiate Nvidia

if no luck than run
> sudo ./filename.run

---

### Post by Naitsirhc Hsem on 2010-07-16
Just an addon to emoguitarist,
open the terminal and type
```
 cd Downloads
sudo ./filename.run 
```

quick tip, when you are typing in the filename, hit tab once you have the first few characters in, it auto completes the file

---

### Post by emoguitarist06 on 2010-07-16
> **Naitsirhc Hsem said:**
> 
quick tip, when you are typing in the filename, hit tab once you have the first few characters in, it auto completes the file

I second this tip!

**Remember though that Ubuntu is case sensitive so if the file name is Nvidia.run you must type a capital "N" lower case "v" then tab :)

EDIT: Also make sure when you open the terminal you must change from your home directory to whatever directory your filename.run is located (unless of course it is in your home directory)
Example: 
```

cd Downloads
sudo ./filename.run
```

---

### Post by Demolition Man on 2010-07-16
> **emoguitarist06 said:**
> FIRST I recommend installing the propriety Nvidia drives included in Ubuntu
System > Administaration > Hardware Drives
Activiate Nvidia

if no luck than run

When I go to "System > Administration > Hardware Drivers", there are no drivers listed for me to enable.

The "sudo" option seems to have worked, though. Thank you.

---


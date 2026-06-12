---
title: "Module with parameters at startup, how?"
date: 2005-04-08
forum: Networking &amp; Wireless
---

### Post by eric71 on 2005-04-08
Due to my weird internet access in my building I use something called "Home PNA" or HPNA.  It is a network run through the buildings phone lines.  I have to use a USB network interface called the ADM8511 Pegasus II, which can do both normal ethernet and HPNA.  THe pegasus module is part of the kernel and Ubuntu detects and loads it fine.  The only issue is that by default it is not in HPNA mode, and during boot it can't connect via DHCP.  So I have a little bash script I run via a panel launcher to rmmod pegasus and modprobe pegasus with the correct parameter (mii_mode=1) so it is in HPNA mode.

Though this isn't too inconvenient, I'd like it to go into HPNA mode from the start and connect during boot.  I've tried adding "pegasus mii_mode=1" to etc/modules, but although it loads pegasus, it does not seem to see the parameter. I've tried it without qotes and with quotes.  Nothing seems to work.

Does anyone know how this can be done?

---

### Post by p!=f on 2005-04-08
You may try following...
```

sudo -s
echo "options pegasus mii_mode=1" > /etc/modutils/pegasus_hpna
update-modules

```
example:
* nvidia-options file with various module options created
```

[~] > cat /etc/modutils/nvidia-options
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRATE=8

```
* run update-modules to update modules :)
```

sudo update-modules

```
* check /etc/modules.conf for the changes
```

[~] > grep -i nvidia /etc/modules.conf
### update-modules: start processing /etc/modutils/nvidia-kernel-nkc
alias char-major-195 nvidia
### update-modules: end processing /etc/modutils/nvidia-kernel-nkc
### update-modules: start processing /etc/modutils/nvidia-options
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRATE=8
### update-modules: end processing /etc/modutils/nvidia-options

```

---

### Post by erkki70 on 2005-04-08
Terve!
[QUOTE=jdong]patience. Debian still uses /etc/modules/ to house all module configurations. There's where all the config goes. If it's a **module-init-tools specific** command (like load or unload actions), they need to go in /etc/modprobe.d/. After editing, you must run **update-modules** for your changes to be merged with the system modules config.[/QUOTE]
Original thread here
[http://www.ubuntuforums.org/showthread.php?p=6003&mode=linear]("http://www.ubuntuforums.org/showthread.php?p=6003&mode=linear")

You could try 
 ```
sudo nano /etc/modprobe.d/aliases
``` 
And add
 ```
alias pegasus
option mii_mode=1
``` 
Save and 
 ```
sudo update-modules
```
 
Hope this helps.

Cheers,
Erkki

---

### Post by eric71 on 2005-04-08
[QUOTE=erkki70]Terve!

Original thread here
[http://www.ubuntuforums.org/showthread.php?p=6003&mode=linear]("http://www.ubuntuforums.org/showthread.php?p=6003&mode=linear")

You could try 
 ```
sudo nano /etc/modprobe.d/aliases
``` 
And add
 ```
alias pegasus
option mii_mode=1
``` 
Save and 
 ```
sudo update-modules
```
 
Hope this helps.

Cheers,
Erkki[/QUOTE]

Kiitos! I'll try it. 

Eric

---

### Post by eric71 on 2005-04-08
THe exact syntax required to be added to aliases was:

alias eth2 pegasus
options pegasus mii_mode=1

with a little trial and error, it works!  

Thanks for the help,

Eric

---

### Post by erkki70 on 2005-04-08
Great!
Thanks for sharing the right syntax to fix this problem. :wink:
Cheers,
Erkki

---

### Post by usama_ah on 2006-05-31
so i'm planning on installing ubuntu 5.10 .. i was wondering where i can get pegasus and how i can edit everything like you did? i too have an HPNA adapter and Ubuntu can't detect it -- it's obvious that i'm an extreme newbie but i'm tired of Windows and I heard Ubuntu was good (and Knoppix apparently, but I want to try Ubuntu first).

any help would be apperciated.

---

### Post by eric71 on 2006-06-05
Make sure you use 5.10, as for some reason the driver is a bit buggy in kernel 2.6.15 in Dapper Drake.  It initially connects, getting an IP address, but slows down and dies rather quickly. every distro I've tried with kernel 2.6.15 has this problem.  I'm now using 2.6.16 in Debian Sid, and all is well again. I reported the bug, and even emailed the driver's developer, but got nowhere. At least it seems to be fixed now, just not for Dapper.

But if you are using 5.10, then you should be fine.  The pegasus module is included with the Linux kernel. If your adapter does indeed have a Pegasus chipset, it will be detected fine.  The problem is that it doesn't automatically detect that you are on an HPNA network.  You will need to follow the instructions in the earlier posts to turn on HPNA mode to get it to work.

Eric

---


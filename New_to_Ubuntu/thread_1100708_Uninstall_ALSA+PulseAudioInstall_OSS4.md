---
title: "Uninstall ALSA+PulseAudio/Install OSS4"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2009-03-19
What's the proper way to go about uninstalling ALSA/PulseAudio and the other audio drivers and replacing them with OSS4?

I'm on Ubuntu 8.10 and I don't have any idea what I'm doing.

---

### Post by Eisenwinter on 2009-03-19
If you installed ALSA through the package manager, type the following command:

```
sudo apt-get remove alsa && sudo apt-get autoremove
```

---

### Post by subaruwrc01 on 2009-03-19
I'm getting an error when I run that code.

```
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

---

### Post by Ms_Angel_D on 2009-03-19
> **subaruwrc01 said:**
> I'm getting an error when I run that code.

```
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Look at the code you posted it's telling you what to do

Open the terminal Accessories->Terminal

and run ```
sudo dpkg --configure -a
```

then try Eisenwinter's suggestion.

---

### Post by gavin8or on 2009-09-06
Go here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Do it now. Save your audio life on ubuntu. Pulseaudio is kinda cool but kinda like putting a hemi into a pinto... send your ALSA to the crusher! I've never regretted it, audio quality is better, everything Just Works, virtually zero latency.

---


---
title: "Changing my resolution"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Samip on 2009-08-07
I have a Toshiba Portege 3500 that I just installed Ubuntu 9.04 on. The max screen resolution is 1024 x 768, but in Display Preferences, the Resolution only goes up to 800x600. How do I raise the resolution higher?

---

### Post by Buuntu on 2009-08-07
Have you activated your driver in System > Administration > Hardware Drivers?

---

### Post by Samip on 2009-08-07
There are no related drivers listed there.

---

### Post by mapes12 on 2009-08-08
Applications>Accessories>Terminal

Type this and post the output back here

```
sudo lshw -C Display
```

---

### Post by blazes8n on 2009-08-08
Hi there. I'm just looking around as I have the same problem as you...resolution at 800x600 but should be higher. And no hardware drivers. However, I have been going round in circles on Terminal and various commands. I am currently looking for any drivers, and am attempting also /etc/X11/xorg.conf....does anyone know how to manually alter the configeration on the new Ubuntu 9.04?

---

### Post by Liolikas on 2009-08-08
> **blazes8n said:**
> Hi there. I'm just looking around as I have the same problem as you...resolution at 800x600 but should be higher. And no hardware drivers. However, I have been going round in circles on Terminal and various commands. I am currently looking for any drivers, and am attempting also /etc/X11/xorg.conf....does anyone know how to manually alter the configeration on the new Ubuntu 9.04?
```

sudo lspci | grep VGA

```
Show here what you have.

---

### Post by Samip on 2009-08-08
@mapes12
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=8

```

@Liolikas
```
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

```

---

### Post by LewRockwell on 2009-08-08
[http://ubuntuforums.org/showthread.php?t=1234831](http://ubuntuforums.org/showthread.php?t=1234831)

.

---


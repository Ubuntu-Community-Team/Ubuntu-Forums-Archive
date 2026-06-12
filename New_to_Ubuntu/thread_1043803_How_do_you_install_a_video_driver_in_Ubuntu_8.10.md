---
title: "How do you install a video driver in Ubuntu 8.10"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by jacatone on 2009-01-18
Ubuntu 8.10 certainly fixed the whole wifi problem with the new 2.6.27 kernel, but now there are video driver problems. Anyone know how to install an Nvidia or ATI driver in this distro? Envy doesn't seem to work anymore. Thanks.

---

### Post by taurus on 2009-01-18
See if your card shows up on the System -> Administration -> Hardware Drivers.

---

### Post by jacatone on 2009-01-19
Nope, that was the first thing I checked.

---

### Post by taurus on 2009-01-19
What kind of graphic card do you have?

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by jacatone on 2009-01-19
Say's it's a GeForce2 MX/MX 400 which according to Synaptic is covered with the nvidia-glx-71 driver. Synaptic shows the driver as installed, but I can't figure out how to get it working.

---


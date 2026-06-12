---
title: "Question about modprobe"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by nebu on 2009-07-23
If i add a particular module to my kernel.... will it remain after a restart.... as in.... is the loading of the module permanent? or do i have to load the module into the kernel every time i use the hardware?

im talking particularly about the usbserial module....

---

### Post by sisco311 on 2009-07-23
> **nebu said:**
> If i add a particular module to my kernel.... will it remain after a restart.... as in.... is the loading of the module permanent? or do i have to load the module into the kernel every time i use the hardware?

im talking particularly about the usbserial module....

Just add it to the /etc/modules file.

If you have to specify some custom options, then you have to create .conf file in /etc/modprobe.d/.

What's the command you use to load the module?

---

### Post by nebu on 2009-07-23
heres the command...
> 
modprobe usbserial vendor=something product=something


---

### Post by sisco311 on 2009-07-23
```
echo "options usbserial vendor=something product=something" | sudo tee /etc/modprobe.d/usbserial.conf
```
should do the trick.

---

### Post by ~sHyLoCk~ on 2009-07-23
> **sisco311 said:**
> Just add it to the /etc/modules file.

If you have to specify some custom options, then you have to create .conf file in /etc/modprobe.d/.

What's the command you use to load the module?

Don't you have to regenarate your kernel image?

---

### Post by wizard10000 on 2009-07-23
> **~sHyLoCk~ said:**
> Don't you have to regenarate your kernel image?

Nope - not if the driver is compiled as a module, which apparently it is.

---


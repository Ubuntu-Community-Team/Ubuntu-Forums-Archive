---
title: "visual problem"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dowgman1 on 2009-05-13
since upgrading to 9.04 i have been getting  black lines throghout my monitor.i checked my cable with no luck then switched the monitor to another computer.using microsoft and the screen was fine. is there a problem on your end?

---

### Post by ashmew2 on 2009-05-13
> **dowgman1 said:**
> since upgrading to 9.04 i have been getting  black lines throghout my monitor.i checked my cable with no luck then switched the monitor to another computer.using microsoft and the screen was fine. is there a problem on your end?

Welcome to the community , Well i think itll be better if we had more information about your system , so could you open a terminal and post the output of :
```

lsusb
```

PS - Whats with the > is there a problem on **_your_** end?

---

### Post by billgoldberg on 2009-05-13
> **dowgman1 said:**
> since upgrading to 9.04 i have been getting  black lines throghout my monitor.i checked my cable with no luck then switched the monitor to another computer.using microsoft and the screen was fine. is there a problem on your end?

Install your graphics driver.

If the problem remains, turn off compiz fusion or try another driver (or the open source one).

If you need help with those things, let us know.

---

### Post by dowgman1 on 2009-05-13
> **ashmew2 said:**
> Welcome to the community , Well i think itll be better if we had more information about your system , so could you open a terminal and post the output of :
```

lsusb
```PS - Whats with the

Here is what terminal told me.

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0553:0a02 STMicroelectronics Imaging Division (VLSI Vision) 
Bus 003 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

As per your, I meant is linux having a display problem with certain hardware when the 9.04 version launched. I had no problems with 8.04. As per graphics drivers, they are updated.

---

### Post by dowgman1 on 2009-05-13
> **billgoldberg said:**
> Install your graphics driver.

If the problem remains, turn off compiz fusion or try another driver (or the open source one).

If you need help with those things, let us know.

who or what exactly is compiz fusion? I have the AMD/ATI driver installed.

---

### Post by Frank-er on 2009-05-14
Anyone get anything on this? I've been staring at this with nothing!

---

### Post by bacardiandwatermelon on 2009-05-14
Try using a live cd to see if the graphics are fine. It might have been an issue with the upgrade. It may be required to do a clean install? Maybe? :-)

---

### Post by dowgman1 on 2009-05-15
I turned compiz fusion on and off...<i found out how to do so by using the search function.

Nothing tho, the lines are still blaring and obnoxious.

Any other methods other than a clean install? If so, im going to go back to 8.10

---


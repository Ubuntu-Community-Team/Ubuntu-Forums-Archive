---
title: "High PCI Adapater Temp: Why?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Ron Carson on 2011-04-16
Recently, my fans have been running full speed for extended periods. Sensors says:

> acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0 C  (crit = +103.0 C)                  
temp2:       +56.0 C  (crit = +120.0 C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +66.4 C  (high = +70.0 C)  I'm running an up-to-date version of Maverick on a 5 year old Compaq. I only recently noticed the increased temperature.

Any help greatly appreciated!

---

### Post by r-senior on 2011-04-16
First thing I would check would be whether your case is full of dust, heatsinks clogged, vents blocked, etc.

---

### Post by Ron Carson on 2011-04-16
Did that before. Inside is clean. Exhaust port is free and no dust on "heat exchanger"  Part of my problem is I don't really understand what is being reported.

What is "k10temp-pci-00c3"?

---

### Post by no2498 on 2011-04-16
install htop to see what is running
type it in a terminalclick enter it tells you how to install it
after installed type htop click enter
also comes up in applications system tools

---

### Post by 5149.5 on 2011-04-16
> **Ron Carson said:**
> What is "k10temp-pci-00c3"?

The following command might give a clue:


```
sudo lspci | grep -i c3
```

---

### Post by Ron Carson on 2011-04-16
> **no2498 said:**
> install htop to see what is running
type it in a terminalclick enter it tells you how to install it
after installed type htop click enter
also comes up in applications system tools

I intstalled Htop. Looking at the results I don't see anything abnormal, not that I know what I'm looking at... 

Suggestions?

---

### Post by Ron Carson on 2011-04-16
> **5149.5 said:**
> The following command might give a clue:


```
sudo lspci | grep -i c3
```

The command doesn't return anything....

---

### Post by no2498 on 2011-04-17
did you type in your pass word you dont see anything as you type it just click enter

---


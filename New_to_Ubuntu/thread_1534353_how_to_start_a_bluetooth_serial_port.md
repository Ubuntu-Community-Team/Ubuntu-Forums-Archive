---
title: "how to start a bluetooth serial port?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by outleradam on 2010-07-19
I have a bluetooth serial port which I would like started every time I pair a device.   How do I do this?  I have a script which I made that requires sudo access to start:

```
 rfcomm connect 0 
stty -f rfcomm0 speed 9600
```The problem is that it requires SOO many checks that the actual script is very long. 

There must be a system way to start a com port via bluetooth.

---


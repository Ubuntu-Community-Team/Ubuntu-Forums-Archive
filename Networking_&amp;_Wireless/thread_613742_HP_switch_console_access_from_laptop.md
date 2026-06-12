---
title: "HP switch console access from laptop"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by ktenney on 2007-11-15
Howdy,

I want to be able to configure HP switches via out of band
console connection with my Thinkpad R50e

The laptop has no serial port, so I am using a USB->Serial 
cable which seems to be recognized, existing as 
/dev/ttyUSB0

I would appreciate any direction on connecting to the HP
switch (2626) via this device.

What sort of application is required?
How do I configure the application to use the 
USB->DB9 at /dev/ttyUSB0?

Thanks,
Kent

---

### Post by ktenney on 2007-11-16
Solved.

I had been trying minicom unsuccessfully, seems I was just
being impatient. After configuring minicom correctly, I was unable
to connect until saving the config, stopping minicom and restarting 
it with the correct config file, The file looks like:

# Machine-generated file - use "minicom -s" to change parameters.
pu port             /dev/ttyUSB0
pu backspace        BS
pu rtscts           No 
pu xonxoff          Yes
pu localecho        Yes

---


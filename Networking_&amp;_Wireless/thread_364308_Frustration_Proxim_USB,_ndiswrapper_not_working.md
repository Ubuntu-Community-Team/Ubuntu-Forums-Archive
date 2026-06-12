---
title: "Frustration: Proxim USB, ndiswrapper not working"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by phalanxjc on 2007-02-18
So, I'm new to Ubuntu and trying to get wireless working on my fiance's computer.
Running Edgy with the Proxim Orinoco 11b USB.
Installed ndiswrapper and downloaded the driver.
lsusb reports its plugged in and ndiswrapper says driver present, hardware present.
Typed in sudo modprobe ndiswrapper.
But, nothing shows up on ifconfig or in the Admin/Networking menu!
What am I doing wrong?  I'm banging my head on this one.](*,)

---

### Post by teaker1s on 2007-02-18
install these
[COLOR="Red"]ndiswrapper-common
ndiswrapper-utils-1.9[/COLOR]

and try modprobe again

---

### Post by phalanxjc on 2007-02-18
Thanks, I will try that.  I had installed 1.8.

---

### Post by phalanxjc on 2007-02-19
Installed 1.9 and worked like a charm.
'preciate it teaker

---

### Post by teaker1s on 2007-02-19
:guitar: :guitar: :guitar: result

---


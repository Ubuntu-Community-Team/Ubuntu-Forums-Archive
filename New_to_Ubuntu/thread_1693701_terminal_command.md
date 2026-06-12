---
title: "terminal command"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by skt.diaz on 2011-02-23
i was trying to make ubuntu(maverick) detect my evdo modem. my modems instruction manual said somethng about ejecting an icon which would appear on d desktop. no icon appeard. so aftr many google searches i accidentaly came across a command -- eject /dev/sr1            
what does this command mean? modem got detected and is workin now

---

### Post by aeiah on 2011-02-23
it ejects the device called sr1, quite simply.

i cant tell you what that is on your system for sure, but since sr0 is usually your cd/dvd drive, im guessing its the portion of your usb modem that is pretending to be an optical drive. a lot of them do this to carry drivers and software on the device its self.

you need to eject it for the system to recognise the device as a modem, and not as a pseudo optical device (since it is both but cant be both at the same time)

---

### Post by howefield on 2011-02-23
eject is usually used to eject removable media.

For more info, type man eject into a terminal.

---

### Post by skt.diaz on 2011-02-23
thnx. took me ages to get my modem workin

---

### Post by skt.diaz on 2011-02-23
how would i know what device to eject if i use a new modem?

---


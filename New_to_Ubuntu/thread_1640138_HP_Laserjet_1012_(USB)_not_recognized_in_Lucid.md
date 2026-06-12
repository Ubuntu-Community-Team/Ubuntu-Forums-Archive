---
title: "HP Laserjet 1012 (USB) not recognized in Lucid"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by jbocean on 2010-12-07
I have been running 10.04 since spring and was able to print just fine w/ an old HP Laserjet 6-L. But I had to move that printer to another computer w/ Win-7.  I tried to add to my Ubuntu-only computer (Dell Dimension 4550) 
an HP Laserjet 1012 (USB) .

Ubuntu does not even 'see' the printer when I choose Printing from the System menu. I checked & re-checked that everything is connected correctly.

What should I do next?

Thanks!

---

### Post by LADmaticCA on 2010-12-07
It appears you need to download the HPLIP drivers from HP...

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

After you select your distro and printer model it will give you installation instructions.

---

### Post by rburkartjo on 2010-12-07
jb or you could install HPLIP toolbox from the ubuntu software center. follow the instructions and it should recognize your printer. i had to use it. should work fine.

---

### Post by jbocean on 2010-12-07
I installed the HPLIP from the software center, rebooted and printer still not recognized. Also I tried plugging the printer into a different USB port w/ no success. Tomorrow I will uninstall HPLIP from the Software Center and try an HPLIP install via the web. If the HP drivers software doesn't work then I wonder if the problem is in the USB ports being mounted and recognized.

Thanks
J

---

### Post by rburkartjo on 2010-12-10
jb did you go to the option for  that has HPLIB search for your printer driver. if so it could be a problem with the  usb port. something if i have too many devices using one port things dont work

---

### Post by khelben1979 on 2010-12-11
Have you considered upgrading to Ubuntu 10.10 to see if the problem gets fixed? According to [hplip webpage]("http://www.openprinting.org/driver/hplip") it should be working.

I got an HP 1022 which works excellent with the old Debian Lenny! Linux kernel which is used is 2.6.26. Your distribution uses a newer 2.6.32. I know it's not the same model, but since it's working over here, I wouldn't recommend you choose to dismiss HP because of your present troubles.

Just checked the wikipedia page and it seems like [this]("http://en.wikipedia.org/wiki/HP_LaserJet_1012") is your printer b.t.w.

---

### Post by quad3d@work on 2010-12-26
I had issues with Lucid as well. It just won't work.

Running Linux Mint 10 (based on 10.10) and HPLIP package was installed by default. Laserjet 1012 works like a champ!

---


---
title: "Installing driver for Epson Stylus Nx415 al l in  one printer"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by beew on 2011-05-27
Hi,

Picked up a Epson Stylus Nx415 all in one printer from the street and it appears to be in good working order. I went to the website and happily found that  it actually has Linux drivers in .debs. But when I tried to install the first .deb file I get the error message
> Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)



I checked Synaptic and it showed that libltdl7 is installed. How should I proceed?

Please help, thanks.

I am using Ubuntu 10.10

---

### Post by beew on 2011-05-27
Should I make a symlink?

---

### Post by beew on 2011-05-28
Hello?? Anyone?

---

### Post by Pand5461 on 2011-05-28
Maybe you could try this ```
sudo dpkg -i --ignore-depends=libltdl3 your-driver-here
``` and see if it works.

---

### Post by beew on 2011-05-29
Bump!

---

### Post by Mark Phelps on 2011-05-31
> **beew said:**
> Hi,

Picked up a Epson Stylus Nx415 all in one printer from the street and it appears to be in good working order. I went to the website and happily found that  it actually has Linux drivers in .debs. But when I tried to install the first .deb file I get the error message


I checked Synaptic and it showed that libltdl7 is installed. How should I proceed?

Please help, thanks.

I am using Ubuntu 10.10

Those are likely different libraries, so you need to go into Synaptic and see if there are entries for the "...tdl3" library.

---

### Post by beew on 2011-05-31
> **Mark Phelps said:**
> Those are likely different libraries, so you need to go into Synaptic and see if there are entries for the "...tdl3" library.

There is only one which is libltdl7.

---

### Post by cjazz on 2011-05-31
beew,

I don't know which driver you're trying to install so I can't help you there. The good news is that the trusty OpenPrinting database [here]("http://www.openprinting.org/printer/Epson/Epson-Stylus_NX415") says the NX415 works perfectly under Linux. It gives two possible drivers -- one recommended (epson-espcr) and one additional (gutenprint, which can be installed via synaptic.) Is one of these the driver you are attempting to install?

---

### Post by beew on 2011-05-31
> **cjazz said:**
> beew,

I don't know which driver you're trying to install so I can't help you there. The good news is that the trusty OpenPrinting database [here]("http://www.openprinting.org/printer/Epson/Epson-Stylus_NX415") says the NX415 works perfectly under Linux. It gives two possible drivers -- one recommended (epson-espcr) and one additional (gutenprint, which can be installed via synaptic.) Is one of these the driver you are attempting to install?

Actually the printer (don't know about scanner) is recognized by Natty. As soon as it was plugged in jockey (Additional Drivers) offered to install the driver. Haven't tested whether it works though. With Maverick however the device was not picked up, it was detected by natulis and that was it, so I did some googling and found a sites with  the Linux driver, I tried to link it here but the link has just turned into Japanese for some reasons. I have to recheck the site and post back later.

---


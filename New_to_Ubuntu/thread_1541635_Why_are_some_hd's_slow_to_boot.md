---
title: "Why are some hd's slow to boot?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by DonaldJ on 2010-07-29
This Seagate hd, 40-gigs, boots up fast...  The desktop shows, then in a couple seconds it's ready..  but these other brand hd's get to the desktop, and take about half a minute to a minute to finally show the desktop icons and background pix...  Why are some hd's so slow to boot up Ubuntu 910?.. Is there a code or software that fixes this glitch?..

---

### Post by SpockVulcan on 2010-08-02
Its not Ubuntu's fault. It can be caused my a number of things, slow RPM, not much cache, or even a drive that is failing.

---

### Post by LowSky on 2010-08-02
Depends on the hardware. Hard drive size doesnt do anything for performance.


What really matters is the type of connection to the Motherboard and the hard drives cache, and the speed of the RAM and finally the Processor.

A hard drives in laptops are ofter much slower that desktop machines. Even today a laptop can have a drive that is only rated at 4200 RPM, some desktops still have drives that are only 5400 RPM, and its even become common for people to buy slower drives so they are quieter and use less energy.

My Desktop has a 10,000 RPM 74GB WD Raptor HD (SATA 1). It was the fastest thing out there a few years back, I'm use it now for Ubuntu. But now I have a WD 7200 RPM Caviar Black drive and it uses SATA 2 and has 32MB of Cache which is 24 more than the Raptor. It  might spin a bit slower but it seems to be faster for day to day things.

---

### Post by DonaldJ on 2010-08-02
Now it's clear that my obsolete slow machines and hd's are the fault...

Is there anything one can do to speed-up existing Ubuntu and hardware in an old tower?..

---

### Post by soldier1st on 2010-08-03
anything less than 7200RPM will be very slow and different HDD's have different atributes like latency and access time and the less access time the faster it can seek data and cache can help but connector type can play a difference, like a pata drive and a sata drive. the pata drive has an 80 pin connector and it runs in pararell(data flow is like data is going in both directions so that is very slow and it and it has to compete for bandwith) but for sata the connector is shorter and it uses a serial connection) here is a site for what you seek [http://www.directron.com/patasata.html](http://www.directron.com/patasata.html)

---

### Post by Mark Phelps on 2010-08-04
While rotation speed MAY slow down the drive, a key determinant of drive responsiveness is the controller type (PATA vs SATA) and the transfer speeds.  

Older PATA drives, although using serial connectors, had transfer speeds of 100Mb/s and 133 MB/s (that's Megabits per second).

In contrast, even the slowest SATA drives have transfer speeds of 1.5Gb/s (that's Gigabits vs. Megabits for PATA).  Current SATA drives typically have speeds of 3Gb/s and the newer drives coming out now (known as SATA 3.0) have speeds of 6Gb/s.

So basically, SATA is always going to be faster than PATA.

---

### Post by DonaldJ on 2010-08-04
WoW!..  that's a lot of wicked data on computer speed...

Which faster hd's will work in an old Compaq Presario?..

---


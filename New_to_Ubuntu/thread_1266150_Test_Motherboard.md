---
title: "Test Motherboard"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by expatCM on 2009-09-14
Does anyone know of a utility to test a motherboard?  I think Windows used to have something called MBM but Ubuntu ....  well I have not read of anyone else asking .........

I have an ASUS M3A78.  It has six SATA ports, all in use.  What I have noticed is that the drives plugged into SATA ports 2 and 3 randomly disappear.  

I get the idea that this is a hardware issue and I am down to thinking of only two things.  One that the motherboard has an issue and the other that the PSU is delivering insufficient power.

The PSU I rule out since the problem is associated with drives on only these two ports.  I may of course be mistaken since the power to these drives is at the end of the line. 

All the hard drives perform perfectly when mounted in an external USB housing.  I have also changed the SATA cables just to eliminate a weak link.

So I would like to run a diagnostic on the motherboard.  Has anyone heard of any suitable application or have any other ideas?

---

### Post by LowSky on 2009-09-14
6 hard drives? How many watts is your power supply?

I would say you need at least a 600Watts supply, but closer to 800-1000 if you're using a high-end graphics card

---

### Post by expatCM on 2009-09-14
erk ....  are you sure .....  the PSU is only 500W....  but I did check before building this and 500W is supposed to allow a margin of comfort ... 

The machine spec is 

M3A78 motherboard 
AMD 940 Athlon 64
2GB RAM (one strip)
ASUS Xonar D2X sound card
GeForce 8400 GS graphics
5 SATA HDD
1 SATA DVD RW

---

### Post by LowSky on 2009-09-15
by the way 940 model number is for a PHENOM II, not an ATHLON 64


check your BIOS and see the voltages being supplied to the motherboard. They should all be very close to the norms with little fluctuation. Asus MB should do this in realtime.

I believe your power supply is barely giving enough juice. Most Power supplies with 6 SATA style connectors are rated at about 600Watts
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010090058+1131310111+1788248895+1409730089&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=58&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010090058+1131310111+1788248895+1409730089&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=58&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

Are you running a RAID, it just dawned on me that some hard drives are not built to perform in RAID's as they power down to save energy. Its the reason companies like WD and Samsung make RAID capable hard drives

---

### Post by expatCM on 2009-09-16
Well done LowSky ...  I think you are probably correct. Thank you for your suggestions .... 

I dropped a 650W power supply in and tested last night.  No problems at all.  I am testing the old power supply on a machine with fewer devices and so far that also have no problems.

When I took out the old power supply I found a broken wire on one of the SATA connectors, this would not explain the whole problem but perhaps the intermittent appearance of one drive.  Never seen a broken wire on a PSU before .....

But there is a BIG lesson to learn here.  If I run the hardware spec. through one of the many power supply calculators you will find that the wattage I used was totally acceptable.

Perhaps what is missing is that the calculators do not take account of the power loading on individual rails.  So if you stack a row of SATA devices on two 12v rails, in my case that is too much.  Increase the wattage and the power on the rails appears to be increased. Well that is my theory today ............

---


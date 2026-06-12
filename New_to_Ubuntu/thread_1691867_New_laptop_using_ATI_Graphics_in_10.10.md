---
title: "New laptop using ATI Graphics in 10.10"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by bob brazie on 2011-02-20
I am looking at a new laptop that is using the 512MB ATI Mobility Radeon HD 5470 DDR3 switchable graphics card. 

I just looked throug the new dada base at this site:

[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)

and do not see it mentioned anywhere. Does someone know if this is a supported or working card in Ubuntu 10.10? Or some other place I might find some information before ordering this new machine.

Thanks in advance. Bob.

---

### Post by cariboo on 2011-02-20
This is my personal opinion, due to AMD/ATI's inability to release updated drivers in a timely fashion, they are always 2 -3 months behind Intel and Nvidia, I wouldn't at this time purchase anything with ATI graphics.

---

### Post by adduds on 2011-02-28
> **bob brazie said:**
> I am looking at a new laptop that is using the 512MB ATI Mobility Radeon HD 5470 DDR3 switchable graphics card. 

I just looked throug the new dada base at this site:

[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)

and do not see it mentioned anywhere. Does someone know if this is a supported or working card in Ubuntu 10.10? Or some other place I might find some information before ordering this new machine.

Thanks in advance. Bob.

to get fglrx drivers (proprietary amd/ati drivers) to work in ubuntu i had to set graphics to discrete rather than switchable in bios

---

### Post by misterbiskits on 2011-03-01
This card appears to be supported.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
In the fields, specify

[LIST]
[*]Notebook Graphics
[*]Mobility Radeon Series
[*]Mobility Radeon HD5xxx Series
[*]Linux x86
[/LIST]
Clicking "Display Results" [brings you ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")to the linux driver for this card.

If you need it, manual installation instructions [are here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually").

Hope that helps.

---

### Post by mastablasta on 2011-03-01
> **cariboo907 said:**
> This is my personal opinion, due to AMD/ATI's inability to release updated drivers in a timely fashion, they are always 2 -3 months behind Intel and Nvidia, I wouldn't at this time purchase anything with ATI graphics.
 
 
what do you mean? as i know they worked with cannonical to release the drivers at same time as Ubuntu 10.10. What more could we want?
 
And i dont' think 5x series is the problematic one. It's the latest 6x series that has issues.
 
oh and as i knwo there is not much choice on notebooks these days. it's either ATi or Intel. As i read certain nvidia chips have issues and actually 0 support for linux.

---

### Post by misterbiskits on 2011-03-06
> **cariboo907 said:**
> This is my personal opinion, due to AMD/ATI's inability to release updated drivers in a timely fashion, they are always 2 -3 months behind Intel and Nvidia, I wouldn't at this time purchase anything with ATI graphics.

I just installed Lucid on my laptop which has a 4250 onboard.  Installing the proprietary ati driver via system>administration>hardware drivers _completely butchered_ my display with artifacts and horizontal lines everywhere.  
Reinstalling Lucid and using the manual installation method quoted above (with correction for the 11.2 version of the driver) has my display working fine with the ati driver activated.
I think this thread has made it pretty clear, several times, that ATI is not the problem, but rather it is Ubuntu which doesn't properly support ATI's contribution to this OS.

---


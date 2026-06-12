---
title: "Dell 1450 minicpi card on 7.04.."
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by LVDave on 2007-06-23
Am installing Ubuntu 7.04 on a Dell Inspiron 2200, with a Dell 1450 802.11a/b/g minipci card. All works swimmingly except for the wireless.. Reading about ndiswrapper, I've determined thats the only way to get the 1450 working.. Have read the ndiswrapper pages, installed ndiswrapper on the system, it seems to be working fine.. However, now to the problem.. I downloaded the Dell windows driver package for this card, as suggested on the ndiswrapper webpage, and ran it on a windows machine, and obtained the data2.cab file that the ndiswrapper website suggested, and tried a cabextract on the 2200 to get the bcmwl5a.inf and bcmwl5a.sys to install via ndiswrapper.. The cabextract reports this cabinet file is an installshield cabinet, and suggests using an unshield util, when thats tried, it reports data2.cab is not an installshield file.. Since I suspect Dell supports this card on Ubuntu, are these two files available anywhere else, without the need to extract from a cabinet???

Tried posting this on the Dell Linux forum, got bupkis replies... 

Dave

---

### Post by Ayuthia on 2007-06-25
Can you post the link to the website that mentions the .cab file?  I took a glance at the ndiswrapper site for your card and it shows this as the link for your drivers:

Driver: [ftp://ftp.dell.com/network/R90501.EXE](ftp://ftp.dell.com/network/R90501.EXE)

---

### Post by kevdog on 2007-06-25
If you have a windows machine, can you just extract the drivers that way?

---

### Post by chili555 on 2007-06-25
I downloaded the file Ayuthia refers to, did *unzip R90501.EXE* and got, in part:```
Archive:  R90501.EXE
  inflating: AegisI2.exe             
  inflating: AegisI5.exe             
  inflating: bcm43xx.cat             
 extracting: bcm43xxa.cat            
  inflating: BCMLogon.dll            
  [B]inflating: bcmwl5.inf              
  inflating: bcmwl5.sys[/B]              
  inflating: bcmwl5a.inf             
  inflating: bcmwlcpl.cpl            
  inflating: bcmwld2k.exe            
  inflating: bcmwlhlp.chm  
```That should do it!

---


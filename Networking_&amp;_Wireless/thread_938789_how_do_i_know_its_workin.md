---
title: "how do i know its workin ?"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by spydergt on 2008-10-05
i also have a 2wire a/b wifi card thats branded ,  it shows up as orinico underneath pccardctl ls  and lspci shows agere systems lt winmodem and somewherez else i got hermes for it , 

so my question is is with ubuntu 8.04 hardy , how do i know its implamented the right driver that i want to use for aircrack-ng / airsnort  from the kernel 2.6  ?  and must i do anything to this card ?  

if you could show me a link to something , that would be awesome .. ow and im gonna need you to come in on sunday and finish up those tps reports that you didnt finish ...  mmmmmKkkaaayy.... hahaha ... lunacy ...

---

### Post by pytheas22 on 2008-10-05
The easiest way to find out whether your driver will support airodump/airsnort is just to try to start the program.  If monitor mode is not working, you'll get an error message.  A lot of the drivers that come default with Ubuntu don't support monitor mode, but if you patch their source code and recompile them, they will work.

If monitor mode doesn't work out-of-the-box for you, the aircrack website has a [good outline]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=fbd1fcd32650025f3ffd5c9c9c67448a") of how to get the proper drivers installed for monitor-mode support for each chipset.  I think that Hermes chipsets don't support injection, but you can sniff (this means that it will take you a lot longer to crack a WEP key, but it can be done if you have patience).

---


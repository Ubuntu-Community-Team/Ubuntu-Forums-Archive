---
title: "CUPS issue with printing to remote CUPS server raw queue"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by Burt_Bicksler on 2016-06-07
Hi,

I've been trying to track down the source of a problem I'm having trying to print to the Brother FAX-2820 printer that I have connected to a RPi print server.

I was able to get this working from Ubuntu 12.04 LTS but have not had any luck getting it to work with Ubuntu 14.04 or newer.

Since Brother's wrapper / driver is only for Intel processors I set up the CUPS print server with a RAW queue on the RPi and then installed the Brother CUPS wrapper on the Ubuntu 12.04 machine.

I am able to print just fine from the 12.04 machine to the Brother on the RPi.

But when I try to print from the 14.04 machine to the RPi all I get are blank pages coming out of the printer.  If I move the printer directly to the 14.04 machine connected via USB it prints just fine.

So it is an issue with what is being sent by CUPS on the 14.04 machine to the RPi.  But I'm not sure where to look for the problem.

I have compared the CUPS printer.conf between the working 12.04 install and the 14.04 and everything appears to be the same including the URI.

So I'm looking for some pointers on how to isolate and correct the problem.  

Has anyone run into a similar problem, and if so how did you resolve it?

Thanks,
Burt

---

### Post by Burt_Bicksler on 2016-06-07
Some additional information.&nbsp; I also have Samba set up on the RPi to allow our Windows computer to print to the Brother, and a test from Windows to the Brother via RPi using Samba prints just fine, so it is an issue with getting the Ubuntu 14.04 installation to send the proper data to the RAW queue on the RPi.

---


---
title: "Printer connectivity issue - but WIFI stable after 16.04 install"
date: 2016-12-22
forum: Networking &amp; Wireless
---

### Post by rocky3 on 2016-12-22
Wireless Printer connectivity problem - The only way I can print is when directly connected via USB.   I am running Ubuntu 16.04 on an HP DV7 laptop.  It won't print either way, whether connected wireless or via  wired cable LAN.  I used the "install tool" on the Brother web site, selected "linix" "Deb" flavor.  They gave me the opportunity to enter my IP address 192.168.3.105.  Even though I can't ping the that address, somehow, it found and appeared to load the driver:

lpadmin -p HL2270DW -v socket://192.168.3.105 -E

Then, it gave me the opportunity to print a test page.  . . . . that DID NOT WORK.

I have attached my wireless output below just in case it may have information, i.e. IFCONFIG,  that may help uncover this mystery.

[http://paste.ubuntu.com/23668192/](http://paste.ubuntu.com/23668192/)

Any assistance you  could provide would be greatly appreciated!!

SOLVED 
1) in the command line I typed [fping -g 192.168.3.0/24]  This resulted in [192.168.3.181 is alive].  Then I went to my windows machine and typed in [ping -a 192.168.3.181].  This resulted in BRW . . . . FOD] designating that 181 was associated with my BROTHER printer.
2) In went to the brother site and used the linix installer tool (DEB).  Then I followed the instructions on the installer menu.  When it came to URI I selected IP address (#12).  Then I inserted the 192.168.3.181 and it printed the test page!!!!! 

NOTE:  I was unable to print because I was guessing at my Printer IP address and the linix installer tool took a bad address and faked everything looked like it would work.  But lesson learned. . . I needed to find out exactly what my IP address was before executing the linix installer tool on the brother site.

Rocky

---

### Post by rocky3 on 2016-12-29
Bump

---

### Post by rocky3 on 2016-12-31
Bump

---

### Post by praseodym on 2016-12-31
Did you set a fixed IP for the printer in your router?

---

### Post by rocky3 on 2017-01-02
[SIZE=3]**Praseodym,  Thanks for reading my post at this busy time of the year as families reconnect.  In answer to your question. . . . .yes.  Dell downloaded the printer driver to accommodate my windows 7 dell machine.  In the process, they told me my printer IP address was static and that it was  192.168.3.105.  However, when I access my router and look at the active wireless client table, I don't see IP addresses.  All I see is two MAC addresses. . . . and it stands to reason, I would need three (2 laptops and one printer) . . .. . nevertheless, I can print fine from the DELL. **[/SIZE]

---

### Post by rocky3 on 2017-01-07
Bump

---


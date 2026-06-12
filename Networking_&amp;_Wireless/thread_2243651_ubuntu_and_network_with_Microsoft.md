---
title: "ubuntu and network with Microsoft"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by cemenc2 on 2014-09-10
Hello guys and gals,

In my work environment, we use microsoft OS workstations and servers. 
However I also like to use our older (slower) workstations to let users have access to our network drives, intranet pages etc. 
So, I like to know is it possible to use ubuntu in microsoft windows server environment? 
this will reuqire the user to login to our network and get network drives mapped, and possibly get the intranethome pages
lets not forget network printers. 

thanks
Jamal

---

### Post by Dragonbite on 2014-09-10
For Linux to access Windows Shared directories, you want to look into Samba (samba-client), though I think Ubuntu comes with that installed (I've had to install it myself with other distributions).

For accessing Intranet pages initially, you could us the server's (internal) IP address and put that in the URL.

Things like accessing an Enterprise server (like MS SQL Server) may work, but less confident about that (especially with MS SQL Server).  LibreOffice Base is the closest equivalent to MS Access and may be able to connect to a MS SQL Server, but I haven't tried.

Network printers should work, once you get the drivers.  Not so sure if the networked printers are Copier/printers or multi-function (includes scanning). Printing should not be an issue (Linux drivers providing.. HP is good, Cannon and Brother are questionable), scanning and other features will be a little more difficult unless the manufacturer has Linux drivers for it all.  You can try Simple Scan and see if it can "see" or you can set it up with the Network Copiers.

It will be some trial-and-error to make it work in YOUR environment.  I am interested in hearing what you find and how it goes.

Good luck!

---


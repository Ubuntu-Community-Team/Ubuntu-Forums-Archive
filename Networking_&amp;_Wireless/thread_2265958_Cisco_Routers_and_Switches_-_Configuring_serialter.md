---
title: "Cisco Routers and Switches - Configuring serial\terminal sessions"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by diddy2 on 2015-02-18
Hello, 

Does anyone here configure Cisco switches or routers? When configuring a router out of the box you need to 
establish a serial\ terminal session. Trying to use Putty but it keeps locking up. Also I need to use "gksudo putty" from
the terminal each time to open. Minicom is not that much better. 

I finally got everything working with Ubuntu on my laptop. My only down fall is not being able to program a router\switch with 
ease. I do not want to revert back to Windows because Putty does not work. Anyone know any tricks or better ways?


(I know SSH is more secure. When configuring out of the box you need a serial\terminal session.
After the router is setup. SSH is used to connect once connected to the network)

Thank you, 

diddy

---

### Post by tripp98 on 2015-02-22
Use gtkterm.  Works great.  

once installed use sudo gtkterm to give access to serial ports.  It works with usb to serial converters and the new cisco interface.

---


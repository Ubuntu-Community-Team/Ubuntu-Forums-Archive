---
title: "difficiulty printing to networked printers"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by VCSkier on 2007-11-28
My university has print stations all over campus, so windows laptop users can send print jobs from anywhere they are connected to the network (connection requires authentication), and then "release" the print job at any of the print stations by entering their username and password.  It is incredibly convenient, but I can't figure out how to get it running on linux.

There are details posted on my school's site [here]("http://www.liberty.edu/informationservices/customerservice/resnet/index.cfm?PID=11107") for manual setup on a Mac, and it makes mention of SAMBA, so I installed SAMBA and GSAMBAD, but it all seems a bit complicated for me.  Any advice?  Thanks.

---

### Post by oldsoundguy on 2007-11-28
Don't know if this will help on an Apple, but all you really have to do once Samba is installed is go the the printer installation utility and select "install via samba" and follow the yellow brick road. (do the search).  Then install it. 
 I have a home network consisting of 2 XP machines, a 2003 Win PDA and 2 Gutsy machines (total of 3 are wireless).  Boxes are in different locations and some Windows boxes have hard wired printers and one Linux box has a hard wired printer (a total of 5 printers).  I can access any and all from any and all.  It DOES work (and the default drivers are sufficient drivers for most.)(except an AVERY label printer .. still awaiting a driver! LOL)

---

### Post by timcredible on 2007-11-28
where i work, they have networked printers that require you to print via a windows print server.  to do that, i **don't** install samba, i just go to System->Printing->New Printer->Windows printer via SAMBA, point to the print server and queue (like \\printserva\printer115) and checkmark the box for authentication required.  if you haven't tried that, give it a shot.

---


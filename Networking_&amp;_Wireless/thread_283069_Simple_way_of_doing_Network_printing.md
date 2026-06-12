---
title: "Simple way of doing Network printing?"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by cocotu on 2006-10-23
I have search in many places about being able to print to a network printer. I just don't see some clear instructions on how to do this. Here at work we are testing a PIII machine using Xubuntu, it works fine. We are trying to print from it using a network printer via TCP/IP. What do I need to do, install, configure?? I'm confused. We work for a non-profit organization so we are looking for options for a network without Windows, but we are getting frustrated already....

Thanks](*,)

---

### Post by fritz_monroe on 2006-10-23
Set up CUPS to print as an lpd device.  I just set up my home systems to print to a NetGear print server using [this page]("http://aplawrence.com/Linux/netgearcups.html").  The page is specifically about the NetGear print server, but I would think it's pretty close to the same procedure.

---

### Post by cocotu on 2006-10-24
I have CUPS installed, I want to know how to configure this network printer. I in localhost:631 and I set up the Device URI: ipp://x.x.x.x:631/ipp/ and I tried [http://x.x.x.x/ipp/](http://x.x.x.x/ipp/) when I go to print a test page I get around 20 pages with little simbols at the top of the page. Which would be the correct Device URI for this network printer(HP LaserJet4250n) in windows we just need to input the IP address and we are printing! How can I do that in Linux?? Thanks

---


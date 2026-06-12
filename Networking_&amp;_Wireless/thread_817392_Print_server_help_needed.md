---
title: "Print server help needed"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by dave_didlydodo on 2008-06-03
I have a hardware print server with fixed IP address on my (wired) network. How do I set up printing using it in Ubuntu (8.04)? I have the correct printer drivers and I know it supports LPR and IPP.

This is a follow-up to a post I made a couple of days ago, when I mentioned the type of server (Edimax PS-1206MF). No-one responded, perhaps because no-one didn't have that type of server. So is there any guidance for small hardware print servers generally?

---

### Post by the4thamigo_uk on 2009-09-26
I had the same problem and I have found a solution without the need to install any drivers.

(1) Open System->Administration->Printing
(2) On the 'Printer Configuration' window click New->Printer
(3) On the 'New Printer' window expand Network Printer->LPD/LPR Host or Printer
(4) Type the ip address into the 'Host' field
(5) Type 'lpt1' into the 'Queue' field Click Forward and wait
(6) On the 'Choose drivers' page ensure 'Select printer from database' is selected and find your printer in the list and click Forward

hope this helps...

---


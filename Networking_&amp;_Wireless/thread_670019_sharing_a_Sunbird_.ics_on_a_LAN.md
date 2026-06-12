---
title: "sharing a Sunbird .ics on a LAN"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by eadwacer on 2008-01-17
I have a household LAN, with one each Win2K, XP, and Ubuntu Feisty PCs, plus a NAS drive. I'd like to run Sunbird as a shared calendar app, and have put OurCalendar.ics on the NAS. Sunbird on the 2K box can see it. Sunbird on the Ubuntu box can't. As an aside, my Nautilus file manager sees the NAS as a smb on a Windows Workgroup, and has no trouble showing me myNAS/Shared Files/Calendar/OurCalendar.ics.

Nautilus says the address of the file is: 
smb://myNAS/Shared%20Files/Calendar/OurCalendar.ics

but if I tell Sunbird to Subscribe to Remote Calendar usig that address, it goes through all the motions, but doesn't mount the calendar file in the panel.

I have checked the forums, and there's stuff about WebDav (I don't want web access, or a server), and about getting Ubuntu to see a Windows network (it does that now), but I can't find an answer to my specific problem. 

I'm sure it's something simple, but I'm not sure if it's a Sunbird issue or a Ubuntu issue, so I"m starting here.

Update: still no luck getting it to work. When I look at the Error Console, I see this error message:

Error: [Exception... "Component returned failure code: 0x804b0012 [nsIIOService.newChannelFromURI]"  nsresult: "0x804b0012 (<unknown>)"  location: "JS frame :: file:///opt/sunbird/components/calICSCalendar.js :: anonymous :: line 161"  data: no]
Source File: file:///opt/sunbird/components/calICSCalendar.js
Line: 161

---


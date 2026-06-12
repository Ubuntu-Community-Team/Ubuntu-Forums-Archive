---
title: "[SOLVED] Windows Shared Printer not working under Hardy"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Kralizec on 2008-05-07
I made a minor post in another thread about this, but thought it might be prudent to post a more detailed report. I have a XP desktop computer and my Ubuntu laptop on my network. In Gutsy, I was easily able to connect to and print from the shared printer on the XP machine. However, after upgrading to Hardy, for some reason all of my printer GUI software was removed from System->Administration so I had to reinstall it manually. The Add Printer wizard does see that the print share is available, but for some reason won't let me connect to it. I put in all the network data and the correct username for the XP machine, and try to print a test page and it spits out this error: "Printing to 'DeskJet-970C' failed with error code: 1286
is the printer paused ?" The printer is not paused. Then the next time I open the printer properties (because it does add the printer to my list) and go to connection, it has changed the connection from a SMB connection to a IPP connection on file:/dev/null, so my print jobs are going exactly nowhere. Any help would be very greatly appreciated.

BTW: A local printer is not an option right now either.

---

### Post by Kralizec on 2008-05-08
Bump. Kind of urgent.

---

### Post by Kralizec on 2008-05-14
Somehow it resolved itself. The Samba option reappeared in my printer manager.

---


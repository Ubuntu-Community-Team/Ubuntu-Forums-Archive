---
title: "Setting up to print with Belkin F1UP0001 Print Server"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by pkc2 on 2008-01-20
Hi, Total Newbie. Trying Ubuntu 7.10 on my desktop. Currently have a lan setup with 3 computers on it and a print server which allows my family to print to another desktop (wired) and my laptop (wireless). Unable to get Ubuntu to print via the print server to my HP Deskjet 970Cxi printer. I've read other messages about this and taken the advice given and tried installing a new printer as AppSocket/HP JetDirect with no joy (although the lan light flashes on the print server when I send a test page to the printer that's about as far as it gets). I've also edited my cups configuration file with similar lack of results.
I know my print server is at 192.168.2.4 and I can load its setup page into my browser. If I connect the printer directly to my computer Ubuntu finds it immediately and sets it up correctly. 
Hope I've supplied enough info and that someone can help
Thanks
Peter :(

---

### Post by pkc2 on 2008-01-20
Solved this problem. It was dead simple. After setting it up as HP/JetDirect I was then putting the URL of the printer as [http://192.168.2.4](http://192.168.2.4) instead of just 192.168.2.4. 
Silly mistake :)

---

### Post by snapper737 on 2008-01-28
Used HP JetDirect as above (with just the IP address)  but for some reason I had to change the port to 9101

---


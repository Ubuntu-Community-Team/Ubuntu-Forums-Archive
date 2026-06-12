---
title: "Print from Ubuntu to Vista"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Spccowboy on 2007-09-19
I'm trying to print from an Ubuntu laptop over a wireless network to a shared printer on my Vista desktop. I can't seem to find the printer through ubuntu. Thoughts?

---

### Post by Technophobia on 2007-09-19
so you goto 

1) system > admin. > printing

2) add new printer

3) select network printer > Windows Printer (SMB)

4) pick the host windows computer

5) pick model of the printer

and you get nothing under host? 

My only 2 suggestions with my limited knowledge of printers. Wait a little bit for the network to load up. Sometimes windows networking is a bit slow in finding everything on start up. I guess thats one of the reasons active directory exists for windows. And if you have a firewall up shut it down or give if access to printer sharing. Hope that helps a little.

---

### Post by Spccowboy on 2007-09-19
Well I had tried that before but thought I'd give it another shot with more patience to see if the network was just being slow. That still didn't work. As it turns out the problem was even simpler. The Vista box had gone to sleep and could no longer be detected. I've set it not to sleep and found the printer with no troubles now. Thanks.

---


---
title: "tool for measuring dsl line quality?"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by ayampanggang on 2008-01-22
Anyone knows one?
I'm using ADSL service and i think it's a good idea to have a tool that can measure line quality (e.g. SNR ratio, signal strength, etc).
I think it can be quite useful when you need to troubleshoot the network at downtime.

Thank you!

---

### Post by fs3rp4 on 2008-01-22
> **ayampanggang said:**
> Anyone knows one?
I'm using ADSL service and i think it's a good idea to have a tool that can measure line quality (e.g. SNR ratio, signal strength, etc).
I think it can be quite useful when you need to troubleshoot the network at downtime.

Thank you!

Probably your ADSL modem have this tools. Did you look in status or connection menu?

---

### Post by Roger Gundberg on 2008-01-22
Have you looked at Wireshark? Formerly Ethereal. Run it as root. Go to the Add Remove programs. I hope you are more technically versed than I Good luck!

---

### Post by az on 2008-01-22
Many adsl modems don't have a user interface.

Perhaps using the pppoe package's pppoe-status command?

---

### Post by fs3rp4 on 2008-01-22
> **az said:**
> Many adsl modems don't have a user interface.

Perhaps using the pppoe package's pppoe-status command?

Are you sure? 

Every modem from D-link, Planet, Cisco, Alcatel, etc... have user interface. 

What modem do you use?

---

### Post by fs3rp4 on 2008-01-22
> **Roger Gundberg said:**
> Have you looked at Wireshark? Formerly Ethereal. Run it as root. Go to the Add Remove programs. I hope you are more technically versed than I Good luck!


Wireshark don't work with layer 1 "SNR ratio and signal strength".

---

### Post by ayampanggang on 2008-01-23
yeah, i'm looking a tool that can work on physical or atleast data link layer. ethereal don't do that i think.

i'm using zyxel modem/router and as far as i know (in the manual book) it only supports web interface. i don't know if i can access command line interface. the web interface sucks tho, doesn't have the details that i want.

thanks for the reply :)

---


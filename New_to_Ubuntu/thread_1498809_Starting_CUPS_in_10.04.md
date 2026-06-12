---
title: "Starting CUPS in 10.04"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by aa4bb on 2010-06-01
Updated from 9.10 to 10.04. I have an HP printer on my LAN.

When I tried to print, no printer showed up. Under "System>Administration>Printing", I chose "Help>Troubleshoot". It said the CUPS spooler does not appear to be running and said to go to "System>Administration>Services" and look for "cups". However, no entry for "Services" appears on my "System>Administration" menu. I'm at a dead end here.

---

### Post by fatality_uk on 2010-06-01
If you open a wqeb browser and type in this address, what comes up?
[http://localhost:631/](http://localhost:631/)

---

### Post by aa4bb on 2010-06-01
"If you open a wqeb browser and type in this address, what comes up?
[http://localhost:631/"]("http://localhost:631/")

Firefox can't establish a connection to [http://localhost:631/](http://localhost:631/)

---

### Post by aa4bb on 2010-06-01
Some little inner voice told me to run Update Manager.

When I did, it installed CUPS. Then I went to System>Administrative>Printing. It found my printer on the network and installed it. All is well.

---


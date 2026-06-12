---
title: "rhytmbox issue after unplugging ipod before unmounting"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by carrotsoup on 2010-08-12
I accidentally pulled out my iPod before unmounting [I completely forgot] and suddenly on my desktop there was a largish white box that appeared and it started shuffling through the titles of all of my songs. I had Rhythmbox open, and it stopped after a restart, but any ideas as to why it did this? I thought it was really odd and I didn't know how to terminate the process...[how to do this..?]

---

### Post by Vaphell on 2010-08-12
**killall <process_name>**
or 
**ps ux** to get the list of running processes owned by you
**kill <process_id>** (asking politely)
**kill -9 <process_id>** (nuking)

---


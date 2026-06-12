---
title: "msi wind u130 &quot;laptop critical battery&quot; problem"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Anish4 on 2010-06-18
hi i got this major problem in ubuntu 10.04. when i remove the ac power supply i get a popup saying "battery critically low" but my battery still has 1 hour remaining and is at around 60% full.

help!

---

### Post by Hukei on 2010-10-17
I got the same netbook. Just update the BIOS using FREEDOS. Grab the BIOS update at msi.com. They mention the battery meter issue there.

---

### Post by animeshmeher on 2010-11-12
Hi!

Try this, 
Press Alt-F2 and type **gconf-editor**. Press Enter. 
Navigate to **Apps -> gnome-power-manager -> general**. 
**De-select** the option **use_time_for 1f40 _policy**.

No need to restart, just close the config editor.

That should help. 

I suggestion though. Please google your problem a bit before posting . Thatll save duplicate post. :smile:
Even i had the same problem and googled for the answer.

---


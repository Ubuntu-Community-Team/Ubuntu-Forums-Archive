---
title: "meaning of line ?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by Bootycelli on 2009-09-07
Hi,
can someone tell me what means such a line ?
This is an example of what I got after using the command lines on foremost in order to recover files crushed during ubuntu installation.
Thanks


WMV err num_header_objs=1639869363 headerSize=3110745171061075150

---

### Post by Bootycelli on 2009-09-07
anyone for some help ?

---

### Post by Whiffle on 2009-09-07
We're going to need a little more context.  What command were you running?

---

### Post by Bootycelli on 2009-09-07
There are the commands 



sudo apt-get install foremost
   	

   	sudo mount /dev/sdb1 /recovery sudo mkdir /recovery/foremost
   	

   	sudo foremost -i /dev/sda -o /recovery/foremost
   	

   	sudo foremost -t avi -i /dev/sda -o /recovery/foremost
   	

   	sudo chown -R youruser:yourgroup /recovery/foremost


I found them on [http://swik.net/foremost](http://swik.net/foremost)

---


---
title: "Exactly where and how do I load the windows driver I need for my wireless???"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by gorgerax on 2008-07-22
Hey all.  nOOb here and so far, I'm having a lot of fun and everyone here is great!

I found a great "how to" that should get my Netgear WG111T USB running.  However, I am supposed to have the Netgear's install disk install a certain file *"Put in the WG111T Windows Install CD. Hit the Install Driver button.. Go to the CD, go into the ndis5 folder and install the netwg111t.inf file.  If you no longer have the CD then you can grab the drivers from the netgear website.. "*  

I lost the disk and can only find an .exe online.  I can retrieve that file from my Windows box, but exactly where and how do I install it?

I am running Ubuntu 8.04.  Thanks a bunch!

---

### Post by chalewa on 2008-07-22
[http://drivers.softpedia.com/progDownload/Netgear-WGT-Driver-Download-46609.html](http://drivers.softpedia.com/progDownload/Netgear-WGT-Driver-Download-46609.html)


that should contain the inf file that you need. 

i think that the command you need to run is 

```
sudo ndiswrapper -i /location/of/inf/
```

---

### Post by SunnyRabbiera on 2008-07-22
fair warning though, getting wireless can be a real pain in the @#$%... Not our fault mind you.

---


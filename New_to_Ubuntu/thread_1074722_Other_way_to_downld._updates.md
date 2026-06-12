---
title: "Other way to downld. updates?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-02-19
I m very tired with the speed(response) of the server for ubuntu updates. My connection is efficient for segmented download. Whenever i start update, speed first increase for 10 seconds upto 13-14 kBps then get vanished, .........is there any other way to download and install updates? Help me.........:(

---

### Post by Perfect Storm on 2009-02-19
Tried changing servers in your sourcelist?

I usually get 400-600

---

### Post by eshant_engineer on 2009-02-19
how to do that? I don't know....

---

### Post by Perfect Storm on 2009-02-19
```
sudo nano /etc/apt/sources.list
```

[ctrl]+[o] Save
[ctrl]+[x] exit

then you can edit it.

---

### Post by eshant_engineer on 2009-02-19
which are the alternative servers that i should use in place of present ones?

---

### Post by jerome1232 on 2009-02-19
You could goto System-Administration-Software Sources, click the drop down box next to "Download From:" select "other" tell it to find the best server.

---

### Post by Therion on 2009-02-19
> **jerome1232 said:**
> 

You could goto System-Administration-Software Sources, click the drop down box next to "Download From:" select "other" tell it to find the best server.
+5

First thing I do on fresh install whether for myself or someone else.  This one little change makes all the difference.

---

### Post by binbash on 2009-02-19
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by eshant_engineer on 2009-02-19
> **binbash said:**
> [http://keryx.betaserver.org/](http://keryx.betaserver.org/)

hey, can i really update from this site?

---

### Post by EXCiD3 on 2009-02-19
> **eshant_engineer said:**
> hey, can i really update from this site?

Yes you can, I'm the developer of it, if you've got any questions, just ask ;)

---

### Post by eshant_engineer on 2009-02-19
ya, i have one pro...while extracting keryx 0.91 error like as shown and how to install it?

---

### Post by eshant_engineer on 2009-02-19
i also tried to extract on ubuntu but not succeeded.

---

### Post by EXCiD3 on 2009-02-20
Try downloading it again, it looks like it got corrupted when you downloaded it. I'm currently in the process of finishing up the 0.92 release and should have it online in about an hour. You might want to just wait for that, lots of updates. :D

**Update: ** Released a new version just a few minutes ago. Try downloading it and giving it a shot. Several new features, all there to make your life easier! [http://keryxproject.org](http://keryxproject.org) (new domain for the latest release too!)

---


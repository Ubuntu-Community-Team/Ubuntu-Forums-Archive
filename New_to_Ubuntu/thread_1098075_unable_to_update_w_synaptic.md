---
title: "unable to update w/ synaptic"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by fiskking on 2009-03-16
since yesterday I am unable to update from synaptic manager and I get the following error:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_i386.deb
  Size mismatch
```


I am using Hardy Heron and yesterday when I tried to update it said it could not retrieve feisty fawn.  I corrected this problem w/in SoftwareSources but I do not know how to correct this, anyone help/?

---

### Post by Peneus on 2009-03-16
Same problem here. 
hopefully it will be fixed soon.

---

### Post by Therion on 2009-03-16
I was able to download the package manually...

go here:  [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/)

The file is there.

Not sure what to tell you...

---

### Post by opm595 on 2009-03-16
I am also experiencing the exact same problem. Is it something only related to Hardy users?

I've attempted in a terminal window to sudo apt-get update, then tried upgrade --fix-missing, and also using Synaptics etc, but to no avail.

Furthermore can someone please elaborate a little more as to what is meant by "size mismatch"?

First time I've ever experienced a problem of this nature with updates.

  . . . .Help us Obi-Wan Kenobi! . .

---

### Post by mkrahmeh on 2009-03-16
if you changed the sources.list between hardy and fiesty, then all i can think of is to find the package causing the problem in the /var/cache/apt and remove it from there..try the update again afterwards

> **opm595 said:**
> Furthermore can someone please elaborate a little more as to what is meant by "size mismatch"?
its just that the size of the package in the server is not the same as what the apt-get is expecting..as far as i know

---

### Post by fiskking on 2009-03-16
well i´m glad that I´m not the only one experiencing this problem:D  maybe something is being fixed out there in ubuntu land

---


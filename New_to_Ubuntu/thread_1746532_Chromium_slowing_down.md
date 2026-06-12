---
title: "Chromium slowing down"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by cambam247 on 2011-05-01
This would be the first sign of any problems on my laptop since I wiped windows and went linux my Chromium 10.0.648.205 (81283) Ubuntu 10.10 Browser is taking a little longer to load pages and video on you tube and other sites in full screen is freezing up.Is there anything I can do besides clearing my browsing data to get Chromium running smoother....
Peace all...

---

### Post by fabricator4 on 2011-05-01
> **cambam247 said:**
> This would be the first sign of any problems on my laptop since I wiped windows and went linux my Chromium 10.0.648.205 (81283) Ubuntu 10.10 Browser is taking a little longer to load pages and video on you tube and other sites in full screen is freezing up.Is there anything I can do besides clearing my browsing data to get Chromium running smoother....
Peace all...

How much RAM do you have, and how much is being used?  Chromium is a bit of a pig.  Use the free command in terminal to get the real picture.

How much HDD is there free?

Chris.

---

### Post by cambam247 on 2011-05-02
What command should I use? 
Here's what I know

---

### Post by cambam247 on 2011-05-02
The "FREE" command  I see lol newbie here

---

### Post by cambam247 on 2011-05-02
cambam24@cambam24-HP-550:~$ free
             total       used       free     shared    buffers     cached
Mem:       2052520     604556    1447964          0      42864     307360
-/+ buffers/cache:     254332    1798188
Swap:      6142972          0    6142972

---

### Post by fabricator4 on 2011-05-02
> **cambam247 said:**
> cambam24@cambam24-HP-550:~$ free
             total       used       free     shared    buffers     cached
Mem:       2052520     604556    1447964          0      42864     307360
-/+ buffers/cache:     254332    1798188
Swap:      6142972          0    6142972

You can put the screen data between code tags to make it easier to read.  There's a # button at the top of the screen that will insert the tags for you, thus:

```
cambam24@cambam24-HP-550:~$ free
             total       used       free     shared    buffers     cached
Mem:       2052520     604556    1447964          0      42864     307360
-/+ buffers/cache:     254332    1798188
Swap:      6142972          0    6142972
```

The bottom line is, there doesn't seem to be anything wrong with your memory usage or disk space.  Open up System monitor 

```
-->System
---->Administration
------>System Monitor
```

and click on the resources tag.  It should tell you if there's something hogging the system.  Look in processes and sort by CPU%. See if there's an application that's misbehaving.

Also look in the resources tag and see what your network appears to be doing while you're looking at YouTube etc.

Chris

---

### Post by cambam247 on 2011-05-02
Thx chris for your help, Cheers...

---


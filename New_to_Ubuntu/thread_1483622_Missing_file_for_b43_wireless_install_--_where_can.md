---
title: "Missing file for b43 wireless install -- where can I find this file?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by NUboon2Age on 2010-05-14
A script in B43-FWCutter requires a file from a web site that doesn't seem to exist any more and so the wireless driver install fails Where can I get this file?  Or is there another solution to this dilemma?

wl_apsta-3.130.20.0.o

originally found at:
downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o

---

### Post by anewguy on 2010-05-14
I believe that in most instances you just need to hard-wire to your router, do an sudo apt-get update, then look in hardware drivers for the restricted driver and enable it.  Be sure to unplug the hard-wire cable before trying your wireless.

Dave ;)

---

### Post by Sealbhach on 2010-05-14
That website does still exist, from what I can see, I just put that address in my address bar and downloaded it.

.

---

### Post by NUboon2Age on 2010-05-14
> **Sealbhach said:**
> That website does still exist, from what I can see, I just put that address in my address bar and downloaded it.

.

If you try it you'll see that its a zero-length file.

---

### Post by bredman on 2010-05-14
I just downloaded this file and it is 638kB.

Recommend that you try again. I did an install of b43-fwcutter last week and had no problems. This is the best way to get a BCM43xx wifi working. Don't bother with anything else, everything else broke my heart until I found how to do it properly.

---

### Post by NUboon2Age on 2010-05-14
> **anewguy said:**
> I believe that in most instances you just need to hard-wire to your router, do an sudo apt-get update, then look in hardware drivers for the restricted driver and enable it.  Be sure to unplug the hard-wire cable before trying your wireless.

Dave ;)

I did that and I don't find that file.

---

### Post by NUboon2Age on 2010-05-14
> **bredman said:**
> I just downloaded this file and it is 638kB.

Recommend that you try again. I did an install of b43-fwcutter last week and had no problems. This is the best way to get a BCM43xx wifi working. Don't bother with anything else, everything else broke my heart until I found how to do it properly.

Okay I did it again and I see you're right -- my browser said it was a '0 file' and I misinterpreted that to mean its a zero byte file (I guess it meant it is less than an MB large).  Thanks!  I'll see if that does it for me before marking this solved.

---

### Post by Sealbhach on 2010-05-14
Edit: looks like you sorted it out.
.

---

### Post by anewguy on 2010-05-14
BTW - anyone needing the firmware cutter - you don't have to download it, it is on the LiveCD you installed from in the /pool/main/b folder.  Just click it to start installation.  For those interested, the build-essential package is also in the same folder.

Dave ;)

---

### Post by Ozymandias_117 on 2010-05-14
> **anewguy said:**
> BTW - anyone needing the firmware cutter - you don't have to download it, it is on the LiveCD you installed from in the /pool/main/b folder.  Just click it to start installation.  For those interested, the build-essential package is also in the same folder.

Dave ;)

Thanks, this is very useful information to have!

---


---
title: "Where'd my space go?"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by ipburbank on 2010-06-20
Hey - I have been having this problem for years, but always just re-installed to solve it; the issue is that how much space I have used is reported to be very different depending on what I ask. See the attached image for an example.

I also have a Drobo attached to my machine, which has indicator lights for how much space is used. After deleting 5 hundred gigs of data from it, none of the lights turned off (claims that there is no new space on it). Why?!

(i did empty the trash)

Thanks, Istvan.

---

### Post by B!aine on 2010-06-20
I had a similar issue with some external types of drives (thumb drives and NAS).  What I eventually did to solve it was open the device so it shows hidden files (Ctrl+H or view>show hidden files).  There is a hidden trash folder that keeps stuff that you delete.  Try opening that and deleting the contents to see if it helps.

---

### Post by ipburbank on 2010-06-20
I also tried that. .trask-1000 or something like that IIRC.
also, if I put the drive onto a windows machine, the lights change to what they should be. but once I put the drive back onto my linux box, the lights go up 20% or more.... what?

---

### Post by B!aine on 2010-06-20
Yeah, that's the file that I was talking about.  That worked for me.  Hopefully someone more knowledgeable will get on and provide a fix.

---

### Post by jerome1232 on 2010-06-20
So let me get this right the drive has lights on it physically that indicate when it's full? Do you have to install a driver for it under Windows?

Perhaps it's just a linux driver issue.

---

### Post by ipburbank on 2010-06-20
no, no drivers.
the drobo has a processor in it.
can I re-build a directory in linux? just incase the inodes or something got messed up?

---


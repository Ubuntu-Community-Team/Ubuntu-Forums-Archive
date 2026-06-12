---
title: "Mic and Speakers on Acer Aspire One"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Ed in CT on 2010-02-20
I'm using an Acer Aspire One 532h-2268 with Windows 7 Starter 32-bit installed.  Processor is Intel Atom N450.  Partitioned the drive and put Ubuntu 9.1.  Working well but cant get the built in microphone or speakers to work.  Anyone know how I can get the mic and speakers to work?

Thanks,

Ed

---

### Post by naiku on 2010-02-20
Try going to System - Preferences - Sound and click on the Hardware tab. See if you have any options there and if changing them gets your sound/mic working. I had the same problem on my Dell a week ago, the default profile did not work for me, as soon as I changed it I got the sound working.

---

### Post by 416inversed on 2010-02-20
I don't know if it's the same reason, but the microphone for my Acer Aspire D250 didn't work out of the box. I followed the directions here:
[https://help.ubuntu.com/community/AspireOneAOD250](https://help.ubuntu.com/community/AspireOneAOD250) (about 2/3rds of the way down the page)
to compile new drivers for it.

It might work for you?

---

### Post by Ed in CT on 2010-02-21
Thanks.  That link worked perfectly and solved the problem.  For the a brief moment I felt like a real computer guy downloading and compiling (whatever that is) files.  I really appreciate your help.  Ubuntu rocks and this forum is awesome.  Thanks so much.

---

### Post by 416inversed on 2010-02-21
Awesome. Glad it worked.

These boards really are a great resource in learning the in's & out's of Ubuntu... all you need to do is ask.

---

### Post by BaroqueBloke on 2010-04-19
I have the same problem.  Used you the list you posted and got down to "./configure --with-cards=all"  and I keep getting the error "./configure: No such file or directory"

any ideas?  

Thanks!

---


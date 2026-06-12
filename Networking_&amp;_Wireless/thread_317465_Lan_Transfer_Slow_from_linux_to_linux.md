---
title: "Lan Transfer Slow from linux to linux"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by Ethos on 2006-12-12
Hell everyone I just finished configing my ubuntu server. I replaced the network cables from my router to my switch and to my server, but im still getting transfer speeds of 4mbs from my desktop to the file server. All of the adapters are at full 100, my outside connection is very good and there is no problem with that....I just downgraded my firmware from a special custom one to the standard linksys one for my router thinking that could be the problem, but that wasnt the case...Any ideas on how I can test more aspects of the network to pinpoint this issue? thanks alot Ethos

---

### Post by Ethos on 2006-12-12
Also I just setup ftp, and im getting 11mbs... :/ noting near 100...

---

### Post by insane_alien on 2006-12-12
is it Mb/s or MB/s your getting. theres a factor of 8 difference. if your getting 11MB/s then its actually the proper speed(88Mb/s + the packet stuff needed). if its 11Mb/s then its definitely slow.

---

### Post by Ethos on 2006-12-12
well lets think of it this way...how long should it take me to transfer 1gig at that rate? (the proper rate)

---

### Post by insane_alien on 2006-12-13
i'm getting just over 93 seconds at 11MB/s. i'm going to assum that yours is taking much much longer than that. maybe somewhere on the order of 12.5 minutes

---

### Post by Ethos on 2006-12-15
I actually setup a ftp on my server and im getting 11.7 MB/s so all is good :).

---

### Post by gwk on 2007-10-15
I'd be interested if anyone has some insight on this issue.  I have the same situation.  100Mbit network but when a linux comp is on one side of the connection it stays steady around 100 kbytes/second.  

Tried both Ubuntu to Windows and Ubuntu to Ubuntu and the transfers are super slow.  Downloading from the net is much faster, I can max out my internet connection at 1.5megabytes/sec.

Anyone have ideas?

---


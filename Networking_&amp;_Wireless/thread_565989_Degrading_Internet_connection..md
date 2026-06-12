---
title: "Degrading Internet connection."
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2007-10-02
Hi. My Computer picks up wireless internet from the office. For some reason in ubuntu the internet will be fairly fast for a little wile then it will slow down to unusable speed. I got plenty  of signal. when i boot into windows the connection is fine for as long as the computer is on. Can  tou please help me.

---

### Post by Dwiman89 on 2007-10-02
Any one? any one?

---

### Post by amitabhishek on 2007-10-03
same problem here. Speed deteriorates after some time of browsing. I have broadband LAN connection

---

### Post by mrsticks on 2007-10-04
I wonder if this is all related.  About 2 days ago, I noticed the internet would just stop.  I could download fine ( my standard test of downloading the kernel ).  But most sites would half load and just sit there.  Sometimes they would time out.  I thought it might be my internet connection, DNS maybe, so I let it be.  But it continued another day. I booted up into windows and all the same sites worked fine, no issues.  Yet on the same box, in Linux, the sites wouldnt load, or even time out.

I am running 7.04.  As for updates:
libssl 0.9.8c-4 and openssl 0.9.8c-4 were installed on 9/29
libpq5 8.2.4 was installed on 10/2

Seems odd that 2 or 3 people would have similar symptoms.

Any thoughts out there?

Thanks

-peter

---

### Post by mrsticks on 2007-10-05
I figured out what was doing it for me.  moblock.  I have had it installed on this PC for 9 months at least.  I have had no problems with it before.  Last week, I noticed that Synaptic had problems with the repository listed for moblock.  So I went to their homepage ( [http://moblock-deb.sourceforge.net/ ]("http://moblock-deb.sourceforge.net/")  ) and double checked that I had the correct ones and correct gpg keys.  I updated my sources.list and got the new keys, installed the latest version.  

I must have not noticed the problem because I was away for a few days.  Ive been thinking and thinking about it, as all other internet works, downloading, uploading, ftp, ping, but most websites would not load.

Today I shut off moblock, everything works, then stopped it, problem persists.

That was my issue and solution.

-peter

---

### Post by webceo on 2007-10-07
Well I have the same issue on my computer, but it has nothing to do with moblock in my case, I actually don't have that at all.
I'm running Feisty, sometimes I just can't reach some websites, when I can reach others. I test the same websites on a windows computer on the same network (a wireless network) and they load.

Anyone has an idea of what the problem might be ?

Thanks

---


---
title: "Unbearably Slow Internet in Gutsy (ipv6 disabled, using OpenDNS)"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by conjurer on 2007-11-06
Hi, ever since I upgraded to Gutsy, internet has been really, really, unbearably slowww.  I've spent hours reading all of the other threads about this issue and I have done the following:

 - Globally disabled ipv6 (unaliased it, and blacklisted it also)
 - added the OpenDNS servers
 - updated libc6 (took me forever to do it, it would only download a little bit in the beginning and then would stop downloading. I had to cancel and re-download the update several times to get it completely)

None of these things have worked. Can anyone help me out?

By the way, I'm **not** using a router, and I have a **wired** connection only (**no wireless**). And unlike some people, my internet speed does not improve once the website is found. Every page of every thread I've read in this forum were slow to load (At the time I'm writing this, the page still hasn't fully loaded yet, and most likely still will not have finished loading by the time I pressed on the 'post' button)

Please, can anyone suggest anything?

---

### Post by conjurer on 2007-11-06
Ok I followed the following advice and it seems to have worked:

> Add the following to /etc/sysctl.conf (524288 could be too large, try 262144 or 131072 in place of 524288 if you don't notice an improvement. 524288 worked best for me though.):

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Then to have the settings take effect immediately, run:

sudo sysctl -p

524288 didn't do anything for me, but after replacing it with 262144, internet is back to normal again!

---

### Post by k9brand on 2007-11-06
> **conjurer said:**
> Ok I followed the following advice and it seems to have worked:



524288 didn't do anything for me, but after replacing it with 262144, internet is back to normal again!

262144 worked for me too... thanks so much !

---

### Post by brunoscunha on 2007-12-06
Worked very well for me with the 524288.
Nice going :D

---

### Post by r4ik on 2007-12-11
262144 is the one for me thank you very much :)

---

### Post by Scunizi on 2007-12-11
Even though my connection wasn't overly slow, actually quite normal, I gave it a shot and found the tweek to help pretty nicely.  Either number referenced seemed to work the same for me.  Thanks!

---

### Post by kevdog on 2007-12-11
Can someone write a quick How-To for this solution.  Its very simple and elegant.  Be sure to describe the problem and then include the solution.  I would like to make reference to it for other new users with similar problems.

---

### Post by Scunizi on 2007-12-11
See posts #1 & #2

---

### Post by kevdog on 2007-12-11
Well I guess that is all Im going to get!  Im just trying to make it real easy for beginners.  I mean super-easy, idiot proof.

---

### Post by i.tJunKie on 2007-12-11
Hey guys!

My internet connection was pretty alright to begin with, but would sometimes load some pages at an amazingly painful turtle paceness...:) I did the broadband tweak and tried loading the painfully slow pages and it worked a treat! 524288 seemed to work ok...but 262144 worked a whole lot better :)

Thanks ;)

---

### Post by Scunizi on 2007-12-11
kevdog, you sound articulate and cam probably write this yourself.  Here's my rendition for nOOb's of which I count my self as one.  


```
Slow internet with broadband?  Try the following from a terminal....

gksudo gedit /etc/sysctl.conf (this open up a new window)

Copy and paste the following at the bottom of the newly opened window.

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

***********************************************************************************
Now click the "Save" button.

In a terminal type (or copy and paste) sudo sysctl -p and hit enter.

Close FF or your current browser and reopen.  Notice any speed difference? 
If not go back to step 1 and after the window opens look for the "replace" button at the top.  
Click that and enter 524288 in the "find" location and 262144 in the "Replace With" box. 
Now click "Replace All".  Save again then in the terminal retype sudo sysctl -p <enter>.  
Restart your browser again and see if there is any difference.  Yes?  Congratulation!
Special thanks to conjurer for finding this solution.
```

---

### Post by Bobba on 2008-01-18
Wow that's better!!!! Slow internet since upgrade to Gutsy has been driving me nuts. This has done the job, using 524288.
Thanks a lot :guitar:

---

### Post by Bobba on 2008-01-22
Correction: The above solved slow internet for me, however lan communication was still super slow and I could no longer stream music over my network due it never gets past buffering. Had to downgrade back to Feisty and now it works great again.

---

### Post by zeller on 2008-01-22
So does this work with wireless? I saw that the problem was initially with a wired connection.

---

### Post by Bobba on 2008-01-22
This was for wireless for me

---

### Post by zeller on 2008-01-24
Anyone else have trouble using this solution for a wireless lan? Particularly on a college campus?

And I take it these additional lines can just be commented out or deleted from the /etc/sysctl.conf file if neither number works? Yes, no, maybe so?

---

### Post by Fascination on 2008-02-12
Im on a wireless lan and this solution worked wonders for me. I didn't have too many problems with speed before, but since I started using imap for my mail the connection would start dropping out on me every 1/2 hour to an hour.
Soon as I ran this (kept at 524288) its been working like a dream!

---

### Post by zeller on 2008-05-30
How do I disable this? Typing sysctl -p gets it started? What disables it other than simply deleting the lines or commenting them out?

---


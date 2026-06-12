---
title: "Wireless help needed!"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by papafred07 on 2006-07-19
alright, let me prefice this by saying a am a complete noob at linux in general (like 4 days of experience).  In any case, I am having many problems getting my wireless internet to work.  I have a dell inspiron 6000 with a pro wireless 2200 b/g card built in.  My router is the standard Linksys wireless G broadband.  Our network is secured which seems to be the root of the problem (whenever I first installed dapper, I was at a friends house where there was an unsecured wireless and I was able to connect fine).  I've alread y installed network manager too.  Despite being able to view numerous network including my own using the wireless assistant, I am unable to connect to them.  Whenever I try typing iwconfig in terminal I get this response:

lo        no wireless extensions.

eth1      unassociated  ESSID:"linksys_SES_42393"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


I am not even sure what 'lo' or 'eth1' or 'eth0' are.  Any help at all would be GREATLY appreciated.

---

### Post by gabrieliscool on 2006-07-19
The Recent Kernel Update Breaks Wireless Connectivity, Just Have To Wait It Out Or Boot To The Previous Kernel (That's What I'm Doing).

---

### Post by papafred07 on 2006-07-19
How do you boot to the previous kernel?  Why would they make an update that disabled wireless?

---

### Post by papafred07 on 2006-07-19
actually, nevermind any of this. I just got it working!

---

### Post by jamboarder on 2006-07-20
What did you do to get it working?

---

### Post by ubun00b on 2006-07-20
hi, i'm having wireless issues too, where is the wireless assistant you've been using located?

---


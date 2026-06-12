---
title: "install drivers for Fujitsu FDX310 ADSL USB modem"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Ian Edmont on 2007-04-29
Hi, 

Just installed 7.04 and am trying to install drivers for Fujitsu FDX310 ADSL USB modem. When entering "/usr/bin/eciadsl-start | tee log.txt" in root konsole I get a synching error. Log file below. Any ideas how to fix this please? 

Thanks. 

Ian E 

LOG FILE: 


[EciAdsl 1/5] Setting up USB support... 

Preliminary USB device filesystem is OK 

[EciAdsl 2/5] Uploading firmware... 

eciadsl-firmware: success 
firmware loaded successfully 

[EciAdsl 3/5] Synchronization... 


Please Wait.. Synchronisation in progress [-] 
Please Wait.. Synchronisation in progress [\] 
Please Wait.. Synchronisation in progress [|] 
Please Wait.. Synchronisation in progress [\] 
Please Wait.. Synchronisation in progress [|] 
ERROR eciadsl-synch SYNCHING: failed 

ERROR eciadsl-synch: failed 
Synchronization successful 

[EciAdsl 4/5] Connecting to provider... 

using channel 1 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x1 <magic>] 
sent [LCP ConfReq id=0x1 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6228), status = 0xfa 
using channel 2 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x2 <magic>] 
sent [LCP ConfReq id=0x2 <magic>] 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6238), status = 0xfb 
Modem hangup 
Connection terminated. 
using channel 3 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x3 <magic>] 
sent [LCP ConfReq id=0x3 <magic>] 
sent [LCP ConfReq id=0x3 <magic>] 
sent [LCP ConfReq id=0x3 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6273), status = 0x0 
using channel 4 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x4 <magic>] 
sent [LCP ConfReq id=0x4 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6301), status = 0x0 
using channel 5 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x5 <magic>] 
sent [LCP ConfReq id=0x5 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6329), status = 0x0 
using channel 6 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x6 <magic>] 
sent [LCP ConfReq id=0x6 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6357), status = 0x0 
using channel 7 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x7 <magic>] 
sent [LCP ConfReq id=0x7 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6386), status = 0x0 
using channel 8 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x8 <magic>] 
sent [LCP ConfReq id=0x8 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6414), status = 0x0 
using channel 9 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0x9 <magic>] 
sent [LCP ConfReq id=0x9 <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6442), status = 0x0 
using channel 10 
Using interface ppp0 
Connect: ppp0 <--> /dev/pts/2 
sent [LCP ConfReq id=0xa <magic>] 
sent [LCP ConfReq id=0xa <magic>] 
Modem hangup 
Connection terminated. 
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 6470), status = 0x0 
ERROR: failed to connect

---

### Post by tcrabb on 2007-08-05
Exactly same behaviour with me - ok 2 years have passed has not Ubuntu sorted this out??? Anyone?

---


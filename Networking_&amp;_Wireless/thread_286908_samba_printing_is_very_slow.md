---
title: "samba printing is very slow"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by su1c1de on 2006-10-28
hi guys

i installed ubuntu like 3 weeks ago and after some trouble it got my 2 printers (hp laserjet 1020 and hp deskjet 3650) to work with cups and samba.

but there is just one damn problem with the deskjet 3650... if i print directly from the ubuntu machine it prints immediately.. but if i try to print from one of my windows machines through samba it takes almost 15 minutes unitl it starts printing...

i watched the network traffic with tethereal while printing and this was shown over and over... the whole 15 minutes

```
415.623620 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.625056 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.625122  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109568994 Ack=111381173 Win=32767 Len=0
415.626755 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.626902  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.631337 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.633019 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.633098  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569045 Ack=111385521 Win=32767 Len=0
415.634557 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.634698  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.639099 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.640698 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.640891  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569096 Ack=111389869 Win=32767 Len=0
415.642145 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.642360  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.646836 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.648352 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.648419  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569147 Ack=111394217 Win=32767 Len=0
415.649803 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.649942  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.654414 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.655917 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.655981  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569198 Ack=111398565 Win=32767 Len=0
415.657329 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.657463  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.661901 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.663391 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.663456  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569249 Ack=111402913 Win=32767 Len=0
415.664802 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.664940  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.669352 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.670992 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.671057  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569300 Ack=111407261 Win=32767 Len=0
415.672464 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.672602  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.677048 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.678642 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.678709  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569351 Ack=111411609 Win=32767 Len=0
415.680174 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.680311  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.684733 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.686424 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.686488  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569402 Ack=111415957 Win=32767 Len=0
415.687877 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.688024  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.692430 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.693967 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.694033  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569453 Ack=111420305 Win=32767 Len=0
415.695603 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.695740  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.700151 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.702626 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.702691  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569504 Ack=111424653 Win=32767 Len=0
415.704277 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.704416  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.708871 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.710516 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.710582  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569555 Ack=111429001 Win=32767 Len=0
415.711968 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.712104  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.716519 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.718123 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.718189  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569606 Ack=111433349 Win=32767 Len=0
415.719649 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.719788  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.724285 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.724663 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11434 opnum: 19 ctx_id: 0
415.724789  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569657 Ack=111436613 Win=32767 Len=0
415.725573  192.168.0.4 -> 192.168.11.152 DCERPC Response: call_id: 11434 ctx_id: 0
415.731707 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.733254 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.733347  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569749 Ack=111439533 Win=32767 Len=0
415.734733 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.734906  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.739423 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.740879 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.740945  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569800 Ack=111443881 Win=32767 Len=0
415.742332 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.742472  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.746920 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.748344 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.748409  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569851 Ack=111448229 Win=32767 Len=0
415.749885 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.750023  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.754491 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.756167 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.756233  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569902 Ack=111452577 Win=32767 Len=0
415.757755 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.757893  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.762398 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.764036 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.764100  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109569953 Ack=111456925 Win=32767 Len=0
415.765487 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.765622  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.770093 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.771755 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.771821  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570004 Ack=111461273 Win=32767 Len=0
415.773225 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.773370  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.777804 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.779237 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.779311  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570055 Ack=111465621 Win=32767 Len=0
415.780893 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.781037  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.785468 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.786957 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.788427 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.788743  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570106 Ack=111469969 Win=32767 Len=0
415.788815  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.793819 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.795455 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.795521  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570157 Ack=111474317 Win=32767 Len=0
415.797093 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.797235  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.801686 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.803125 192.168.11.152 -> 192.168.0.4  TCP [TCP segment of a reassembled PDU]
415.803192  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570208 Ack=111478665 Win=32767 Len=0
415.805896 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.806032  192.168.0.4 -> 192.168.11.152 SMB Write AndX Response, FID: 0x7127, 4280 bytes
415.808116 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11435 opnum: 19 ctx_id: 0
415.808826  192.168.0.4 -> 192.168.11.152 DCERPC Response: call_id: 11435 ctx_id: 0
415.811251 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11436 opnum: 19 ctx_id: 0
415.811498  192.168.0.4 -> 192.168.11.152 DCERPC Response: call_id: 11436 ctx_id: 0
415.928455 192.168.11.152 -> 192.168.0.4  TCP 1046 > netbios-ssn [ACK] Seq=111480461 Ack=109570443 Win=16377 Len=0
417.811796 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11437 opnum: 23 ctx_id: 0
417.849813  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570443 Ack=111480593 Win=32767 Len=0
417.858114  192.168.0.4 -> 192.168.11.152 DCERPC Response: call_id: 11437 ctx_id: 0
417.862813 192.168.11.152 -> 192.168.0.4  DCERPC Request: call_id: 11438 opnum: 29 ctx_id: 0
417.862842  192.168.0.4 -> 192.168.11.152 TCP netbios-ssn > 1046 [ACK] Seq=109570531 Ack=111480725 Win=32767 Len=0
417.863111  192.168.0.4 -> 192.168.11.152 DCERPC Response: call_id: 11438 ctx_id: 0
418.031648 192.168.11.152 -> 192.168.0.4  TCP 1046 > netbios-ssn [ACK] Seq=111480725 Ack=109570639 Win=16181 Len=0
445.203326 192.168.11.152 -> 192.168.0.4  SMB Close Request, FID: 0x7127
445.203667  192.168.0.4 -> 192.168.11.152 SMB Close Response
445.373256 192.168.11.152 -> 192.168.0.4  TCP 1046 > netbios-ssn [ACK] Seq=111480770 Ack=109570678 Win=16142 Len=0
478.523734 192.168.11.152 -> 192.168.0.4  TCP [TCP Keep-Alive] netbios-ssn > 36696 [ACK] Seq=0 Ack=0 Win=16535 Len=1
478.523778  192.168.0.4 -> 192.168.11.152 TCP [TCP Keep-Alive ACK] 36696 > netbios-ssn [ACK] Seq=0 Ack=1 Win=1728 Len=0 TSV=2781778 TSER=8023 SLE=0 SRE=1

```

printing on the laserjet and cups-pdf wokrs just fine through samba

does anyone have an idea whats wrong?

thanks guys

---

### Post by davemc on 2008-04-08
Bugs in XP

Solution is covered here...

[http://lists.samba.org/archive/samba/2005-September/110571.html](http://lists.samba.org/archive/samba/2005-September/110571.html)

---


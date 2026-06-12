---
title: "Aircrack-ng - no matching network found - Check you essid"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by Anthony_Mobley on 2016-02-04
Hi, I'm doing a pen testing course and I am trying to work with aircrack-ng. I decided to practice by trying to hack my wifi password.

So far everything has gone perfect. 

I just finished getting a WPA handshake and now I am trying to crack the password with Aircrack and crunch and I am typing in this command -

crunch 10 10 -t %CF4DC%%%% 1234567890 | aircrack-ng -w - SCAN_test-01.cap -e "my networks essid"

the return is -
/////////////////////////////////////////////////////
opening SCAN_test-01.cap
crunch will now generate the following amount of data: 1100000 bytes
1 MB
0 GB
0 TB
0 PB
crunch will now generate the following number of lines: 100000
opening SCAN_test-01.cap
opening SCAN_test-01.capwait...
No matching network found - check your essid.
////////////////////////////////////////////////////

The essid I am entering is definitely correct so I don't understand why it's doing this. Can anyone help?
thanks

---

### Post by howefield on 2016-02-04
Thread closed.

From the forums Code of Conduct:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed. 

---


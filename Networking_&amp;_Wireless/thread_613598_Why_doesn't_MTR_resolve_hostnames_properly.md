---
title: "Why doesn't MTR resolve hostnames properly?"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Treq on 2007-11-15
Hi all,

there is this little irritation. MTR doesn't seem to resolve properly the traced IP-addresses.
Most/all of these missing entries are found in my /etc/hosts file, but MTR seems to not take the /etc/hosts file into account when resolving. This must be a bug, surely?

Cheers,
Treq
======================================

llso@Yep:~$ mtr [www.vg.no](www.vg.no)
                                                       My traceroute  [v0.72]
Yep (0.0.0.0)                                                                                             Thu Nov 15 10:23:17 2007
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                                                                                                             Packets
               Pings                                                                                                               
 1. 213.46.232.129
 2. 213.46.234.241  
 3. 213.46.234.213   
 4. 213.46.225.251
 5. 213.46.161.117 
 6. 213.46.183.186   
 7. te-4-1.car3.amsterdam1.level3.net
 8. ae-31-55.ebr1.amsterdam1.level3.net
 9. ae-2.ebr2.dusseldorf1.level3.net
10. ae-4-4.car1.stockholm1.level3.net
11. 213.242.110.26 
12. ge-6-1-0.cr2.osls.no.catchbone.net
13. te7-4.rs2.sand.no.catchbone.net
14. 193.69.165.11       
15. 193.69.165.21
======================================

But step 1-6 _do_ (mostly) resolve:
======================================
llso@Yep:~$ tracepath [www.vg.no](www.vg.no)
 1:  Yep.local (213.46.232.999)                            0.234ms pmtu 1500
 1:  213.46.232.129 (213.46.232.129)                        0.937ms 
 2:  nl-ams05b-mc2-vl-302 (213.46.234.241)                  0.905ms 
 3:  213.46.234.213 (213.46.234.213)                      asymm  4   1.913ms 
 4:  nl-ams05a-ra1-fe-4-0-0 (213.46.225.251)              asymm  5   2.954ms 
 5:  nl-ams05a-ra3-so-7-0-3-0 (213.46.161.117)            asymm  7   2.831ms 
 6:  nl-ams09a-ri1-ge-5-0 (213.46.183.81)                 asymm  7   3.175ms 
 7:  pni-as3356 (4.68.63.125)                             asymm  8   3.323ms 
 8:  ae-31-55.ebr1.amsterdam1.level3.net (4.68.120.158)   asymm  9   5.575ms 
 9:  ae-2.ebr2.dusseldorf1.level3.net (4.69.133.90)       asymm 10   6.656ms 
10:  ae-4-4.car1.stockholm1.level3.net (4.69.135.21)      asymm 11  33.134ms 
11:  213.242.110.26 (213.242.110.26)                      asymm 13  39.699ms 
12:  ge-6-1-0.cr2.osls.no.catchbone.net (81.0.128.81)     asymm 14  39.816ms 
13:  te7-4.rs2.sand.no.catchbone.net (193.75.1.166)       asymm 14  39.932ms 
14:  no reply
======================================

---

### Post by stevux on 2007-11-15
a guess;
[INDENT]Maybe your DNS server is really slow? As MTR is non-blocking for DNS requests, it may take some time for the dns names to replace the IP addresses in the list. Let it run for a couple of seconds, see what happens..
[/INDENT]


how to troubleshoot;
[INDENT]open a second shell window
  run the command [COLOR="Red"]'sudo tcpdump -s 1500 -i eth0 -w dnsreq.pcap udp && port 53[/COLOR]'
  in the 1st window, type '[COLOR="Red"]mtr [www.vg.no](www.vg.no)[/COLOR]'
  wait 10 seconds, make sure some names do not resolve
  go to the 2nd window, stop tcpdump with CTRL-C
  type '[COLOR="Red"]wireshark dnsreq.pcap[/COLOR]' (if you do not have wireshark yet, type '[COLOR="Red"]sudo apt-get install wireshark[/COLOR]' first)
  now look for the non-resolved ip address requests, and see what the reply from the server(s) was
[/INDENT]
hth,

---


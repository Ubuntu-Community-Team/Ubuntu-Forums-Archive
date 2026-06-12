---
title: "Ad-hoc Signal Quality"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by weizilla on 2007-01-17
I have a working ad-hoc network with 2+ hosts, however, I am having problems determining the quality of the wireless connections between the individual hosts.  
For instance, if I have hosts A, B and C, I would like to run a command on B which would tell me how strong the A-B and B-C wireless connections are. The only thing I can think of is running "iwlist scan", however, it only shows one ad-hoc host in the results and there's no information to determine which host it is. 

Does anyone have any suggestions or maybe a console program which will do this? Even a webpage which explains more about how linux wireless ad-hoc systems work would be helpful.

---

### Post by Rhubarb on 2007-01-17
There is one dirty method of working out your signal quality:
Copy a large file to / from each host on the ad-hoc network.
Then time how long it takes to receive that file, and there you have a primitive way of finding out each host's signal quality (connection speed).

It's not pretty or nice, but it should do the job for you.

---

### Post by weizilla on 2007-01-17
I wish I could do that but I'm looking for a quick method of determining quality. Sending big files back and forth isn't really suitable in my situation.

---


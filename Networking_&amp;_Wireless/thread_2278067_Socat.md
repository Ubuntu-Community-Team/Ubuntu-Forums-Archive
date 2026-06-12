---
title: "Socat"
date: 2015-05-13
forum: Networking &amp; Wireless
---

### Post by gpgp on 2015-05-13
Hello

I was just wondering if anyone has a lot of experience with socat. 
i am just wondering if socat could listen to 16 tcp connections and forward them over udp.

it certainly reads like it can do that but if someone has done something similar i would like to hear about your experience.

the 16 devices are automation encoders and i want to give the streams coming in to a video server system. that system prefers udp multicast for automation data. we have the software company for the video servers writing new software to handle the tcp connections but we havent gotten a stable release working yet, so i am looking to other ideas.

thanks you very much, any ideas appreciated.

gpgp

---

### Post by Skaperen on 2015-05-14
i have a lot of experience with **socat** including having written a few scripts that use it.
i know it can listen to 1 TCP port.  i am not aware of the ability to do more.  why not run 16 processes in parallel?
if you (and colleagues) are writing code maybe you can consider SCTP in place of TCP.

---

### Post by gpgp on 2015-05-14
Thank you for your reply. 
we are married to tcp because of the automation encoders in use.

gpgp

---


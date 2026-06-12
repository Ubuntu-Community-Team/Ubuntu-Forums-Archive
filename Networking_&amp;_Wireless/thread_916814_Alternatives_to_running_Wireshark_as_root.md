---
title: "Alternatives to running Wireshark as root?"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by scoob8000 on 2008-09-11
I'm setting up a box mainly for traffic sniffing purposes.  I want to make this machine as user friendly as possible.

So far, I've determined wireshark needs to be run as root in order to see any interfaces to capture on.

I have a "user" account that automatically logs on, and a folder on the desktop to save my wireshark traces to.

Problem is when you you're running wireshark as root and save a trace, that file gets saved as owner root.  The only way my "user" can then do anything with the file is if I "sudo chmod 777 capture.pcap"..

Any easier solutions out there?   :)

---

### Post by HalPomeranz on 2008-09-11
You have to run wireshark as root, there's no getting around that.  Otherwise the program wouldn't be able to put the interface of your system into promiscuous mode in order to capture all the network traffic flying by.

Btw, instead of doing "chmod 777 capture.pcap" you should do "chown <youruserid> capture.pcap".  Your chmod command makes the file read-write for everybody on the system.  The chown command would make it so that your user ID owns the file and only you can read it.

---

### Post by scoob8000 on 2008-09-11
So my only other idea then would be to create a cron job to chmod or chown all the files in that directory every few minutes?

Just trying to automate things as much as possible..

---

### Post by HalPomeranz on 2008-09-11
> **scoob8000 said:**
> So my only other idea then would be to create a cron job to chmod or chown all the files in that directory every few minutes?


Yep, that's pretty much what it comes down to.

---


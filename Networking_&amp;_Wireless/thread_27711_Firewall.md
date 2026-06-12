---
title: "Firewall"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by Simian on 2005-04-17
I'm not really that clued up about security or firewall. I recently installed Firestarter ande everything seemed fine. But all day today I have been taking hits from

Source:82.322.81.145 and 130.88.202.49 Protocol: UDP Server: NTP


when I look up hostnames for 130.88.202.49 I get: maverick.mcc.ac.uk

What is this about and should I be worried?

(incidently, I hope this is posted in the correct forum)

---

### Post by heimo on 2005-04-17
Those are probably the ntp servers that you can find if you right click your desktops date/time, select Adjust Date&Time ->Periodically syncronize -> Select Servers. Those are network time protocol servers (130.88.202.49=ntp2a.mcc.ac.uk=maverick.mcc.ac.uk), You should allow ntp traffic from those servers (or your time won't be syncronized).

Cheers!

---

### Post by Simian on 2005-04-17
[QUOTE=heimo]Those are probably the ntp servers that you can find if you right click your desktops date/time, select Adjust Date&Time ->Periodically syncronize -> Select Servers. Those are network time protocol servers (130.88.202.49=ntp2a.mcc.ac.uk=maverick.mcc.ac.uk), You should allow ntp traffic from those servers (or your time won't be syncronized).

Cheers![/QUOTE]
 Thanks heimo. I was getting worried for a while then. 
In the future when I get inbound events like that how can I tell whree they are comming from?

---

### Post by heimo on 2005-04-17
It's a wide subject. You need to know what is going on in your computer. Even the malicious connection attemts are not always so interesting. Hack attempts and viruses are knocking our computers all the time. And it's easy to get suspicious about valid traffic (without real reason).

To know about these things, learn TCP/IP (read RFCs) and related protocols - learn tools like ethereal, tcpdump, netstat, nmap and iptables. Check the projects snort, The Honeynet Project and various security lists (CERT / Securityfocus). Very, very interesting stuff. Well, not for everyone, but for me it is.

Or, you can continue with your life and do something useful. :D

---

### Post by Simian on 2005-04-17
Thanks for all the advice heimo. I better start reading  :|

---

### Post by heimo on 2005-04-17
In general, you're quite safe as long as you're not running any services (Apache/SSH/FTP/Postfix) that listen outside connections (and as far as I know, there's none in default install). Keep Ubuntu updated and you're very safe.

---


---
title: "Network Manager only detects strongest non secure network"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by michaeljb2005 on 2007-06-24
I don't know if this problem is localized to network manager or not but when I restart my computer it only recognizes the strongest un-secure network around me (probably a neighbor).  I know there are several secure networks around me including mine and it does not detect those at startup.  Generally I can either wait until it detects those networks or I have to manually connect to my network by selecting "other wireless networks".  It takes time to connect but eventually sees all the networks around and connects to mine.  I'm not sure what's going on here but it's a real pain to have to wait and manually connect my network at startup every time.  Anyone have any ideas what the problem might be?

---

### Post by scrooge_74 on 2007-06-24
I think it has something to do with broadcast time 

what happen when starting if you type on a terminal 

 iwlist eth1 (or your wireless card) scanning

those the networks show there?

---

### Post by michaeljb2005 on 2007-07-02
> **scrooge_74 said:**
> I think it has something to do with broadcast time 

what happen when starting if you type on a terminal 

 iwlist eth1 (or your wireless card) scanning

those the networks show there?

It says unknown command 'eth1'.  I'm not sure what you're talking about with broadcast time.  What happens is when I start my computer and it's loading into gnome, network manager is trying to see all the networks around me but it only sees the strongest unsecured network (it's not mine).  And since it doesn't see mine I have to manually tell it to search for other networks planting the information for my router into it.  Eventually it connects and sees all the networks around me but not til I manually configure it.  I have to do this everytime on startup.  Any ideas?

---


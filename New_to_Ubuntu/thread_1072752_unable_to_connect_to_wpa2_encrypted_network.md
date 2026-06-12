---
title: "unable to connect to wpa2 encrypted network"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by yobird42 on 2009-02-17
I just added wpa encryption to my wireless router today and I'm unable to connect. When I try, it says validating connection and doesn't do anything.

I'm using a dlink wua-2340 wireless adapter, drivers from ndiswrapper, and wicd to manage the connection. I have xubuntu hardy.

The router is a dlink gamer lounge dgl-4300 connected to a windows vista computer and managed with network magic.

---

### Post by Paqman on 2009-02-17
From a quick look at D-Link's site it doesn't mention anything about that adaptor supporting WPA2. Can you switch the router to normal WPA?

---

### Post by yobird42 on 2009-02-17
> **Paqman said:**
> From a quick look at D-Link's site it doesn't mention anything about that adaptor supporting WPA2. Can you switch the router to normal WPA?

that's not the problem. I'm using the same computer with windows xp and it's working fine obviously. I'm thinking about changing the router to WEP and see if that works.

---

### Post by yobird42 on 2009-02-18
could someone help me please?

---

### Post by bodhi.zazen on 2009-02-18
I had a lot of trouble personally with wpa and network manager, I struggled with it for over a month.

I installed wicd, and now it works ;)

IMO debugging the problme with network manager is difficult, and so wicd is worth a try.

Wicd is easy to install, and if wicd fails, then we can look at things like manual configuration etc ...

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by stchman on 2009-02-18
> **yobird42 said:**
> I just added wpa encryption to my wireless router today and I'm unable to connect. When I try, it says validating connection and doesn't do anything.

I'm using a dlink wua-2340 wireless adapter, drivers from ndiswrapper, and wicd to manage the connection. I have xubuntu hardy.

The router is a dlink gamer lounge dgl-4300 connected to a windows vista computer and managed with network magic.

WEP is worthless.

What is the chipset on that USB adapter?  I have both an Atheros and Intel wireless cards using my WPA2 connection.

---

### Post by TravisNewman on 2009-02-18
Are you 100% positive that the XP machine isn't autodetecting the appropriate WPA? I've thought the same thing in the past, when the router did not support WPA2

---

### Post by thinking2loud on 2009-02-18
My albeit limited experience is that nm applet is a bummer.  Configure the network manually.  Much more reliable.

---

### Post by yobird42 on 2009-02-19
yes I'm 100% sure. I'm connected manually now, however, so it's no longer an issue.

---

### Post by bodhi.zazen on 2009-02-20
> **yobird42 said:**
> yes I'm 100% sure. I'm connected manually now, however, so it's no longer an issue.

w00t :)

I am happy your problem is solved, to help others can you describe your solution ?

---


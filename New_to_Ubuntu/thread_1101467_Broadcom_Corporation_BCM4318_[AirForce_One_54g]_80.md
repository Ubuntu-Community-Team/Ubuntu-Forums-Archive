---
title: "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by snout71 on 2009-03-20
newbie having problems getting ubuntu recognise my 
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless card

help

---

### Post by clive littlewood on 2009-03-20
Hi

Starting a new thread on the same subject will not gain you any friends and or help.

Be patient  !!!!!!     :D

Clive

---

### Post by snout71 on 2009-03-20
am sorry

it wasnt that i was being impatient, i was trying to attract other thoughts/solutions as i am but a simple minded idiot who shouldnt really own a pc :)

advice taken, 

thanks

---

### Post by lkraemer on 2009-03-20
snout71,
Google and Search are your friends.

Try a search on this forum for BCM4318.  There are lots of HOWTO's.

Also for ref:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

lkraemer

---

### Post by SeePU on 2009-04-19
Well, maybe if you directed the OP to the ANSWER, he wouldn't have to post multiple times.

The Broadcom card is a PITA and still there is no RECENT how-to or should I say, no obvious source or place to find the 'solution.'  

Don't back down to useless replies, OP! 

I have the same card and I'm also looking for a good 'how-to.'

---

### Post by ptn107 on 2009-04-19
I have the same chipset in my Compaq laptop.  System -> Administration -> Hardware Drivers fixed it.

---

### Post by SeePU on 2009-04-19
> **ptn107 said:**
> I have the same chipset in my Compaq laptop.  System -> Administration -> Hardware Drivers fixed it.
So, your wireless works now?

I want to know whether I could use the same wireless card in Ubuntu/Kubuntu/Mint with either WEP or WPA encryption.   I have a Debian distro installed on my Thinkpad that has a mini-PCI wireless c ard with this same Broadcom BCM4318 chipset.  I had all sorts of problems trying to use it with a WEP network but that was my only choice.   None of the Ubuntus are on my Thinkpad yet but I was thinking of installing one.  

I have Kubuntu on my desktop but I use a wireless USB adapter with minimal issues (some disconnections but no big deal).

---

### Post by ptn107 on 2009-04-19
> **SeePU said:**
> So, your wireless works now?

Yes.  Enabling the proprietary drivers in System -> Administration -> Hardware Drivers does the job.  It may require a restart, I can't remember.

---

### Post by lkraemer on 2009-04-20
snout71,
What Distro are you running and what is the Version?

Please re-read post #4 above.
OR
Open a Terminal Window and do:
```

lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig


```
and Post the output.

If you know the routers essid and the correct <interface>,
ie wlan0, ath0, etc.... replace that as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig


```
Post the output of iwconfig above.

lkraemer

---


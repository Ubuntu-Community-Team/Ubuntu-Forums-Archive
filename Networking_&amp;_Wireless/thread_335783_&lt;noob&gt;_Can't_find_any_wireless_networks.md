---
title: "&lt;noob&gt; Can't find any wireless networks"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by again617 on 2007-01-10
I installed Ubuntu on my friend's (relatively new) Acer laptop because the laptop got infected and messed up very quickly.  So I gave him the option of trying Linux.

Except I can't even set up his internet. Using the Network Manager, no available networks are shown.  Running the command-

iwlist eth1 scanning

gives a-

eth1    no scan results

even though I know that I am in range.  Can someone give me some more things to try?

Thanks,

---

### Post by scrooge_74 on 2007-01-10
does iwconfig

gives you the details for the wireless card?

did it got detected and installed properly?

Check this links
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by again617 on 2007-01-10
Yes, it does.

Here is the information:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1    IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

--the link you posted does not solve my problem.

Can I disable the emoticons somehow?

---

### Post by scrooge_74 on 2007-01-10
Did you try using wifi-radar 

are you using any security for the network? if so take it down and try to connect

---

### Post by again617 on 2007-01-10
> **scrooge_74 said:**
> Did you try using wifi-radar 

are you using any security for the network? if so take it down and try to connect

The security is down at the moment.  And I will make an attempt at wifi-radar and let you know how it turns out.

---

### Post by again617 on 2007-01-10
Ok, that took longer then it should have finding and installing wifi-radar but I did it and the results don't look too positive:

eth1      Interface doesn't support scanning : No such device

...is what the terminal window says over and over.

Any other suggestions?

---

### Post by stupidkid on 2007-01-10
Are you sure the driver is correct? Just because iwconfig gives a wireless interface it doesn't mean the driver works.

---

### Post by again617 on 2007-01-10
> **stupidkid said:**
> Are you sure the driver is correct? Just because iwconfig gives a wireless interface it doesn't mean the driver works.

I suppose I'm not sure.  How would I check to see if it is correct?  I did not install a driver manually.  The driver that is being used simply came with the Ubuntu installation.

---

### Post by scrooge_74 on 2007-01-10
google your card or check the manufacturer, someone out there is probably using it or having troubles with it

---

### Post by again617 on 2007-01-10
> **scrooge_74 said:**
> google your card or check the manufacturer, someone out there is probably using it or having troubles with it


I'll do that tomorrow.  Thanks.

---

### Post by stupidkid on 2007-01-11
Actually its better if you google the chipset of the card, which can be found through lspci.

It should be something like

```
Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

---


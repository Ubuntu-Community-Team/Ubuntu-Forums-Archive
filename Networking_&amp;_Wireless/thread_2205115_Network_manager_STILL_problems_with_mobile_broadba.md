---
title: "Network manager STILL problems with mobile broadband"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2014-02-12
I am currently running Lubuntu 12.10, but what follows has occurred on all Ubuntu systems I have used, including the latest stable Lubuntu (13.10). I have a Vodafone K3806-Z USB modem. Network-Manager "sees" it and says it has connected to the Internet, yet I cannot browse or send or receive emails.

As such I have to connect using wvdial or sakis3g. I would like to use Network-Manager though, because (a) connection via sakis3g is very long-winded; (a) both wvdial and sakis3g have their own frustratingly erratic connection difficulties; (b) certain software I use "looks for" a connection via Network Manager (Ubuntu One desktop client).

This is a long-standing problem. I am amazed and disappointed that developers seem to be ignoring it. I have returned to it from time to time hoping that new updates or new insights would provide a solution. No such luck over the past two years at least. This is my latest attempt. 

I am sure someone out there can help me to get Network Manager working with mobile broadband once and for all! (That's a challenge). Please tell me what you need to know.

---

### Post by varunendra on 2014-02-13
The problem (*seems* connected, but can't browse) you mentioned is common for WiFi connections, but for 2G/CDMA/3G modems, this is the first time I've heard of it. Is your connection type one of these?

Can we see the output of -
```
lsusb
```
..along with a description of your connection type and settings in NM?

Perhaps take a look at /var/log/syslog also and post back the parts that look relevant/suspicious?

I think you should follow posts by **[bmork]("http://ubuntuforums.org/member.php?u=1724590")** who seems to be directly involved with the development of the drivers that handle USB serial connections like 2g/3g modems. Maybe PM him and ask to take a look at your problem?

Although as per my personal experience so far, once the connection is established, the behaviour of the connection is dependent on the ISP, but your case may show us another aspect of it..

---

### Post by rdh61 on 2014-02-13
Thank you for your reply. Connection is 3G I think. Output of lsusb:

robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ lsusb
Bus 001 Device 012: ID 19d2:1015 ZTE WCDMA Technologies MSM 
Bus 003 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$

NM settings for this connection: please see attached screenshots.

The syslog file has a great many entries. I am afraid I am not able to interpret it. Shall I attach it?

I'll follow your advice and contact bmork.

---

### Post by varunendra on 2014-02-13
I searched for the APN displayed in your screenshots, and many pages came up, some of which are addressing certain bugs and some others are non-English pages that you can understand better.

But if it is a 3G connection, I think you shouldn't enter anything in the **Username/Password** and **PIN** fields. Was it autoconfigured or did you configure that manually?

Right now I am using Vodafone myself here in India (although currently 2G, but 3G configuration is same) and not only in Vodafone but all 2G/3G connections here only need the Dial Number and APN. Network type depends (usually it is best at "Any", but has to be declared explicitly at some places). Same for "Allow Roaming" - it depends on where I am.

I have kept the username, password and PIN fields blank and I believe it should be same (blank) everywhere for 2G/3G connections.

Does this page relate to your configuration ? : [http://www.squib.it/Apn/apn-gprs-internet-vodafone-italia.asp](http://www.squib.it/Apn/apn-gprs-internet-vodafone-italia.asp)
Or this page? : [http://www.europasim.com/apn-configuration](http://www.europasim.com/apn-configuration)

Both these (and all I have seen so far) have one thing in common - they don't have username/password/pin. I think that is only required by some specific ISPs, and Vodafone is not one of those. But of course I am speaking from the perspective of Indian ISPs, and I may be wrong regarding other countries.

**PS:** You may also experiment with "Allowed Methods" under PPP settings. They do help sometimes. For example, the second link above specifically shows authentication type to be "CHAP". You may try disabling one or more as the Network Manager suggests (in case of problems, when you are sure everything else is correct).

---

### Post by bmork on 2014-02-14
Thanks for the confidence, but I don't think I have much help to offer here.  If it works with wvdial and sakis3g, then it isn't likely to be related to drivers.  And I don't know much about the versions of ModemManager and NetworkManager currently in Ubuntu.

I'd try enabling some debug logging in MM and NM and see if there is something obviously wrong there. But I have no idea what it could be

---

### Post by varunendra on 2014-02-14
> **bmork said:**
> If it works with wvdial and sakis3g, then it isn't likely to be related to drivers.

I fully agree.

And I don't have much idea about debugging either, other than gaping at the syslog/dmesg logs. :P

---

### Post by rdh61 on 2014-02-14
I have looked at various pages on the web, including (now) the ones you point me to. You are right that I should not have entered anything in the user name, password and PIN fields. I have now removed them. I have also tried playing with the other parameters you mention. The only difference made is that changing some of the parameters I get no connection at all. Otherwise, no change: the best I can get is a connection but no web browsing.  It seems quite a few people here in Italy have been having the same problem, but can find no solution except sakis3g and WVdial. But if they can connect and work properly, why not NM?

---

### Post by varunendra on 2014-02-14
> **rdh61 said:**
> ....but can find no solution except sakis3g and WVdial. But if they can connect and work properly, why not NM?

I've no idea. :(

Maybe try its newer versions if available in the repositories (package names are "network-manager" and "network-manager-gnome") and if they have the same problem, submit a bug report at launchpad.

---


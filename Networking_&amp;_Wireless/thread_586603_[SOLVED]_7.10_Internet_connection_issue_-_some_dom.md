---
title: "[SOLVED] 7.10 Internet connection issue - some domains unreachable."
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by jeez on 2007-10-22
Hi,

Using 7.10 (clean install) since past thursday without any problem, I started having connection issues yesterday.

My internet connection is working, but :
* There are domains I can't reach anymore at all (google,...).  Firefox displays "connecting to..." for ten minutes then I get a timeout. Same with Evolution/pop3
* There are domains I can reach, but the pages take forever to load and/or load partially (slashdot.org, ubuntu.com,...  probably because of google-analytics).
* The rest works as usual.

What I did :
* Booted up xp on the same computer : works fine, so I ruled out router, modem and ISP.
* Tried using Epiphany, same results.  Ruled out browser/client software.
* Tried another NIC : no change.
* Checked network config, DNS.  Tried DHCP/static IP.  All the same : no change.
* Ping, traceroute,... :  same results.

The linux environment is still very new to me, so my understanding of its inner workings is quite shallow.  Therefore it is quite possible that I did something that caused the problem, but as far as I remember I didn't install/update anything, nor did modify any config at all. 

I have no clue what to do next. Any help would be greatly appreciated.

Thanks,

Nico

---

### Post by ajgreeny on 2007-10-22
This may not be the answer but try disabling IPv6 in firefox.
In the address bar type **about:config** then in the filter at the top type **ipv6**.
**network.dns.disableIPv6** will show.  Click in that and then right click it and toggle it to **true. ** Now your firefox may work better, but I can't guarantee that is the problem, so if not, my apologies.  Good luck, anyway.

---

### Post by jeez on 2007-10-22
Tried it, no change.
Thank you for the tip.

Cheers, Nico

---

### Post by NilsE on 2007-10-22
Are you by any chance running moblock? or for that matter any other blocking software.

There are a number of people who have had problems in the last few days.

---

### Post by froy02 on 2007-10-22
Check your firefox preferences in Edit, Preferences, Security.   See how they are set.  I set mine to use "Check downloaded list" .  Play with it and may help you solve your problem.  Give it a try.

---

### Post by jeez on 2007-10-22
Thank you Nils, that was it.
I actually thought about moblock before posting here, but since I was unsure if I had installed it or not, I just ran "apt-get remove moblock". Apt told me it wasn't installed, and I ruled moblock out.

The actual name is moblock-nfq, I removed it, and everything works just fine. 
Didn't know moblock was started with the system.

Thanks again, to the three of you..

Nico

---

### Post by NilsE on 2007-10-22
I am glad that solved your problem.  

I can't see where it is installed with the system and it is not in the repos.  That's strange that it showed up for you.

---

### Post by jeez on 2007-10-22
Oops, misunderstanding here.
It was not installed with the system, i installed it myself from the repos.
I meant that I didn't know moblock was running automatically on startup, I thought I had to launch it manually.

Cheers,

N.

---


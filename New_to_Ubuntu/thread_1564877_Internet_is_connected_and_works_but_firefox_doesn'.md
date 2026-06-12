---
title: "Internet is connected and works but firefox doesn't"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by ..sam.. on 2010-08-31
Here is a strange one, the internet connects no worries, I can get on with Arora but Firefox times out?

Not strange you say, well this only happens at my house. Works fine at work.

Any thoughts?

---

### Post by freak42 on 2010-08-31
if firefox works at work but not at home then
check your firefox proxy settings at
edit (menu)->preferences->advanced (top tab)->network (tab)-> Connection Settings (Button) 

It most likely should be set to no proxy or system proxy settings

hth
m

---

### Post by ..sam.. on 2010-08-31
I've got it on no proxy and it works now but very slowly a wont load some pages at all. They just time out.

---

### Post by prshah on 2010-08-31
> **..sam.. said:**
> very slowly a wont load some pages at all. They just time out.

See [ Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution.

Summary hint: Change the MTU (to 1492, or so)

---

### Post by lovinglinux on 2010-08-31
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by ..sam.. on 2010-09-03
lovinglinux you are a genius. That one fixed it.
Worked like a charm.

Just incase that link ever dies, here is it says/said.

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.
Type about:config in the address bar, press Enter.
Find network.dns.disableIPv6 in the list.
Right-click -> Toggle.
Restart Firefox and try again.

Cheers

---

### Post by lovinglinux on 2010-09-03
> **..sam.. said:**
> lovinglinux you are a genius. That one fixed it.
Worked like a charm.

Just incase that link ever dies, here is it says/said.

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.
Type about:config in the address bar, press Enter.
Find network.dns.disableIPv6 in the list.
Right-click -> Toggle.
Restart Firefox and try again.

Cheers

You are welcome. BTW, the site is mine and it is hosted on Google Blogger servers, so it won't die.

---


---
title: "Troubles with Firefox Page Loading"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Hunter Morrell on 2010-07-10
I opened Firefox up earlier to check my usual stuff and thought everything was fine. Well, a few seconds later, the page stopped loading and gave me an error page saying something about "could not connect to server". I just passed it off as just a random thing that wouldn't happen again. Well, its happened numerous times today and its even getting to where the pages won't load correctly. See attached screenies for more detail.

---

### Post by lovinglinux on 2010-07-11
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

---


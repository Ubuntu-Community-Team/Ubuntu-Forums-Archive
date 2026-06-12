---
title: "WiFi connected and active - cannot get any webpage to show up in Firefox."
date: 2010-08-01
forum: New to Ubuntu
---

### Post by GuildedMason on 2010-08-01
SO - thanks to help fromt he forum - it looks as if my WiFi connection is active.

It says active - 100%.

However - I can't get to see anything on Firefox.
(I've checked and I am not in offline mode, also I have 'No Proxy' checked).

Any ideas?

---

### Post by beew on 2010-08-01
You may need to wait a while like I said on the other thread. I experienced the samne thing and after an hour or so it connected nicely and from then it was fine even after reboot.

Another possibility is that maybe your card is damaged. Try  to see if you are getting any packets by pinging if it still doesn't work after an hour or so. I have a computer that had the same problem (windows XP) Connection 100%, signal excellent but just couldn't get online. After checking many forums I decided it was near dead and got an external card instead.

---

### Post by GuildedMason on 2010-08-01
So I tried this - [http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

It didn't work. Although I noticed most of the lines in the were 'commented out' by #.
Is that supposed to be the case?

Still no Internet access ...

---

### Post by GuildedMason on 2010-08-01
OK -- thanks.

I will try that.

---

### Post by lovinglinux on 2010-08-01
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

For future reference, see Firefox [Common Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

---

### Post by GuildedMason on 2010-08-02
Thanks - tried all that ... still no luck.

BTW - the 'How to disable IPv6' link is broken.

I seem to have an IP address when I look at the Wireless COnnection settings.
So that seems fine.

It looks as if I can connect to my SP - but I can't get anything from it ... weird.

Any ideas on troubleshooting this will be GREATLY appreciated.

---

### Post by GuildedMason on 2010-08-02
I've been looking at this - and I don't believe the problem is with Firefos.

Seems to me I have a problem on the actual WiFi connection - although I can't figure out what!!!

It reads me an IP address, Broadcast address, Subnet Mask, Default Route, Promary and Secondary DNS. 

It seems as if the connection is up an running ... but I can't even Ping an address.

I will mark this one as solved and raised another issue with the correct title.

---


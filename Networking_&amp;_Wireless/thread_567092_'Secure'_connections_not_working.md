---
title: "'Secure' connections not working?"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by foundation on 2007-10-04
Okay, so I got my net working (*Yay*!) but now I'm facing another problem, certain *connections* simply won't work, here's some examples:

Any type of secure site, like trying to log into Hotmail, GMail, my ISP (As in the site to check bandwidth usage, etc), Firefox extensions page, etc. Also, I can't log into any IM clients like Pidgin or the like so this isn't a problem restricted to a certain browser but rather with my *whole system*. :(

But what does work is.. well, everything it seems (HTTP, FTP, torrents, etc). **Any ideas?** And thank you for the help people so willingly give on here. :o

Edit: Here is the standard error I receive when trying to access any of the sites I listed just above:
```
Unable to connect

Firefox can't establish a connection to the server at www.google.com.   

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
```Yup, nothing useful. :(

Aside from this and 1 or 2 other small problems I'm loving 7.10, seriously, Canonical has done fairly well.

---

### Post by noob12 on 2007-10-04
Are you running a firewall on the ubuntu host at all?

Are you going straight to a regular router or are you doing some kind of internet sharing from another box?

---

### Post by foundation on 2007-10-04
Umm, no firewall unless there is one present in the default Ubuntu 7.10 install and it's straight from a regular router, I've tried both wired/wirless connections and neither work. Also, when I bought into XP (On the same laptop), the things work.

:(:(

---

### Post by noob12 on 2007-10-05
Have you checked your proxy settings within GNOME under **Preferences | Network Proxy** and within  Firefox under **Edit | Preferences | Advanced | Network | Connection Settings ...** ?

Make sure you don't have an SSL proxy set.  Use direct connection.

---

### Post by ninja0nfire on 2007-10-09
I am having the same problem with a fresh 7.10 install.

GNOME and Firefox are both set for direct connection, no SSL.

:confused:

---

### Post by simonmcf on 2007-10-11
I'm finding the same annoying issue. HTTP works fine. HTTPS results in failed connections.

I performed an update from 7.04 to 7.10 using the method described in the Ubuntu Wiki. All updates have been applied and Update Manager reports "System is up-to-date".

No firewall is in use.

Laptop is ASUS PRO31P series connecting to Internet via wireless connection to DLink DSL G604T running firmware v2.00B02.AU

Trying to download [https://sourceforge.net](https://sourceforge.net) using wget results in:

wget [https://sourceforge.net](https://sourceforge.net)
--08:01:16--  [https://sourceforge.net/](https://sourceforge.net/)
           => `index.html'
Resolving sourceforge.net... 1.0.0.0
Connecting to sourceforge.net|1.0.0.0|:443... 

wget just sits and waits at this point. Firefox times out on any HTTPS connections with status "Unable to connect".

I'm running Firefox 2.0.0.6. Interestingly, firefox will not update as the update option is greyed out. I've manually downloaded 2.0.0.7 and it does not work either.

Interesting fact #2, Windows XP Pro running within VMware Server connects fine to HTTPS sites from the same laptop. Therefore, I suspect something amiss with the Ubuntu 7.10 OS rather than the wireless connection or router or Internet connection.

Simon

---

### Post by simonmcf on 2007-11-05
Bump.

Just tried fresh 7.10 install using Desktop ISO install. HTTPS sites still not working with Firefox 2.0.0.6 on Asus PRO31Pseries. 

Any ideas?

Simon

---

### Post by simonmcf on 2007-11-05
Problem: Secure HTTP (HTTPS) not working in default Ubuntu 7.10 install.

Solution: Disable IPv6 as per:

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Basically either disable IPv6 system-wide or to disable IPv6 in Firefox, do:

1) Type "about:config" (without quotes) into address bar
2) Enter "ipv6" (without quotes) in Filter
3) Change "False" to "True" for value of Firefox setting
4) Try browsing to HTTPS site

Worked for me!

Apparently my laptop, router, etc does not work with IPv6 and this was stopping HTTPS sites from working.

Cheers,

Simon

---

### Post by jeffspen on 2008-01-01
I have the same problem and am unable to connect to any https pages.
Have tried everything mentioned in the last post but still does not work.

I connect using a router and have everything set to direct connection rather than any manual proxys

Help!!

---

### Post by IwarV on 2008-05-07
I too have this problem with secure connections and a power cycle of the router (Netgear RP614v3) always solves the problem.... but for a few hours only. Half a day if I am lucky.

But ONLY for secure connections. Normal unsecure connections always work.

And where a secure connection fails on Ubuntu, the other PC running XP *can* make that connection without any problem using the very same router.

My finger is most definitely pointing at Ubuntu on this one. Disabling IPv6 has not done the trick for me alas. So something else is not working as it should.

Any other tricks are much appreciated. The last resort is to go back to XP.

---

### Post by iwc5893 on 2008-07-16
> **IwarV said:**
> I too have this problem with secure connections and a power cycle of the router (Netgear RP614v3) always solves the problem.... but for a few hours only. Half a day if I am lucky.

But ONLY for secure connections. Normal unsecure connections always work.

And where a secure connection fails on Ubuntu, the other PC running XP *can* make that connection without any problem using the very same router.

My finger is most definitely pointing at Ubuntu on this one. Disabling IPv6 has not done the trick for me alas. So something else is not working as it should.

Any other tricks are much appreciated. The last resort is to go back to XP.

I'm having the same problems, and have tried everything listed in this thread also.

---

### Post by IwarV on 2008-07-16
> **iwc5893 said:**
> I'm having the same problems, and have tried everything listed in this thread also.

Mine seems to be fine now. Although I disabled IPv6 in the documented way I found a few IPv6 remnants in /etc/hosts which I remmed out.

That being said, I am currently not bit-torrenting anymore either and I have read a few posts on slashdot recently from people saying that many routers do not cope well with torrents, so perhaps that was the cause of my router problems.

Short of it: with all IPv6 traces removed and no torrenting my router is behaving itself.

---


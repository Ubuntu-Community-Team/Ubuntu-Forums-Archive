---
title: "Problems accessing certain websites"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Melk79 on 2010-06-04
Since upgrading to Lucid, I'm experiencing strange issues with certain websites.  Gmail, Launchpad, Gnome-Look.org, Firefox Add-Ons, Chrome Add-ons.  Firefox 3.6.3. can't get to Gmail.  Chrome can but it takes a long time.  Firefox can get to Lycos Mail (my old spam and odd website registration account), but Chrome can't.

It seems to be related most with https sites and SSL.  Through all my searching, most people say to clear the cache, etc.  I've done that; doesn't help.  I've tried disabling add-ons.  Nothing.  Turning on SSL 2.0 in Chrome actually got Lycos mail to work.  But I've only been able to get to gmail through Firefox by pulling out their certificate and adding an exception.  But that doesn't work very well because Firefox thinks it doesn't need the exception and then it fails again... 

The error message is usually 'Connection Interrupted.'  When I disable SSL 3.0 in Firefox that changes to an SSL error.  My Windows XP machine can get to everything fine with IE, Firefox and Chrome.  I actually had to use Windows and IE to upload an icon to Gnome-Look last night... please help!


Anyone else experiencing these web browsing problems?  It's a tough item to search on and most returns are from years back.  I did find out ESPN3 doesn't work because I'm running 64-bit and they don't support that.  I have a D-Link DIR-615 router and these issues have occured with both Ubuntu and Kubuntu 10.04 (both 64-bit).

---

### Post by wojox on 2010-06-04
Type in the url

```
about:config
```

Enter in the filter search

```
ipv6
```

Change it to **true** and restart firefox

Also look here [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by ThesaurusRex on 2010-06-04
Did you try a reinstall of Firefox or Chromium? It certainly shouldn't be a method you go to immediately, but sometimes it does work (especially after an upgrade).

---

### Post by Melk79 on 2010-06-04
I tried the IPV6 change and it had no effect.  I've also tried re-installing to no effect either.  Thanks for the suggestions.  Any other ideas? 

Both Ubuntu installs experiencing this are clean installs as well, so there shouldn't be any hanging on profile settings or anything.

---

### Post by lovinglinux on 2010-06-04
> **Melk79 said:**
> I tried the IPV6 change and it had no effect.  I've also tried re-installing to no effect either.  Thanks for the suggestions.  Any other ideas? 

Both Ubuntu installs experiencing this are clean installs as well, so there shouldn't be any hanging on profile settings or anything.

Have you tried a different DNS server?

Try [Google DNS]("http://code.google.com/speed/public-dns/") or [OpenDNS]("http://www.opendns.com/").

---

### Post by Linicks on 2010-12-30
This issue is caused by MTU size.  Change it to a value of 1454.

Connect to the internet, and do:

sudo ifonfig {interface} mtu 1454

{interface} is what you are using, i.e. eth0, ppp0 etc.

then start firefox and you will find gmail et al now loads and works fine.

Nick

---


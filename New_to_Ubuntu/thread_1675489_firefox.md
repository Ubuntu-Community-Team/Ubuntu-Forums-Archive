---
title: "firefox"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by msidhard on 2011-01-25
hi
  my firefox or chrome is unable to open some web sites it loads the page even for hours but not opening the page at all and saying that "waiting for ....." like things while trying to load the page.

---

### Post by cgroza on 2011-01-25
If other sites work OK, give us the address so we can test if the problem is your computer or the server.

---

### Post by msidhard on 2011-01-26
it says like
 "waiting for ad.yieldmanager" - when trying some othersites 
 "waiting for ulavu.com"       - when trying to open [www.ulavu.com](www.ulavu.com) "transferring data from a.fsdn.com" - when trying to open [www.sourceforge.net](www.sourceforge.net)
"connected to s-static.ak.facebook.com" - when trying to open the URL [https://login.facebook.com/login.php?login_attempt=1](https://login.facebook.com/login.php?login_attempt=1)

"connected to s-static.ak.facebook.com" - when trying to open the URL
[https://www.facebook.com/recover.php](https://www.facebook.com/recover.php)

etc,etc

---

### Post by zwubber on 2011-01-26
> **msidhard said:**
> it says like
 "waiting for ad.yieldmanager" - when trying some othersites 
 "waiting for ulavu.com"       - when trying to open [www.ulavu.com]("http://www.ulavu.com") "transferring data from a.fsdn.com" - when trying to open [www.sourceforge.net]("http://www.sourceforge.net")
"connected to s-static.ak.facebook.com" - when trying to open the URL [https://login.facebook.com/login.php?login_attempt=1](https://login.facebook.com/login.php?login_attempt=1)

"connected to s-static.ak.facebook.com" - when trying to open the URL
[https://www.facebook.com/recover.php](https://www.facebook.com/recover.php)

etc,etc
I visited the sites you listed,
but all the sites works for me.

---

### Post by wojox on 2011-01-26
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.

    * Type about:config in the address bar, press Enter.
    * Find network.dns.disableIPv6 in the list.
    * Right-click -> Toggle.
    * Restart Firefox and try again.


You can also disable ipv6 on the system level. To do that, open the file /etc/default/grub with an editor:

gksudo gedit  /etc/default/grub

Then replace the following line:

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

With the following line:

GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”

Then update grub:

sudo update-grub

[<webgapps>]("http://www.webgapps.org/firefox/issues-and-solutions")

---

### Post by hannodewind on 2011-01-26
Same problem here...I've tried the IPv6 disable, it is unfortunately not working.

Also, I've tried to ping [www.google.com](www.google.com) and ubuntu.com from System-Administration-Network tools. That does not work. Pinging the same sites from terminal does work though. The updare manager and software centre can also connect with decent speeds.

---

### Post by hannodewind on 2011-01-26
Hi,

Check out [http://ubuntuforums.org/showthread.php?t=1675643](http://ubuntuforums.org/showthread.php?t=1675643).

I had the same problem, I posted a solution that worked for me there. Are you using a DSL connection? Otherwise that might not help you...

---


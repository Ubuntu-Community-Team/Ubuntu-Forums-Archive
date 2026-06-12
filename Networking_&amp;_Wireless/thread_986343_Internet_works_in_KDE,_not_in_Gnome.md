---
title: "Internet works in KDE, not in Gnome"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2008-11-18
I installed gnome-desktop on a Kubuntu installation and whenever I logout and switch session types I get a warning when I log in about my $HOME/.dmrc file being ignored, telling me my permissions should be 644, I chmoded the whole ~ directory, then found I couldn't cd into it! So.. I chmoded it to 777, which I guess was not the best thing in the world.

Anyway, whether or not it's related to that, I cannot use the internet in Gnome. Both Firefox and Opera just churn away hopelessly trying to connect to any page I open. I can, however, access my router interface. I guess some kind of Gnome-specific DNS setting is absent, but what?

---

### Post by pickarooney on 2008-11-19
Any ideas about this gnome DNS(?) issue?

---

### Post by MockY on 2008-11-19
I always suggest that NetworkManager should be replaced. By installing Wicd, you will exclude error or issues caused by NM. I'm not saying it will fix your problem, but you can at least remove NM out of the equation.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by superprash2003 on 2008-11-19
post output of cat /etc/resolv.conf from the terminal.. also post output of ping google.com

---

### Post by pickarooney on 2008-11-19
resolv.conf says this:
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5357
#
### END INFO



nameserver 192.168.1.1
```

It was last updated in June.

Pinging google works and also putting the numeric address of google.com into firefox brings me to the right page.

The nameserver in that file above is the address of my router, on which DNS is activated (it works in KDE just fine).

One other thing, after closing FF and logging out, then logging in again to KDE, opening FF brought me to [http://72.14.207.99](http://72.14.207.99) instead of [www.google.ie](www.google.ie), my normal homepage. For what that's worth. I'll give wicd a shot next.

---

### Post by pickarooney on 2008-11-19
Tested again ther e- after about 6 minutes Opera finally loaded a page, but Firefox was still cycling in thin air. Curiously it didn't time out or display an error page, just kept trying unsuccessfully to load up.

If I install this wicd thing, is it likely to upset my KDE internet connectivity?

[edit]wicd made no difference. FWIW, lynx seems to be working fine in GNOME!

---

### Post by pickarooney on 2008-11-19
I tried installing seamonkey and galeon - same problem
From the command line, if I run firefox (or any other graphical browser) I get this:

```

/usr/lib/libkdeui.so.4: undefined symbol:
_ZN7KGlobal23unregisterStaticDeleterEP18KStaticDeleterBase
/usr/lib/kde3/plugins/styles/baghira.so could not be unloaded

** (galeon:17724): WARNING **: I could not load the bookmarks file, will
load the default bookmarks from
/usr/share/galeon/default-bookmarks.xbel.

** (galeon:17724): CRITICAL **: radio_group_set_from_value: assertion
`action != NULL' failed
galeon: symbol lookup error: /usr/lib/libkdeui.so.4: undefined symbol:
_ZN7KGlobal23unregisterStaticDeleterEP18KStaticDeleterBase

```

Not sure why it's trying to run Baghira-related stuff on Gnome... ? Or if this is related to the issue.

---

### Post by superprash2003 on 2008-11-20
i think changing your DNS servers to opendns may help . [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by pickarooney on 2008-11-20
No, that didn't help.
It's almost as though applications in Gnome were trying to load or use KDE components (baghira theme, KDE DNS tool??) but I don't understand why they would do that.

---

### Post by pickarooney on 2008-11-20
I ran Opera with the -debugdns flag and got the following output when connecting to my provider's homepage.

```
: Resolving 'sitecheck2.opera.com'
dns: Trying IPv6 lookup for host 'sitecheck2.opera.com'...
dns: Thread created
dns: Resolving 'www.orange.fr'
dns: Trying IPv6 lookup for host 'www.orange.fr'...
dns: Thread created
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'sitecheck2.opera.com'...
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'www.orange.fr'...
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'sitecheck2.opera.com' resolved to 213.236.208.60
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'www.orange.fr' resolved to 193.252.122.103
dns: Resolving 'i5.woopic.com'
dns: Trying IPv6 lookup for host 'i5.woopic.com'...
dns: Thread created
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'i5.woopic.com'...
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'i5.woopic.com' resolved to 193.252.149.29
dns: Resolving 'orange.fr'
dns: Trying IPv6 lookup for host 'orange.fr'...
dns: Thread created
dns: Host name lookup of 'orange.fr' cancelled
dns: Resolving 'rc.production.orangeads.fr'
dns: Trying IPv6 lookup for host 'rc.production.orangeads.fr'...
dns: Thread created
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'orange.fr'...
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'orange.fr' resolved to 193.252.122.103
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'rc.production.orangeads.fr'...
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'rc.production.orangeads.fr' resolved to 193.252.121.71
dns: Resolving 'orange.weborama.fr'
dns: Trying IPv6 lookup for host 'orange.weborama.fr'...
dns: Thread created
dns: Resolving 'ad.fr.doubleclick.net'
dns: Trying IPv6 lookup for host 'ad.fr.doubleclick.net'...
dns: Thread created
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'orange.weborama.fr'...
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'orange.weborama.fr' resolved to 217.117.154.5
dns: gethostbyname failed with return value 22 (Invalid argument).
hostent pointer:(nil)
dns: Trying IPv4 lookup for host 'ad.fr.doubleclick.net'...
dns: gethostbyname succeeded
dns: Host name lookup completed with error code 0
dns: Host 'ad.fr.doubleclick.net' resolved to 209.62.179.57
dns: Resolving 'view.atdmt.com'
dns: Trying IPv6 lookup for host 'view.atdmt.com'...
dns: Thread created
dns: Resolving 'fluxlc.orange.fr'
dns: Trying IPv6 lookup for host 'fluxlc.orange.fr'...
dns: Thread created

```
I did eventually connect, after about 2 minutes.

I can't find a similar debug switch for firefox though and it does not connect at all, to anything.

---

### Post by pickarooney on 2008-11-22
Small update: Skype and MSN connect with no problem on Gnome. I also found the following in my /etc/hosts file, but don't know if it's of relevance - it seems to be used by KDE as well. 

If I can't get this resolved, is there a way I can re-install Gnome without formatting and thus having to reinstall KDE (I'm not completely adverse to the latter, I'd just rather not do it if there's a quicker solution)?

hosts
```

127.0.0.1 localhost
127.0.1.1 marklar.home marklar

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---


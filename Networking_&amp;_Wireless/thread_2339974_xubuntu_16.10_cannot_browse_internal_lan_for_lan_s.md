---
title: "xubuntu 16.10 cannot browse internal lan for lan storage.  Name or service not known."
date: 2016-10-14
forum: Networking &amp; Wireless
---

### Post by craymore on 2016-10-14
xubuntu 16.10 cannot browse internal lan for lan storage.  Name or service not known.

Error resolving 'MyBookWorld.local' Name or service not know.  stock xubuntu 16.10 and fully updated only canonical repos and only this error.  all my static ip settings are correct for my lan.  Gigolo further did not show the device or other network computers and further could not connect.

thanks

please can anyone help in getting a correct solution.  thanks

if it was released like this with a bug so severe how could they ?

---

### Post by richbl on 2016-10-17
If I understand your question properly, you cannot resolve your local hostnames. That is, when you attempt to ping (or ssh, etc.) you get an error:

[B]richbl@huey:~$ ping backup.local
ping: backup.local: Name or service not known[/B]

On that, I had the same problem with a fresh install of Ubunu Gnome 16.10, and it turns out to be a known issue ([https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1624071](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1624071)) related to libnss-resolve in systemd.

The solution in my case was to review /etc/nsswitch.conf file and note specifically how NSS resolves your hosts:

```
hosts: files resolve [!UNAVAIL=return] mdns4_minimal [NOTFOUND=return] dns myhostname
```

This logic appears to fail hostname resolution before even getting to mDNS.

Editing the hosts line back to a pre-16.10 release fixes this apparent logic error:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns myhostname
```

The included bug-report link suggests a future release of of the systemd package may eventually correct this problem.

Rich

---

### Post by Morbius1 on 2016-10-17
And as a side benefit it also fixes the problem with cups-browsed: [https://ubuntuforums.org/showthread.php?t=2340042&p=13557627#post13557627](https://ubuntuforums.org/showthread.php?t=2340042&p=13557627#post13557627)

In my case I didn't remove  [COLOR=#000000]"resolve [!UNAVAIL=return]" I just put [/COLOR]"mdns4_minimal [NOTFOUND=return]" in front of it.

---

### Post by ian-weisser on 2016-10-17
> **craymore said:**
> if it was released like this with a bug so severe how could they ?
More pre-release testers are always welcome: [https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)

---

### Post by Morbius1 on 2016-10-18
> **ian-weisser said:**
> >                      [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **craymore**                     [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13556715#post13556715")                 

                 if it was released like this with a bug so severe how could they ?
                            More pre-release testers are always welcome: [https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)More pre-release testers are always welcome: [https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)

[1] There were warnings about this months ago: [Sad news today: systemd-resolved to be deployed in Ubuntu 16.10 ]("https://lists.dns-oarc.net/pipermail/dns-operations/2016-June/014964.html")

[2] In what can only be descibed as ironic so was systemd's creator: [order systemd-resolved.service before nss-lookup.target]("https://github.com/systemd/systemd/issues/848") 
[COLOR=#0000ff]*"Ironic" because the father of both systemd and avahi is Mr. Poettering*[/COLOR]

[3] The original poster lists his involvement with Ubuntu going back to March of 2013 so this can't be the first time someone hasn't suggested this before:

Non-LTS releases are "technology previews" not something anyone is expected to install and use on a daily basis except for testing purposes and to give you an early preview of what the next LTS release will look like.

---


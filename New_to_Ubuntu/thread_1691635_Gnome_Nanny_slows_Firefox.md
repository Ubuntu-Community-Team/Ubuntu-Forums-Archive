---
title: "Gnome Nanny slows Firefox"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by zangler on 2011-02-20
Please can anyone offer help?  I have a relatively new installation of Edubuntu 10.10 on a laptop used by my little darlings who want to access various child friendly websites.  I have activated Nanny and added a blacklist of sites to be blocked.  Problem is, when my LDs want to visit a site, Firefox takes an eternity to download the requested page.

To troubleshoot, I logged in as admin and deactivated Nanny, then visited same sites - very rapid response.

Now I know that Nanny has to do some checking of the site against the blacklist, but surely it should have a minimal impact on download times, etc.

Any ideas?

Thanks.

---

### Post by Souptik on 2011-02-20
> **zangler said:**
> Please can anyone offer help?  I have a relatively new installation of Edubuntu 10.10 on a laptop used by my little darlings who want to access various child friendly websites.  I have activated Nanny and added a blacklist of sites to be blocked.  Problem is, when my LDs want to visit a site, Firefox takes an eternity to download the requested page.

To troubleshoot, I logged in as admin and deactivated Nanny, then visited same sites - very rapid response.

Now I know that Nanny has to do some checking of the site against the blacklist, but surely it should have a minimal impact on download times, etc.

Any ideas?

Thanks.

It may not be a problem with firefox or nanny after all. The problem can be at any point from your network connection to the host server.. do all sites behave in the same way ??

---

### Post by SeijiSensei on 2011-02-20
The [project page for Nanny]("http://projects.gnome.org/nanny/") has to be one of the most useless I've ever seen.  Nowhere does it say anything about how Nanny works.  If it's just comparing URLs to a black list of strings, it should be instantaneous.  However if it has to check upstream with some servers to determine whether a page is acceptable, maybe the connectivity with those servers is poor.  

You might want to take a look at [Dan's Guardian]("http://www.dansguardian.org/"), though I think you'd need another PC to run it.  It's more a proxy server than an application you run on a workstation.

You could also consider [OpenDNS Basic]("http://www.opendns.com/start/") as an alternative.

---

### Post by zangler on 2011-02-20
> **Souptik said:**
> It may not be a problem with firefox or nanny after all. The problem can be at any point from your network connection to the host server.. do all sites behave in the same way ??

Yes.  I have a 4 port router to which I have a Windoze desktop PC and a Ubuntu Studio 10.10 desktop PC connected and the laptop running Edubuntu 10.10 is connected (wired) when required.  Response times for both desktops is fine, as are response times for the laptop when parental controls are removed.  Turn on Nanny and the response times become very sluggish. :confused:

---

### Post by zangler on 2011-02-20
> **SeijiSensei said:**
> The [project page for Nanny]("http://projects.gnome.org/nanny/") has to be one of the most useless I've ever seen.  Nowhere does it say anything about how Nanny works.  If it's just comparing URLs to a black list of strings, it should be instantaneous.  However if it has to check upstream with some servers to determine whether a page is acceptable, maybe the connectivity with those servers is poor.  

You might want to take a look at [Dan's Guardian]("http://www.dansguardian.org/"), though I think you'd need another PC to run it.  It's more a proxy server than an application you run on a workstation.

You could also consider [OpenDNS Basic]("http://www.opendns.com/start/") as an alternative.

Thanks for the suggestions.  Agreed the project page for Nanny sucks and there doesn't appear to be much in the way of help notes within the application.  I'll take a longer look at Dan's Guardian and OpenDNS, but at first glance they seem far too advanced for a ubuntu novice.

---

### Post by Souptik on 2011-02-20
> **zangler said:**
> Yes.  I have a 4 port router to which I have a Windoze desktop PC and a Ubuntu Studio 10.10 desktop PC connected and the laptop running Edubuntu 10.10 is connected (wired) when required.  Response times for both desktops is fine, as are response times for the laptop when parental controls are removed.  Turn on Nanny and the response times become very sluggish. :confused:

Then I think the problem is with the Nanny thing. Just do as SeijiSensei has posted..
Here's the link on ubuntu forums about Dan's Guardian :-

[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

Best of Luck !!!

---

### Post by oldos2er on 2011-02-20
OpenDNS is fairly easy to setup on Ubuntu: [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

### Post by zangler on 2011-02-20
Thank you for the link oldos2er - I followed it and it seems to be working a treat!

Thanks all for your help.

---


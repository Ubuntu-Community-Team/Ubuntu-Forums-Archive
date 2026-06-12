---
title: "Missing netstat options, oh where, oh where have they gone?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by PadreSol on 2008-06-25
Hello peoples,

I was writing a small wrapper using netstat and I noticed that the hostnames were getting truncated in the output.  I found an online manual for netstat that had a --wide or -W for a wider display but my netstat doesn't have that.

We are using some old, old, stuff, what's gone wrong? 2001? 


netstat -V
net-tools 1.60
netstat 1.42 (2001-04-15)


cat /etc/issue
Ubuntu 8.04 \n \l

---

### Post by jetsam on 2008-06-25
I think that's the most recent version of the GPL netstat.  The homepage of the net tools project which contains netstat is here:
[http://net-tools.berlios.de/]("http://net-tools.berlios.de/")

Netstat has a bunch of different versions.  There's a version for Solaris, one for BSD.  Windows even has one with a completely different set of options.  The web page you were looking at may have been for one of these other versions.

---

### Post by jetsam on 2008-06-26
Not sure if this could be helpful or not for you:
```
sudo lsof -i
```
..seems to list all established and listening internet connections and doesn't truncate hostnames like netstat.

---

### Post by PadreSol on 2008-06-26
> **jetsam said:**
> I think that's the most recent version of the GPL netstat.  The homepage of the net tools project which contains netstat is 


The package was recently put up for adoption and someone has volunteered.
If I can figure out how to file an enhancement request I guess I'll do that.

If not I'll roll my own I guess.

> **jetsam said:**
>  The web page you were looking at may have been for one of these other versions.

It's linux (don't know what flavor):

[http://linuxreviews.org/man/netstat/](http://linuxreviews.org/man/netstat/)

---

### Post by PadreSol on 2008-06-26
> **jetsam said:**
> Not sure if this could be helpful or not

Yes, but that one truncates the command. All for the sake of formatting.  I'll take all the data and bad formatting any day. (^;

lsof has so many options, I'm checking to see if it has a long or wide or something flag to show everything.

FWIW, here's the bug announcing the orphan of nettools:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486004](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486004)

---

### Post by jetsam on 2008-06-26
Very strange that the "man on the web" page you linked to is from before this release of netstat:  "Updated: 19 December 2000."  Was the feature taken out?

> lsof has so many options, I'm checking to see if it has a long or wide or something flag to show everything.

...it's a truly awesome number of options.  I couldn't find the one you want, though...

If you haven't seen this yet, you'll probably be interested in this debian bug report on exactly this issue:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=222324]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=222324")

There's a patch in it for netstat that wasn't adopted that adds the --wide option.

---

### Post by PadreSol on 2008-06-26
Well something doesn't add up for sure.  Maybe the new maintainer will be responsive.  I think so many people rely on the basic tools that they should get more attention.

---


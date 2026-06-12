---
title: "Firefox"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by Masru on 2011-08-12
I'm using UBUNTU 11.04. In the firefox does not open many sites, even [www.ubuntuforums.org](www.ubuntuforums.org), [www.iucaa.ernet.in](www.iucaa.ernet.in), and many other site. Now I'm using Opera. What is the problem behind that. Anyone has any solution???

---

### Post by LowSky on 2011-08-12
We need more information.

There is no reason a Browser would block websites and another would allow them unless you setup security blocks in one of them... Check your Preferences in Firefox. You possibly have them set too high.

---

### Post by jerrrys on 2011-08-12
have you installed "ubuntu restricted extras"?  this will not fix all your troubles, but will help.

---

### Post by LowSky on 2011-08-12
> **jerrrys said:**
> have you installed "ubuntu restricted extras"?  this will not fix all your troubles, but will help.

installing that will not help with accessing internet sites. All it does is install mp3, flash, Microsoft fonts, and a few video codecs. NOTHING to do with internet access.

---

### Post by cgroza on 2011-08-12
Long shot here:
Check the firefox file menu and see if it set on work offline.

---

### Post by Furball588 on 2011-08-12
My initial thought since Opera works is to set network.dns.disableIPv6 to true through abut:config.

LowSky is right though...we need a little more information then just a random rant

---

### Post by Furball588 on 2011-08-13
> **jerrrys said:**
> URE is a necessary package

And that is true...

If I wanted to watch videos or maybe some sort of streaming media via flash...

For accessing [www.ubuntuforums.org](www.ubuntuforums.org) as they stated in the beginning and probably one of the most vanilla operating sites around...I don't see anything in there that will assist in this area.

---

### Post by The Cog on 2011-08-13
LowSky is right. Although ubuntu-restricted-extras is a useful package, its absence will not prevent access to web sites like ubuntuforums.org. There is something else going on.

Checking that it's not set for work offline, and maybe disabling ipv6 are worth trying. Otherwise we do need more info, such as:
* Do any sites work in firefox?
* What does firefox say when you try the non-working sites?
* Do you use a proxy?

---

### Post by ofnuts on 2011-08-13
Is there a proxy configured in either Firefox or Opera?

---

### Post by Masru on 2011-08-19
> **The Cog said:**
> LowSky is right. Although ubuntu-restricted-extras is a useful package, its absence will not prevent access to web sites like ubuntuforums.org. There is something else going on.

Checking that it's not set for work offline, and maybe disabling ipv6 are worth trying. Otherwise we do need more info, such as:
* Do any sites work in firefox?
* What does firefox say when you try the non-working sites?
* Do you use a proxy?


My firefox is not working offline. There is no problems for many other sites.

Firefox continue loading when I try to open non-working sites, but it doesn't load, whereas in opera it works fine..

What is proxy???

This problem happens with chromium browser too.. What could the problem?? Firefox and chromium works fine in windows..

---

### Post by corncob on 2011-08-19
Last month my friend's firefox suddenly decided it wasn't going to access websites.  I fixed the problem by upgrading to the latest version.  I imagine a simple reinstallation would have worked too.  I don't know about Chromium though -- that throws a different light on the situation.

---

### Post by Masru on 2011-10-04
> **The Cog said:**
> LowSky is right. Although ubuntu-restricted-extras is a useful package, its absence will not prevent access to web sites like ubuntuforums.org. There is something else going on.

Checking that it's not set for work offline, and maybe disabling ipv6 are worth trying. Otherwise we do need more info, such as:
* Do any sites work in firefox?
* What does firefox say when you try the non-working sites?
* Do you use a proxy?
The problem is that, when I get in to "www.ubuntuforums.org" it keeps on loading it never comes to open. It is opening in Opera browser. When I tried with DEBIAN same problem is going on(both in mozilla Iceweasel and Epiphany). 

Not only this site many other sites: when I search through google some links does not open for ever, it keeps on loading. All these links open in Opera. Whan I tried FEDORA (Mozilla firefox is the browser)there all are fine. Could there be any problem in configuration or any other??
What is really going on with these????

---

### Post by Torisuna on 2011-10-04
I know this will come across weird  but  I was having the same problem accessing with fire fox when I upgraded to 11.04. I traced my problem to my router's NAT setting. My router was set to a NAT setting of 4 (which I never checked before then) When I switched to NAT 1 fire fox ran with no problem. Maybe your in the same boat I was, just a thought.

---

### Post by corncob on 2011-10-05
> **Torisuna said:**
> I know this will come across weird  but  I was having the same problem accessing with fire fox when I upgraded to 11.04. I traced my problem to my router's NAT setting. My router was set to a NAT setting of 4 (which I never checked before then) When I switched to NAT 1 fire fox ran with no problem. Maybe your in the same boat I was, just a thought.

What are NAT settings?  I can't find anything like that in my Netgear N300.

---

### Post by Johnb0y on 2011-10-05
> **corncob said:**
> Last month my friend's Firefox suddenly decided it wasn't going to access websites.  I fixed the problem by upgrading to the latest version.  I imagine a simple re-installation would have worked too.  I don't know about Chromium though -- that throws a different light on the situation.

+1 worked for me. 

p.s. didn't really like the one that comes as standard, so i removed it and got the one from Firefox site - and then ran updates... don't forget updates...lol!

---


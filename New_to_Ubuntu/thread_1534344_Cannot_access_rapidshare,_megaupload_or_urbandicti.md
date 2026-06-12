---
title: "Cannot access rapidshare, megaupload or urbandictionary"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by wishingstar on 2010-07-19
Hi,

I'm running ubuntu lucid on a fresh install, with the latest upgrades through the update manager. Since i installed ubuntu i cannot access the following sites:

rapidshare.com
megaupload.com
urbandictionary.com

I don't know what these sites have in common, since i haven't noticed any problems with other websites (other file hosts like hotfile, mediafire and the likes have no problem). When i tried to ping rapidshare.com, i got an "unknown host" message.

Please help, as i have a rapidshare premium account, and i would hate to have to install xp on vm just for that.

Thanks in advance.

---

### Post by Paqman on 2010-07-19
Where are you accessing the internet from? Does the network filter content at all?

---

### Post by mikechant on 2010-07-20
I'm sure this is some sort of filtering. These sites are all blocked for me at work (on Windows) and I'm sure they would work at home on Ubuntu.

However, it's *possible* that the filtering proxy or whatever it is inspects your browser type and behaves differently (i.e. is more permissive) with known/approved browsers than unknown/unapproved browsers.

Assuming you're using Firefox you could use the 'user-agent switcher' addon to make it pretend to be IE on Windows and see if that makes any difference.

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

However, *if* these restrictions are being imposed as a matter of policy at some workplace/educational establishment, (no matter how stupid they are), any attempt to circumvent these restrictions could result in disciplinary action etc. and I would not recommend risking this.

---

### Post by NT4usB on 2010-07-20
Rapidshare works fine with Ubuntu and Firefox. I don't have an account but have accessed it in the past.
Sounds like a DNS issue. For whatever reason, the servers you're using don't want to resolve rapidshare.
You  could try different DNS server or, if you can resolve the IP address of rapidshare, connect using the IP

---

### Post by danuka_d on 2010-07-22
Try premium link generator so that no restrictions apply, from MU or ISP.
[http://www.megauploadpremiumlinkgenerator.org](http://www.megauploadpremiumlinkgenerator.org)

---

### Post by Mark Phelps on 2010-07-23
I'm using Ubuntu 10.04 and accessing RS with no problems.

To rule out DNS problems, use the following IP for RS: 195.122.131.8

---

### Post by wishingstar on 2010-12-10
Hi all, thanks for all the feedback, I'm bumping this again since the problem persists. Ubuntu 10.04 with firefox 3.6.12 (latest), or chromium (latest) even opera and midori (all latest updates). So it's not a browser problem, it's an issue with ubuntu itself.

I've been able to circumvent the problem by logging onto rapidshare from an XP installation in Virtualbox, but that is not really a solution.

The other day, I started having the same problem with another file host (hotfile.com). I'm connecting from home, so there are really no restrictions in effect here. I've tried User-agent-switcher, but it didn't help. 

I'm wondering if there are any new developments that could solve this issue for good, and Mark, how can I change the IP address for only one website?

Thanks all,
WishingStar
__

---

### Post by wishingstar on 2010-12-10
Update:

I could partially access rapidshare and hotfile after some tinkering with the hosts.allow file.
I added the following lines:
[code]
ALL: .rapidshare.com
ALL: .hotfile.com
ALL: @ns2.easydns.com
ALL: @209.200.151.4
ALL: @ns1.easydns.com
ALL: @216.220.40.243
ALL: www.hotfile.com
[#code]

I was finally able to access the websites, but only if i remove "www." from the address...weird right?

---

### Post by thatguruguy on 2010-12-10
> **wishingstar said:**
> Update:

I could partially access rapidshare and hotfile after some tinkering with the hosts.allow file.
I added the following lines:
[code]
ALL: .rapidshare.com
ALL: .hotfile.com
ALL: @ns2.easydns.com
ALL: @209.200.151.4
ALL: @ns1.easydns.com
ALL: @216.220.40.243
ALL: www.hotfile.com
[#code]

I was finally able to access the websites, but only if i remove "www." from the address...weird right?

Wait a minute.  Have you had your "hosts.allow" and "hosts.deny" files set up all this time?  Could you post the contents of those files here?

---

### Post by wishingstar on 2010-12-10
> **thatguruguy said:**
> Wait a minute.  Have you had your "hosts.allow" and "hosts.deny" files set up all this time?  Could you post the contents of those files here?

Actually no, I just edited hosts.allow for the first time today, i found a tip on google about it, other than the lines i just posted above, I never even knew these files existed!

One more thing, I tried to comment out the lines in hosts.allow, I could still access both hotfile.com and rapidshare.com. However, for each I had to remove "www." from the address in order to get in!

---

### Post by wishingstar on 2011-01-26
Hello all,

I am removing the [Solved] from the title and bumping this thread, I  recently switched to maverick and the problem is back again, and this time, even changing the hosts.allow file did not help! I can access rapidshare.com (after manually removing www. from the url) but I can't access hotfile, megaupload or urbandictionary :'(

I guess i'm back to Virtualbox until I can find a new solution for maverick :(

Any thoughts?

---

### Post by wishingstar on 2011-02-06
Bump!

---


---
title: "DNS resolution problem, how do I SWITCH DNS sources?"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by phubert28 on 2011-01-31
This morning I'm finding that all MY references (AND Google AND Bing searches) for Computerworld UK (including my BOOKMARK for the site) are returning a corrupted:

[www.computerworlduk.com](www.computerworlduk.com) instead of the correct [www.computerworld.co.uk.com](www.computerworld.co.uk.com).

When someone else PROVIDES me the correct link in the [www.varlinux.org](www.varlinux.org) FishBox or in a story post, it ends up being corrupted.

Now, is this a DNS issue or is my SYSTEM doing something strange?????

I've edited my bookmark entry and it's now correct. But even if I KEY the correct value for a new tab, it then generates a WOT (web of trust) warning and then goes directly to a blank page.

When I mouseover the TAB for that page, I see a Google reference to parked domains!

Any ideas?????

I am using OpenDNS. COULD that be the source of the problem?

Our petroleum engineer member in Brazil isn't having a problem, haven't heard from anyone else yet.

How do I CHANGE my DNS provider????

---

### Post by kittkatt on 2011-01-31
Is this only happening with Computerworld?  Try other non-related websites and see if you are still experiencing problems.  If its only Computerworld that is causing you problems, its likely due to something on their end rather than something with you.  

You change your DNS provider by going into your router settings and trying to look for the DNS settings (you will see a primary and secondary DNS address). You then change those addresses to another DNS provider that you wish to use.  OpenDNS [has picture tutorials]("https://store.opendns.com/setup/router/") for most common router brands.  The problem is likely not with OpenDNS though since a compromise of their systems would have quickly made big news.

---

### Post by phubert28 on 2011-01-31
So far, it seems to be ONLY Computerworld UK.
I found it especially odd that my BOOKMARK link was similarly corrupted as are all my Google (and tried Bing, too) searches whether from Chrome or Firefox.

Also, when anyone POSTS a good link, when I COPY it the copied version is corrupted!!!

But even keying the right url gets me to a Google reference to parked domains.

Good point about OpenDNS. This had me thinking about the Obama administrations desire for an Internet "kill switch" ... testing the kill of 'undesirables' perhaps? I'm sure Glyn Moody isn't the favorite of a number of corporations...

I know, crazy thoughts. There are times I wish I'd been a Network Admin rather than a mainframe/mini/Windows (ugh) server admin... never got to do the DNS stuff that much.

**

AND I realize there likely are TOO MANY times I ask questions I SHOULD know the answer to.

Thanks for the response!

> **kittkatt said:**
> Is this only happening with Computerworld?  Try other non-related websites and see if you are still experiencing problems.  If its only Computerworld that is causing you problems, its likely due to something on their end rather than something with you.  

You change your DNS provider by going into your router settings and trying to look for the DNS settings (you will see a primary and secondary DNS address). You then change those addresses to another DNS provider that you wish to use.  OpenDNS [has picture tutorials]("https://store.opendns.com/setup/router/") for most common router brands.  The problem is likely not with OpenDNS though since a compromise of their systems would have quickly made big news.

---


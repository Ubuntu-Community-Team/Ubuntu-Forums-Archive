---
title: "Ubuntu as simple workstation - I need some basic advise!"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by flameproof on 2014-04-07
I need some basic advise!

I run a small network with an Xp PC and some Ubuntu PC. All the Ubuntu's are basically outdated, 9.* + 10.* . Some required software will not run on it. So far I have seen Ubuntu migration as a major headache.

What I have in mind is, something like a stand alone server, that stores emails, documents, bookmarks etc. 

Then a 'workstation' would simply run a version of Ubuntu (or whatever), but all critical userdata is on the server. If you want a new version, simply upgrade, point the email clients working directory at the server and go on.

Any advise is highly appreciated!

---

### Post by papibe on 2014-04-08
Hi flameproof.

A server would help a lot with that.

I would consider another strategy. In order to have backups, I would let users have their data on their machines, but I would mirror what you called critical data on the server. Depending on how important the data is, you could do this weekly, daily or even as changes happens.

There are several tools to accomplish this:
[LIST]
[*]Regular backup tools like deja-dup.
[*]Enterprise grade backup tools like Backula or BackupPC.
[*]Syncing tools like Unison, or BitTorrent Sync.
[/LIST]
Just my thoughts. Let us know how it goes.
Regards.

---

### Post by flameproof on 2014-04-08
> **papibe said:**
> I would consider another strategy. In order to have backups, I would let users have their data on their machines, but I would mirror what you called critical data on the server. Depending on how important the data is, you could do this weekly, daily or even as changes happens.


That is a nice alternative. I will look into those tools.

I also have a 2HDD NAS at home, and I like that I can access that through the web. But I guess it might be a bit slow as a server, or? And a dedicated server can probably do the same anyway.

---


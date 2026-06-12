---
title: "Name access on LAN including Windows and Ubuntu"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by 5circles on 2008-07-18
I'm trying to understand what I should have setup to allow named access between my different systems - Ubuntu and Windows (XP and Vista).

My Ubuntu systems have static IPs - manually entered.  I move the Windows boxes around, and sometimes use wireless, sometimes wired, so I want to use DHCP, but my router can't assign a fixed address, so the addresses might change.  Is that a problem?

I've edited /etc/hosts (and the equivalent Windows file) to include names for the machines with static IPs


I think I need a workgroup with the same name on all systems.   I set this up on Ubuntu in the Samba configuration - /etc/samba/smb.conf.  On Windows, I use Computer Properties | Advanced |Name (or similar depending on which OS) and set up the workgroup.  But it seems to take some time for the old workgroup name to disappear.  How can I make sure that I only have one workgroup - or doesn't it matter?

I've also heard that it is good to have a private TLD name to stop the systems trying to access the Internet when looking up a local name, so I set up the names in windows (in the advanced settings for DNS) and Ubuntu Network | General with a domain name of 'lan' which is the same as the workgroup I'm using.  Does this make sense?

Right now I'm able to see some systems, but not all.  I'm wondering if I need to turn everything off and then start them one by one (but which order) or what else I should be doing. 

Thanks
Mike

---


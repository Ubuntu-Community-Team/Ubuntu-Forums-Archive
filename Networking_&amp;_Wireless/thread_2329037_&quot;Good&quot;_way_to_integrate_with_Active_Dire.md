---
title: "&quot;Good&quot; way to integrate with Active Directory"
date: 2016-06-27
forum: Networking &amp; Wireless
---

### Post by kfkehua on 2016-06-27
Hi all, hope this is the right place for this this question.
We are currently doing a pilot on Ubuntu desktops and we need to join these to Windows domain.
The more I research, the more confusing it gets. There are so many ways to do it in general: samba, realmd, PBIS, sssd, ....
With most of them, the problem is the amount of configuration that are involved, and the lack of documentation thereof. And to make it more complicated, there are different ways for different distros.
Since we are piloting with Ubuntu, is there are "preferred" way for Ubuntu? (we may be using Mate to be precise)
what I'm hoping to see is:
- minimal configuration
- consistent configuration accross the different desktops (unity, KDE, Mate....)
- stable
- well documented
- adopted by others (hope we're not the only ones)
- and maybe supported by Canonical??

Thank you so much.

---

### Post by TheFu on 2016-06-27
Saw a talk at a recent linux conference about using sssd, no need for any commercial tools to make the integration work - definitely didn't need whatever Microsoft sells for "integration."  Showed how-to during the talk - live example.  Striker Leggette was the presenter. Videos should be posted in about 2 more weeks.  I didn't see anything distro specific in the presentation. The kerberos stuff was the only non-trivial part and that isn't too hard.

If you are also using Zimbra (MS-Exchange replacement plus much more), then you can have Zimbra integrate with AD and point your clients at the openldap instance it runs - though the posix LDAP extensions are sorta ugly during migrations. 

These forums are answered by the community. I don't know of **any** Canonical employees who post here and I know a few for the last few years through conferences.  They tend to be about Ubuntu Phone and/or Ubuntu Cloud stuff. I can't recall **any** talks/presentation about desktop integration in years.

As for configuration - use a devops tool to maintain the desktops. Something like ansible can easily handle 1-2,000 systems.

---

### Post by kurt18947 on 2016-06-27
TheFu is a pro at this stuff, I am not. Having said that, would it be worth asking at askubuntu.com? From the time I've spent browsing there, it seems a little more pro oriented.

---

### Post by kfkehua on 2016-06-27
for example I installed a NEW vm, followed this to the T: [https://help.ubuntu.com/lts/serverguide/sssd-ad.html](https://help.ubuntu.com/lts/serverguide/sssd-ad.html)

and still getting errors: Key table file '/etc/krb5.keytab' not found while starting keytab scan

I mean... how hard can this be ... Seriously...

---

### Post by TheFu on 2016-06-27
> **kfkehua said:**
> I mean... how hard can this be ... Seriously...

Trivial or infinite depending on many things.  Any other questions?  ;)

If you ask a question, would be helpful to include:
* relevant config files
* relevant log file entries (like errors and warnings)
* a little about your Linux experience. All we know is that you've posted a few times here and want to integrate with AD. That could mean ZERO linux knowledge or you could be part of the kernel dev team. I've seen really new people make mistakes like using the wrong logins and experienced people tripped up by not leaving an extra blank line at the end of config files (some parsers look for CRLF, not EOF).

Please help us to help you, if we can.  Not sure that we can at this point.  I haven't touched AD in a very long time - Win-Server 2003 was used then. Must say, life has been much easier since then. ;)

Could have sworn that I'd added a link for Striker's personal blog earlier. Sorry. He wrote an update to his WP blog about this. Google found it.

---


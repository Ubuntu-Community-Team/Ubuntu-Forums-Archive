---
title: "likewise-open join domain error"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by debert254 on 2008-08-28
I get the following error attempting to join the domain:


debert01@debert01-desktop:~$ sudo domainjoin-cli join MBGC.local debert01

Error: Invalid hostname [code 0x000004ba]

The name 'debert01-desktop' is 16 characters long. Hostnames may only be up to
15 characters long.


I haven't found anyone else with a similar error.  All of the commands to install likewise-open ran fine. Why the objection to the local hostname?

tia

---

### Post by su-cmitchell on 2008-08-29
I don't have a specific answer to your question but here are some observations:

Go into AD and manually create a computer name.  Notice you have to enter a computer name and a pre-Windows 2000 computer name?  And notice that the computer name field has a 63 character limit and the pre-Windows 2000 name field has a 15 character limit?  Maybe AD is detecting your computer as being pre-Windows 2000 and not allowing the longer name?  Or maybe Likewise has built in a 15 character limit to prevent possible naming issues.

Or maybe it has something to do with DNS. The full DNS computer name (FQDN) is a concatenation of the first 15 characters of a computer name and the primary DNS suffix (domain).  Maybe Likewise doesn't like the computer name and FQDN to be different, or maybe it's just a bug.

Wish I could be more helpful.

---

### Post by likeWiseGuy on 2008-09-25
> **debert254 said:**
> I get the following error attempting to join the domain:


debert01@debert01-desktop:~$ sudo domainjoin-cli join MBGC.local debert01

Error: Invalid hostname [code 0x000004ba]

The name 'debert01-desktop' is 16 characters long. Hostnames may only be up to
15 characters long.


I haven't found anyone else with a similar error.  All of the commands to install likewise-open ran fine. Why the objection to the local hostname?

tia

Hi,

The reason for the restriction of your hostname to 15 characters is strictly due to restrictions set by Active Directory. You can read further at http://support.microsoft.com/kb/909264

I hope this helps.

---


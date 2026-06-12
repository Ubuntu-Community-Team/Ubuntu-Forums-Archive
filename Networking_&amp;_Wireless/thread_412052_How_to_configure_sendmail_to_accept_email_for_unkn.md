---
title: "How to configure sendmail to accept email for unknown users?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by foxmulder on 2007-04-17
Hi,

I have installed sendmail, but by default, sendmail will reject, or bounce, incoming email addressed to users who don't exist as real users or as aliases. 

I want sendmail to accept all incoming email and redirect mail for unknown users to a particular user such as postmaster.

How do I do this? I found one guide but that doesn't work as it is aimed at Solaris...

It tells you to modify the /etc/mail/sendmail.cf in this way:

> To do this, a few changes are needed to sendmail's configuration file. 

```
# "Smart" relay host (may be null)
DSyour ISP's smart mail host
```

After this section, insert the following lines:

```
# place to which unknown users should be forwarded
Kuser user -m -a<>

# deliver mail for unknown users to postmaster locally
DLlocal:postmaster
```

If you want to deliver mail for unknown users to some user other than postmaster, replace postmaster with the name of the user who should receive such mail. Note that the username specified here must exist as a real Solaris user or must be listed as an alias in the /etc/aliases file. By default, postmaster is an alias for the real user root.

Then look for the section headed:

```
###########################################################################
###   Ruleset 5 -- special rewriting after aliases have been expanded   ###
###########################################################################

```

and, a few lines further on:

```
# prepend an empty "forward host" on the front
R$+ $: <> $1


```

Immediately after these two lines, insert the following:

```
# send unrecognized local users to a relay host
R< > $+ $: < $L . > $(user $1 $) look up user
R< $* > $+ <> $* $: < > $2 $3 found; strip $L
R< $* . > $+ $: < $1 > $2 strip extra dot

```
Save the file and sendmail will now accept mail messages addressed to unknown users while online and deliver them to postmaster or to whichever username you have specified.

When I use this code I get an error after I do /etc/init.d/sendmail/ restart

Anyone have any helpful tips? :confused:

---

### Post by foxmulder on 2007-04-20
Man, either Ubunutu is the WORST supported version of Linux or everyone here is n00b just like me: NO REPLIES to this since I posted...

Do people actually get answers here or what? :(

---

### Post by ds9 on 2007-04-21
> **foxmulder said:**
> Man, either Ubunutu is the WORST supported version of Linux or everyone here is n00b just like me: NO REPLIES to this since I posted...

Do people actually get answers here or what? :(

Do people go to the right place to ask their questions ? 
Well, the appropriate room to ask sendmail related questions is Usenet comp.mail.sendmail. 
Anyway I'll try to help you : 
- never edit sendmail.cf directly ! Use sendmail.mc when you want to do some sendmail configuration changes
- for your need : use virtusertable  (your sendmail.mc must include FEATURE(`virtusertable')dnl
) and add a catch-all entry : 
@mydomain.com    postmaster

And please stop saying stupid things about Ubuntu

ds9

---


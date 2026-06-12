---
title: "Login to server without Samba"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-10-11
Is it possible for me to authenticate my Ubuntu system against the Debian system on my network,without actually having to setup Samba on either of the systems??

---

### Post by kidders on 2006-10-11
Hi there,

If what you're interested in is centralising your user/password database for Linux boxes, you don't need to involve Windoze filesharing at all. There are a few ways of doing this, but I do it with LDAP, if that's any use to you. It can be a little hairy to set up though.

---

### Post by hellmet on 2006-10-11
yea..i have no problem with strange setups tho..
and it is exactly what u've written above,
do letme know how u do it..
or try to give me links to it..
thanks

---

### Post by kidders on 2006-10-11
Hey again,

I'm in the middle of a thread that's slowly working in the direction of LDAP authentication at the moment ([http://ubuntuforums.org/showthread.php?p=1606404](http://ubuntuforums.org/showthread.php?p=1606404)). It's a bit long, but we're getting there!

Basically, once you've installed an LDAP server (usually called 'slapd'), any HOWTO you can find will do, more or less. Depending on how far you want to take it, there's some setup to be dealt with first though. The biggest problem I usually have is that, at some point, it becomes necessary for me to tell LDAP that a user is a member of "audio", say, on all machines. That means I have to start putting system users & groups into the centralised db ... which is a pain in the ***!

So, these days, I just admit defeat and do it right at the start. So, here's a *very* brief step-by-step:

[LIST=1]
[*]Sync all the UIDs and GIDs of all real/system users & groups on all your Linux boxes. Carefully!
[*]Install LDAP authentication support on all your machines.
[*]Install an LDAP server on one of them.
[*]Read about how to write your ldap.conf (client-side authentication), nsswitch.conf (priority list for authentication mechanisms) and slapd.conf (LDAP server config).
[*]Have a look at some examples of how to set up things called "organisational units", using a format called LDIF, and see if you can make your own.
[*]Start your LDAP server.
[*]Create a test user.
[*]Try to log into a computer using the new access details.
[/LIST]

Of course, it's never gonna be *that* easy! Let me know if I can be of more specific help.

---


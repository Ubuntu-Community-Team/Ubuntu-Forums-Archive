---
title: "Confused about security software"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Nyas on 2009-02-03
Could not find any thread about this in the forum, so I am creating a new. Sorry, if I missed something.

While browsing some simple guides about security I saw almost never-ending lists of software that should make the computer a safer place.
Even reading their wiki pages, etc. I still can not always understand which does what and more less if I really need them.

If I am the only user of my laptop, have Ubuntu Desktop and not planning to set up a server, which of these are really useful?

For example:
# grsecurity (Kernel protection)
# Rootkit Hunter (Rootkit protection)
# Nagios (Network monitoring)
# Snort (Intrusion detection)
# OpenSSH (Secure remote access client)

Changing the default not-so-secure settings and using NoSctipt with Firefox are relatively simple tasks but installing and configuring the above might be more of a challenge to me.
Also, every additional program uses resources and might create more problems than solve. Especially when I have almost no knowledge about Ubuntu. So just wanted to make sure before installing any of these..

Any links about security software for beginners would also be appreciated.

Thanks.

---

### Post by Peter09 on 2009-02-03
OpenShh (client) is already installed I believe. If you do not wish to set up a server then you do not need any more for that.

I think the rest depends on how security conscious you are - in general if you are using your machine as a standard Desktop then you should not need to do much more than Ubuntu is delivered with.

---

### Post by cariboo on 2009-02-03
Have a look at this [sticky]("http://ubuntuforums.org/showthread.php?t=919472") and this [one]("http:///ubuntuforums.org/showthread.php?t=510812"). They are a great place to start.

Jim

---

### Post by Tubes6al4v on 2009-02-03
Like the others have said, if you are using it just as a regular desktop, then there is not much to worry about. As long as you are intelligent on the net with noscript and whatnot.

For me, I have thought of setting up a desktop at home with remote desktop. Until I actually make that decision, however, I am playing around with the tools one at a time, so I can learn. And yes, it does look daunting. But slowly is the key I think.

---

### Post by binbash on 2009-02-03
Don't install selinux or grsecurity kernel on a desktop machine if you don't know what you are doing because it will give you a lot of troubles.You can use rkhunter (rootkit hunter) at a desktop pc,and check for rootkits etc.Do not try snort if you are not using a server

---

### Post by OrangeCrate on 2009-02-03
As has been said, if your running a desktop version of Ubuntu, you really don't need anything. An often quoted source of information on Ubuntu security is here:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by billgoldberg on 2009-02-03
> **Nyas said:**
> Could not find any thread about this in the forum, so I am creating a new. Sorry, if I missed something.

While browsing some simple guides about security I saw almost never-ending lists of software that should make the computer a safer place.
Even reading their wiki pages, etc. I still can not always understand which does what and more less if I really need them.

If I am the only user of my laptop, have Ubuntu Desktop and not planning to set up a server, which of these are really useful?

For example:
# grsecurity (Kernel protection)
# Rootkit Hunter (Rootkit protection)
# Nagios (Network monitoring)
# Snort (Intrusion detection)
# OpenSSH (Secure remote access client)

Changing the default not-so-secure settings and using NoSctipt with Firefox are relatively simple tasks but installing and configuring the above might be more of a challenge to me.
Also, every additional program uses resources and might create more problems than solve. Especially when I have almost no knowledge about Ubuntu. So just wanted to make sure before installing any of these..

Any links about security software for beginners would also be appreciated.

Thanks.

Which of them are useful for you?

None.

You don't need any other software.

Ubuntu comes with apparmor, iptables configured correctly for desktop users and sudo.

That's all you need.

--

The best advice I can give you to keep your pc safe and avoid things like the recent OSX trojan problems:

- Keep your system up to date
- Only install software from the repos (or trusted sources, when in doubt ask on irc or on these forums)

---

### Post by Nyas on 2009-02-08
Thank you all for the replies. They have clarified the topic for me quite a bit. It is always easier to start when you know where to read and where to skip :)

---


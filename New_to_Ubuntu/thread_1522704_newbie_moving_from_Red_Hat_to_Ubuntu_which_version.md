---
title: "newbie moving from Red Hat to Ubuntu: which version?"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by kristo5747 on 2010-07-02
Greetings!

I want to upgrade my Linux Red Hat machine [Client release 5.4 (Tikanga)] to Ubuntu.

Red Hat is not keeping up with the rest of *nix world and I am dealing with a lot of limitations on a daily basis.

My box is a DELL PRECISION T3400. It is a 64 bit machine with 16GB of RAM and 3Gig CPU.

Not sure if it matters but I am an independent developer ; my box currently runs Apache server, PHP, Python, Mysql server, Oracle 10g and IBM DB2 v9. 

I need an OS that can satisfy my needs with these apps. What version  would you recommend, the 64bit Desktop of 64bit server?

Thanks in advance for your help.

Al.

---

### Post by QIII on 2010-07-02
64 bit, that much is sure at least.

Desktop or Server really depends on what your primary use is going to be.

Is this primarily for development or as a dedicated server?

(By the way, I also use Fedora.  I experience some frustrations with a few things that are not quite up to the current standard of "modernity", but in all it is not a bad distro.)

---

### Post by sydbat on 2010-07-02
> **kristo5747 said:**
> Greetings!

I want to upgrade my Linux Red Hat machine [Client release 5.4 (Tikanga)] to Ubuntu.

Red Hat is not keeping up with the rest of *nix world and I am dealing with a lot of limitations on a daily basis.

My box is a DELL PRECISION T3400. It is a 64 bit machine with 16GB of RAM and 3Gig CPU.

Not sure if it matters but I am an independent developer ; my box currently runs Apache server, PHP, Python, Mysql server, Oracle 10g and IBM DB2 v9. 

I need an OS that can satisfy my needs with these apps. What version  would you recommend, the 64bit Desktop of 64bit server?

Thanks in advance for your help.

Al.The desktop has the gui already installed, and you can add all the server stuff later. However, if you want the server kernel (I believe it has a different config for...well servers), you can always add the gui after.

Also, have you considered Fedora. It is based on Red Hat and you might be more familiar with it.

Finally, there is CentOS that is really server oriented. Likely the best server OS out there right now.

I guess it depends on how you want to use your box.

---

### Post by QIII on 2010-07-02
> **sydbat said:**
> Also, have you considered Fedora. It is based on Red Hat and you might be more familiar with it.

Well, there's some history behind that.  Might be better to say now that Fedora is the test bed for RH.

In effect, RH dumped a significant part of the "R&D" off to an independent entity.

---

### Post by kaldor on 2010-07-02
Do not use Fedora on preduction machines! The updates enjoy breaking your system.

CentOS is just RHEL for free (basically).

Ubuntu server is great. I use it myself on a low-end machine. Stable and easy to use, it's a great server OS. I don't use Ubuntu as a desktop anymore, but I sure as hell don't have a problem with it on the server :)

If it's a desktop OS, don't go for Ubuntu. I had to leave it for some other distros. Check my sig for some other alternatives.

Good luck! Knowledge of RedHat will leave you prepared enough.

---

### Post by QIII on 2010-07-02
Don't know that I'd recommend OpenSolaris right now.  I'm wondering if it will survive the Oracle takeover.  The 6 month release is 6 months overdue, and it doesn't look like it is going to arrive any time soon.  I still use 2009.06, but I'm not sure how long that will last.

I haven't broken Fedora 13 yet, except intentionally.

FreeBSD is really good, so long as you have some pretty good familiarity.  It's not for grandma.

If you want a really, REALLY secure server, OpenBSD is, arguably, the most secure out there.

Just some thoughts.

There is nothing that says you have to use Ubuntu.  It is good to try other stuff.  Give several a whirl.

---

### Post by snowpine on 2010-07-02
Have you considered taking the new Red Hat EL 6 Beta for a test drive? It is currently in its 2nd beta, I believe, and will shatter your "Red Hat is not keeping up" notion. It is as up-to-date as any other distro right now, addressing your primary concern with your current situation. If you can tough it out until the end of the year, you should see a stable release.

That point aside, the current Ubuntu release (10.04) is Long Term Support (3 years) so it's a pretty good choice. It does not matter whether you start with a Desktop or Server install if you plan to use the computer for both functions (everything you need can be added through the package manager). You can start with a Server install and then "sudo apt-get install ubuntu-desktop" for example. The Desktop version however has the advantage that you can easily test-drive it as a Live CD.

---

### Post by QIII on 2010-07-02
Or even Solaris 10.  If you buy the disk set (about $20), you can get  the certificate to use it indefinitely (but not for a commercial enterprise).

If you download, you get the certificate but are still bound by the 90  day trial limitation.

Sorry, Kristo.  I don't think anyone is trying to make the decision hard.  Just trying to point out that there are many choices and they are worth trying.  That way you can find out what works best for you.  What works best is the best choice for you.

When you ask "What's the best?", you'll get as many answers as there are opinions and you know what opinions are like.  Everyone has one.  And every one is the right answer, depending on what YOU want.

---

### Post by kristo5747 on 2010-07-02
> **QIII said:**
> 64 bit, that much is sure at least.

Desktop or Server really depends on what your primary use is going to be.

Is this primarily for development or as a dedicated server?

(By the way, I also use Fedora.  I experience some frustrations with a few things that are not quite up to the current standard of "modernity", but in all it is not a bad distro.)


It is is primarily for development and test. Not for production type work.

---

### Post by QIII on 2010-07-02
> **kristo5747 said:**
> It is is primarily for development and test. Not for production type work.

I think I'd go with the desktop, then.  I use everything you listed with the exception of DB2, so I can't comment.

The next question of course, is whether you want to use GNOME (Ubuntu), KDE (Kubuntu), Xfce (Xubuntu), LXDE (Lubuntu -- not "officially recognized" yet.)

Again, opinions are like ....  Everybody has one.

If you install Ubuntu, you can always add KDE or Xfce later and choose between them at each session.

---

### Post by kristo5747 on 2010-07-02
> **snowpine said:**
> Have you considered taking the new Red Hat EL 6 Beta for a test drive? It is currently in its 2nd beta, I believe, and will shatter your "Red Hat is not keeping up" notion. It is as up-to-date as any other distro right now, addressing your primary concern with your current situation. If you can tough it out until the end of the year, you should see a stable release.

That point aside, the current Ubuntu release (10.04) is Long Term Support (3 years) so it's a pretty good choice. It does not matter whether you start with a Desktop or Server install if you plan to use the computer for both functions (everything you need can be added through the package manager). You can start with a Server install and then "sudo apt-get install ubuntu-desktop" for example.


I considered installing the Beta 6 of RH but found myself disinclined to dealing with beta issues. If my machine is down, I can't work. if I can't work, I don't get paid.

10.04 server seems a good choice for now.

---

### Post by bodhi.zazen on 2010-07-02
> **kristo5747 said:**
> Greetings!

I want to upgrade my Linux Red Hat machine [Client release 5.4 (Tikanga)] to Ubuntu.

Red Hat is not keeping up with the rest of *nix world and I am dealing with a lot of limitations on a daily basis.

My box is a DELL PRECISION T3400. It is a 64 bit machine with 16GB of RAM and 3Gig CPU.

Not sure if it matters but I am an independent developer ; my box currently runs Apache server, PHP, Python, Mysql server, Oracle 10g and IBM DB2 v9. 

I need an OS that can satisfy my needs with these apps. What version  would you recommend, the 64bit Desktop of 64bit server?

Thanks in advance for your help.

Al.

I think the better question, what is you are wanting that you feel RHEL is lacking ?

Depending on your needs, you may be best off with anything from Centos to Fedora to Debian to Ubuntu, hard to say.

---

### Post by kristo5747 on 2010-07-02
> **bodhi.zazen said:**
> I think the better question, what is you are wanting that you feel RHEL is lacking ?

Lacking may be too strong a word. I have been a RHEL user for the past four years: I like it.

However, my "issues" are from a coder stanpoint. For instance:

1) mysql : still still in 5.1
2) php : still stuck in 5.1

As a coder, not being able to update to upgrade my version of PHP prevents me from using development frameworks such as Symfony or CakePHP. This costs me $$$.

I have attempted to download/configure and make PHP on my machine: both `make` attempts (with 5.2 and 5.3) failed with a slough of errors. 

I can't spend time debugging problems like this (I don't code=I don't get paid) and I am not going to troll forums with that type of issues either.

That's why I am inquiring about Ubuntu. From what I read, software updates happen frequently. This is a huge time-saver for me as I'd rather schedule a CRON job a la 'Yum Update` to take care of this instead of slogging thru make errors.

My 2 cents.

---

### Post by bodhi.zazen on 2010-07-02
> **kristo5747 said:**
> Lacking may be too strong a word. I have been a RHEL user for the past four years: I like it.

However, my "issues" are from a coder stanpoint. For instance:

1) mysql : still still in 5.1
2) php : still stuck in 5.1

As a coder, not being able to update to upgrade my version of PHP prevents me from using development frameworks such as Symfony or CakePHP. This costs me $$$.

I have attempted to download/configure and make PHP on my machine: both `make` attempts (with 5.2 and 5.3) failed with a slough of errors. 

I can't spend time debugging problems like this (I don't code=I don't get paid) and I am not going to troll forums with that type of issues either.

That's why I am inquiring about Ubuntu. From what I read, software updates happen frequently. This is a huge time-saver for me as I'd rather schedule a CRON job a la 'Yum Update` to take care of this instead of slogging thru make errors.

My 2 cents.

If you use Lucid (Ubuntu 10.04) 

Mysql is 5.1 : [http://packages.ubuntu.com/lucid/mysql-server](http://packages.ubuntu.com/lucid/mysql-server)

php is 5.3 : [http://packages.ubuntu.com/lucid/php5](http://packages.ubuntu.com/lucid/php5)

Ubuntu 10.10 is in development and you should expect problems if you use that.

You may wish to consider staying with RHEL (for support) and running Ubuntu, or an alternate OS, in KVM. You may be able to have the best of both worlds.

---

### Post by okplayer02 on 2010-07-03
Well to be honest if you want the latest and greatest for all your software I suggest Archlinux also since their is a rolling release so one you update you have all the updates I have one box for 2 years now with Arch and still going good.

Also Fedora Debian Unstable, Maverick, Sidux, Gentoo, these are all good choices if you want the latest in packages.

---


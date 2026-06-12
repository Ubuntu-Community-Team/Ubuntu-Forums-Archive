---
title: "Partial freezes in Lucid, please help"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by gypsyblue on 2010-08-03
Hi,

I am having an EXTREMELY frustrating problem with my laptop running Lucid Lynx. It appeared suddenly and not immediately after installing any new updates. When I am running Firefox, my browser will suddenly lock up with a sort of partial freezing that varies each time. Sometimes I can use the buttons and the address bar, but I cannot scroll or click on anything in the browser window; sometimes I can scroll and click on things in the browser window but cannot use the buttons or the address bar. In either case, I cannot use the top menu or switch to any other programs while Firefox is frozen, and every single instance has required a hard restart.

This problem first appeared last night, and since then I have not been able to run my laptop for more than an hour at a time without my screen partially freezing and having to hard restart. I work from home with my laptop and the online database system we use MUST be run with Firefox so I cannot use another browser. Sometimes my laptop won't last even 20 minutes without locking up so I am unable to work. I have used Ubuntu for about a year now and I love it, but this problem is SO frustrating that I want to either downgrade or change my OS if I can't solve it.

System Info:
Lenovo Thinkpad T400 running Lucid Lynx (dual-booting Vista Basic)
Intel Core 2 Duo T9600 (2.80 GHz)
Mobile 4 Series Integrated Graphics Controller (Intel)

Any help would be hugely appreciated, this is an extremely frustrating problem for me. Thank you so much.

---

### Post by lovinglinux on 2010-08-03
Would be nice if you could specify which content you are viewing when it freezes. Flash for example is a good candidate for such things. 

Your browser could be freezing due to excessive CPU usage and overheat (flash videos for example), bad javascript on the page you are viewing, extensions performing synchronous database tasks or even a graphics driver issue.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Do the tests and report back.

I also recommend that you read these:

[Database Optimization](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)
[Preferences Tweaks]("http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html")
[Flash Optimization]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

Also use [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") to block content you don't need.

---

### Post by homerhomer on 2010-08-10
Can you try to isolate the issue. You said that you "have to use"  Firefox. I understand that you have to use it for your database but if lets find out if it's just see what's going on.

Try this load up the system monitor, System > Administration > System Monitor, Then click on processes and see who's stealing your resources. You might want to sort by cpu. 

I've had an issue like this, it was Ubuntu One service hogging up my my resources. uninstall.

---

### Post by Elmer Fudd on 2010-08-11
Does running the same process with Firefox in Vista work flawlessly?

---

### Post by correnticalde on 2010-08-14
Hi,

I am experiencing the same annoying problem!

I suspect it is related to the bookmark synchronization, since the first time I got the issue it was right after havig activated Bindwood and the bookmark synchronization. When the problem occurs the process firefox-bin is taking only moderate quantities of CPU (the firefox-bin process gets in status 'uninterruptable' takes approximately 5% to 7% and the 'waiting channel' is jbd2_log_wait_commit), only firefox hangs while the system continues to be responsive. After 8 to 10 seconds gets back to normal.

Quoting the [https://answers.launchpad.net/bindwood/+faq/859](https://answers.launchpad.net/bindwood/+faq/859) : "The first time Firefox is launched after Bindwood is installed, Firefox will take a little while (seconds, not minutes) to copy all your bookmarks to the Ubuntu One CouchDB database. For those experiencing constant unresponsiveness with Firefox and Bindwood, please install the Bindwood PPA for the latest fixes: https://edge.launchpad.net/~urbanape/+archive/bindwood-exp".

Another workaround can be removing Bindwood (unless you really need it).

Hope it helps...

Cheers,

Fabrizio

---

### Post by lovinglinux on 2010-08-14
> **correnticalde said:**
> Hi,

I am experiencing the same annoying problem!

I suspect it is related to the bookmark synchronization, since the first time I got the issue it was right after havig activated Bindwood and the bookmark synchronization. When the problem occurs the process firefox-bin is taking only moderate quantities of CPU (the firefox-bin process gets in status 'uninterruptable' takes approximately 5% to 7% and the 'waiting channel' is jbd2_log_wait_commit), only firefox hangs while the system continues to be responsive. After 8 to 10 seconds gets back to normal.

Quoting the [https://answers.launchpad.net/bindwood/+faq/859](https://answers.launchpad.net/bindwood/+faq/859) : "The first time Firefox is launched after Bindwood is installed, Firefox will take a little while (seconds, not minutes) to copy all your bookmarks to the Ubuntu One CouchDB database. For those experiencing constant unresponsiveness with Firefox and Bindwood, please install the Bindwood PPA for the latest fixes: https://edge.launchpad.net/~urbanape/+archive/bindwood-exp".

Another workaround can be removing Bindwood (unless you really need it).

Hope it helps...

Cheers,

Fabrizio

Firefox 4 will come with a synchronization tool built-in, that will allow yo sync bookmarks, passwords, settings, history and tabs. The current beta already has it. If you want to start using it with Firefox 3.6.8, then get [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/") extension. Don't forget to remove it when Firefox 4 comes out, otherwise you might have a duplicated tool in the preferences.

Say goodbye to Xmarks and Bindwood.

---


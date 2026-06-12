---
title: "Removed Zeitgeist, Can't get the feeling of the times."
date: 2011-05-30
forum: New to Ubuntu
---

### Post by P=NP on 2011-05-30
I've removed Zeitgeist, now I can't access the applications menu. Any work around?

---

### Post by jtarin on 2011-05-30
You need to reinstall. Until [Zeitgeist Global Privacy ]("http://www.webupd8.org/2011/04/zeitgeist-is-finally-getting-options-to.html")is released, install [Activity Journal]("https://launchpad.net/%7Ezeitgeist/+archive/ppa/+files/gnome-activity-journal_0.6.0-0ubuntu1%7Emaverick1%7Eppa2_all.deb") (don&#8217;t use the version in the official Ubuntu 11.04 Natty Narwhal repositories &#8211; that doesn&#8217;t seem to work), go to its Preferences and on the Plugins tab, enable &#8220;Blacklist Manager&#8221; (seems you have to double click the checkbox to enable it) &#8211; now a new &#8220;Blacklist&#8221; tab should be displayed. Here, click the add button and enter the path to your private files (porn). If you want to block all files, use &#8220;*&#8221; for the path.

You can also clear the Zeitgeist history (this is the history of recent files that&#8217;s display in Dash) by using the following commands:

rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace


Read more: [http://www.xp4g.net/linux/things-to-tweak-fix-after-installing-ubuntu-11-04-natty-narwhal/#ixzz1NtL9gTnF](http://www.xp4g.net/linux/things-to-tweak-fix-after-installing-ubuntu-11-04-natty-narwhal/#ixzz1NtL9gTnF)

---


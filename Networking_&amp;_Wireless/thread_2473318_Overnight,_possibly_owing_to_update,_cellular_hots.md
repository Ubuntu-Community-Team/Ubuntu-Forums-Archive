---
title: "Overnight, possibly owing to update, cellular hotspot gives error"
date: 2022-03-31
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2022-03-31
I am running Ubuntu 20.04.4 LTS. As of this evening (I didn't notice this last night), when I use my phone as a wi-fi hotspot, I get an irritating captive portal login pop-up, apparently for my own phone. It opens <https://nmcheck.gnome.org>, but this just gives a "404 Not Found" header, a horizontal rule, and the body text "nginx/1.21.6". One can shut that window, and apparently use the internet (as witness this post), but the icon in the upper right is permanently a question mark, and the desktop application for my cloud drive service, which syncs certain folders, shows up as disconnected. I did download some of the security updates yesterday and wonder if this could be connected.

How can I make this go back to normal?

---

### Post by DuckHook on 2022-03-31
Oof.

It sounds very likely that your most recent updates caused this.

Your situation is a toughie and I don't envy you. Chasing down regressions caused by updates is pretty involved.

[LIST=1]
[*]Update history can be found in /var/log/apt/history.log
[*]Find the date in question.
[*]Then look for the likely culprit (easy for me to say, much harder for you to do).
[*]It helps to concurrently look in your logs, filtering for the times that you connect to your phone. Look for what libraries are being called as well as obvious things like errors and warnings. A module or library being loaded at that moment may be one of those in your last update. If so, then there's a good chance this is the culprit.
[*]If you nail down which component is causing the problems, you can report this as a bug to the proper devs. Ubuntu tracks bugs using Launchpad. Upstream can be in different places, but often it's github these days.
[/LIST]
Aside from reporting it, I don't know if there's anything else you can do. I suppose you could revert the update and apt-mark the older lib/module to chain it in place. That would be beyond my pay grade.

---

### Post by foxy123 on 2022-04-05
> **jdkcarlson said:**
> I am running Ubuntu 20.04.4 LTS. As of this evening (I didn't notice this last night), when I use my phone as a wi-fi hotspot, I get an irritating captive portal login pop-up, apparently for my own phone. It opens <https://nmcheck.gnome.org>, but this just gives a "404 Not Found" header, a horizontal rule, and the body text "nginx/1.21.6". One can shut that window, and apparently use the internet (as witness this post), but the icon in the upper right is permanently a question mark, and the desktop application for my cloud drive service, which syncs certain folders, shows up as disconnected. I did download some of the security updates yesterday and wonder if this could be connected.

How can I make this go back to normal?

Got the same problem recently. As I understand the Network Manager checks the connections by going to [noparse]http://nmcheck.gnome.org/check_network_status.txt[/noparse] It seems for some reason it goes just to [noparse]http://nmcheck.gnome.org[/noparse] It's possible to switch off in Privacy/Connectivity settings but I wonder why it's happening. COuld you post here if you find the way to resolve it without switching off the connectivity test?

---

### Post by jdkcarlson on 2022-04-06
Sorry for my delayed reply, and thanks to both of you. I got discouraged seeing that DuckHook's suggested solution was a fair deal beyond my own technical capabilities, and have been studiously ignoring the problem for a few days now, telling myself I'll begin sometime later what seems like a massive undertaking I am ill-equipped for. 

For now. I can only report back that the problem has not been so good as to resolve itself.

---

### Post by DuckHook on 2022-04-06
> **jdkcarlson said:**
> …I got discouraged seeing that DuckHook's suggested solution was a fair deal beyond my own technical capabilities, and have been studiously ignoring the problem for a few days now, telling myself I'll begin sometime later what seems like a massive undertaking I am ill-equipped for.
Yes, it can get overwhelming, but please don't get discouraged. Once things are running, they tend to continue doing so without further problems.

What jdkcarlson posts is a workaround. You can make the message go away by unchecking: Settings &#8594; Privacy &#8594; "Connectivity Checking". It's not a real *solution* but it will make your usage functional until the problem is eventually solved.

My suggestion was based on chasing down the problem, then filing a bug report in order to make Ubuntu better. But playing detective is not everyone's cup of tea, and it is perfectly acceptable to use workarounds to make the problem go away and let others address the root problems.

As you get more knowledgeable about bugs, how to hunt for them and how to report them, the measures that I posted won't seem so overwhelming. Until then, just do what you need in order to remain functional.

Good Luck and Happy Ubuntu-ing!

---


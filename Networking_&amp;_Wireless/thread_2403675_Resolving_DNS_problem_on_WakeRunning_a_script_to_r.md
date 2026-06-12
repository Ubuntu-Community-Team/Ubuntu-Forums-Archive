---
title: "Resolving DNS problem on Wake/Running a script to refresh DNS on wake up"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by jachim2 on 2018-10-14
Hi all,

This is my first post in the Ubuntu forums although I've been a linux user for almost 16 years. I can run simple command line stuff and have no problems digging around in a system through terminal and making simple modifications. (In case anyone cares, I actually was on the Beta for Mac OS 10.0000; which is how I got involved in the linux community in the first place) Thing is I have an older macbook air 2011 model that can't do the gnome switch (not sure if it matters for the thread purpose).

In just the last month or two I noticed a slow down and problem loading web pages (in opera, firefox, and chrome). To be fair I do usually have lot's of queued tabs in multiple browsers and browsing apps running almost all the time. Then about a week ago I had to keep rebooting my computer after I closed the laptop in order to get the Internet working again.

The command I found that seems to alleviate this problem is : sudo systemctl restart NetworkManager

Works every time, just a little hiccup in reconnecting on Wake. Thing is I have to run it manually with an open terminal window every time right now.

I really don't have much experience setting a command like that to run properly on waking in the foreground or background. I could probably run the basic script in a simple "hello world" kinda script. I know it might need the user password for sudo, and that's where I'm stumped.

If anyone either can help create a simple automatic script to run the command that would be great. If anyone knows why the problem is happening or has any ideas as to how fix it more effectively that would be even better!

- Daniel

---


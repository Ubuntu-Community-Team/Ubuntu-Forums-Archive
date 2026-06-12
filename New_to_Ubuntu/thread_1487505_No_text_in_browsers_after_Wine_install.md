---
title: "No text in browsers after Wine install"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by klompen on 2010-05-19
I installed 10.4 on my eMachines M6811 laptop. The video card is the built-in ATI Mobility Radeon 9600.

Everything about the install went fine and everything was working great until I attempted to install Wine using the Ubuntu Software Center. There were more choices than I anticipated and I somehow managed to install these two packages:

1. Wine Microsoft Windows Compatibility Layer (Beta Release)
     Microsoft Windows Compatibility Layer (dummy package)
2. Wine Microsoft Windows Compatibility Layer (Web Browser)
     wine1.2-gecko

After the install I discovered that both Firefox and Chromium display no text - only graphics and blocks of color are displayed.

I've tried uninstalling both packages and doing a forced uninstall of wine from the command line and I've removed my .wine folder. The problem remains.

I'm not sure where to go next to solve this. I have been unable to figure out how to reinstall the video drivers. At this point I could just reinstall Ubuntu, but once I've been using it for awhile (or if I was supporting someone else) that would not be a very good way to go. In Windows I could reinstall a video driver with my eyes closed, but I'm lost in Ubuntu on anything that isn't just normal tasks. I'd really like to be able to move to the next level instead of taking the easy way out.

Where do I go next?

Ernie

---

### Post by klompen on 2010-05-21
Well I'm not really happy with the solution, but I did solve the problem.

My solution was to reinstall Ubuntu, but to uncheck the options for formatting the partitions and to make sure that I used the existing partitions and marked the same one at root. This  saved settings such as Firefox's preferences, but fixed the video problem. I still had to reinstall wireless drivers after the install had completed.

I'm glad that I got it solved, but I think the solution is a bit over the top and wish I had a clue how to narrow in on what the problem  was. This doesn't seem like a reasonable approach if I was working on someone's PC for pay.

Now to try Wine again so I can run Evernote - and see if I can avoid blowing it up this time.

Ernie

---


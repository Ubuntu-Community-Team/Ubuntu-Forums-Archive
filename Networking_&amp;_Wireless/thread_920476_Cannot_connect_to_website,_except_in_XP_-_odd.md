---
title: "Cannot connect to website, except in XP - odd"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by sit properly on 2008-09-15
I'm trying to access the website: [http://www.littleblackstar.com](http://www.littleblackstar.com) (which is my own site), but cannot. I'm using Firefox 3 and Opera 9.5, but nothing. It will connect via a proxy server. I am also able to ping it.

I can access it through XP (I dual boot on my desktop machine) and through my Ubuntu laptop on the same network. 

This is really odd and I don't know where to go next. It started about an hour ago, prior to that, I could access it normally. I didn't update or perform any maintenance prior to the problem. In fact, I was looking at the site one minute and the next I couldn't access it. 

Pinging and digging both resolve to the same IP (from both computers, desktop and laptop). 

w3m loads on the laptop, but not the desktop (says "opening socket"). Both laptop and desktop have same MTU when I ifconfig. I have also blacklisted ipv6, but no change.

I would really love to solve this. Yes, the site will work for you, it works for me, but not from this computer. Both using 8.04.

Any suggestions?

---

### Post by sit properly on 2008-09-15
Well, weird. I don't know why I didn't try this before - or why it happened, but when I reset my router, it was all fine again. Odd.

---

### Post by knattlhuber on 2008-09-15
How about looking at the system logs for the time when it suddenly failed to load?

EDIT: Oh, you fixed it. K. Ignore my post..

---

### Post by DrMega on 2008-09-15
You weren't just promoting your site were you? :)

Anyway, I had a look at your site (I'm at work, so using IE6), and I think you might want to have a look at it. On your 'About' page the black text appears over the top of a picture, much of which has a very dark background, rendering the text unreadable. I suspect it is IE's notoriously bad handling of CSS and layers but if you want to reach the widest audience, you might want to check it out.

---


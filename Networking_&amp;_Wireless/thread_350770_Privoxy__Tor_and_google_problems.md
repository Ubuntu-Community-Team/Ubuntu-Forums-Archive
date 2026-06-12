---
title: "Privoxy / Tor and google problems"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by Sarisar on 2007-02-01
So I have privoxy and tor set up, and they work fine (thanks for the how-tos people).  However google and wikipedia and some other sites complain that I'm using tor, so I want to set some websites not to use tor.  Now I could set them to not use the proxy through firefox, however I want to still use privoxy for google so I check my gmail account and use google reader but it won't have me logged in when I'm searching for stuff.  I can get privoxy to do that fine however (block cookies for .google.com but allow cookies for .google.com/reader).  Also that is only for one browser, it would be easier if I could get privoxy to do that by itself so it works for all browsers.

So digging around the manual states you can set up exceptions for the forwarding by using:
```
forward-socks4a / 127.0.0.1:9050 .
forward .google.com .
```
(the first one sends privoxy to tor, of course)

So I set that up.  Problem is it doesn't find the page - you get the privoxy message 'can't resolve domain'.  So have I screwed up my DNS somehow in Privoxy?

I have tried various things such as reinstalling privoxy but can't seem to get it to work.  I know it is doing something because I can comment out the line, restart privoxy and you get the google message that 'this request looks like it might be a spammer' error (so privoxy and tor _are_ working) but if I try to stop the forwarding for google it doesn't work giving what looks like a DNS error.

HELP!

---

### Post by Sarisar on 2007-02-01
Update - if I remove the extra stuff in privoxy to simply use that and not bounce stuff through tor it doesn't work either in any browser I try.  So my guess is that privoxy isn't doing DNS requests properly - does anyone know what I'm missing?

---

### Post by Sarisar on 2007-02-08
Still don't know why Privoxy can't do DNS stuff, however I installed tiny proxy and forwarded the non-tor traffic through there and that seems to work :)

---


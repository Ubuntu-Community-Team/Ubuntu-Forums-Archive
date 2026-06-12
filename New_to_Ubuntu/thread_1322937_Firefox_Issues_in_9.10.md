---
title: "Firefox Issues in 9.10"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by jmundinger on 2009-11-11
Since updating from 9.04 to 9.10 and doing the I have experienced frequent issues with firefox crashes.  Initially, firefox froze.  After reporting that problem, I was advised to install the most recent updates to firefox, which I did.  Subsequently, I have experienced frequent crashes.  Typically, it happens with two or more tabs open and when I navigate from one page to another.  Is anyone else experiencing similar problems?  Any suggestions?

---

### Post by fooman on 2009-11-11
could be a plugin or 2 not working correctly....try creating a new firefox profile and see if the problems persist.

close firefox,  then open a terminal or press the alt-f2 keys to open the run dialog box....type the following into either:

```
firefox -P
```create a new profile then open firefox using the new profile....see if the problems stop.  if they do,  then setup the new profile with your favorite plugins and themes, one at a time...see if the problems start after adding a specific one.

hope that helps.

---

### Post by lhb1142 on 2009-11-11
Try this:

1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle. Set to true
4. Restart your Mozilla application and try again.

I had a slightly different problem with Firefox (in 'Karmic') and this workaround (which was told to me by 'Wojox') solved it. ):P

---


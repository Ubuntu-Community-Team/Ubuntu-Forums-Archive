---
title: "CGI will not run on Apache running on Ubuntu server"
date: 2022-05-17
forum: Networking &amp; Wireless
---

### Post by foxsquirrel on 2022-05-17
Apache documentation shows how to configure CGI however Ubuntu does not have any of the files as stated by Apache. So what is up with that..........

---

### Post by TheFu on 2022-05-17
Most people don't use CGI, so it isn't included.

Look for the module(s) you need, if they aren't included.  CGI is from the 1990s. Even back then, we'd create pre-loaded fcgi or mod_perl scripts to gain 20x more performance than CGI alone.  I use CGI for some very trivial, personal stuff, but not for anything with session management.  For full webapps, I want a PSGI interface and don't use apache at all.

---

### Post by foxsquirrel on 2022-05-17
> **TheFu said:**
> Most people don't use CGI, so it isn't included.

Look for the module(s) you need, if they aren't included.  CGI is from the 1990s. Even back then, we'd create pre-loaded fcgi or mod_perl scripts to gain 20x more performance than CGI alone.  I use CGI for some very trivial, personal stuff, but not for anything with session management.  For full webapps, I want a PSGI interface and don't use apache at all.
Yes, I know, I am old too.....

Its for an embedded application. Don't need the horsepower, simple and effective is what we need.

Thing is so much of this stuff is getting ridiculously complicated to program and maintain. When you have a global footprint that stuff has its place and a big team to manage and maintain it.

Searched the internet and only found bloggers that have no clue what they are even writing about let alone tested what they have posted. Was hoping someone on here had some information.

---

### Post by foxsquirrel on 2022-05-17
Found the solution.

---

### Post by TheFu on 2022-05-18
> **foxsquirrel said:**
> Found the solution.

And I see that you didn't choose to post the solution so others might gain from your skills?

---


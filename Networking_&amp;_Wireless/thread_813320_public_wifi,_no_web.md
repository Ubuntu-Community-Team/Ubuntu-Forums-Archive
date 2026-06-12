---
title: "public wifi, no web"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by defaulk on 2008-05-30
I'm having trouble connecting to the web on a public access point that I'm stuck with every day.

I can connect to the network ok.  I get an IP fine.  When I go to bring up any web page, it seems to timeout, looking up the domain I think.

Here's what's strange: let's say I go to [http://www.google.com/](http://www.google.com/).  Times out.  Now I dig that domain.  I get a result!  Now, going back to my browser, I go to google.com, the wifi welcome page comes up, I can "Agree", and then go to google.com....but then nowhere else.  Going to any other domain times out.

This was a problem on gutsy.  I'm now on hardy and I have the same trouble.

Does anybody have any clue what I can do to get this working?

---

### Post by superprash2003 on 2008-05-31
try changing DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by defaulk on 2008-05-31
I tried using OpenDNS servers, but that doesn't seem to work.  I think it has something to with the fact that the public wifi basically denies internet traffic until you get to their landing page and click "I Agree".

---

### Post by Monicker on 2008-05-31
Sounds like a typical captive portal.  Public wifi does not always mean that you can go to any web site that you want.  The page where you must agree to their terms of service should at least give some information about any access restrictions.

What public wifi network is this?

---

### Post by defaulk on 2008-05-31
It's called Harborlink, from the Dayton OH area.  I forgot to mention, but the folks who are on Windows are able to go to any site once they get past the agreement page.  No apparent access issues at all for either Firefox or IE.

I tried contacting their support, and they said they tested their network with Ubuntu, but you know how helpful support like that can be...

---

### Post by ugm6hr on 2008-05-31
> Here's what's strange: let's say I go to [http://www.google.com/](http://www.google.com/). Times out. **Now I dig that domain.** I get a result! Now, going back to my browser, I go to google.com, the wifi welcome page comes up, I can "Agree", and then go to google.com....but then nowhere else. Going to any other domain times out.

What does *Now I dig that domain* mean?

This sounds like a DNS resolution issue.

Can you get to the true IP in FireFox:
64.233.183.104

---

### Post by defaulk on 2008-06-10
Just got back from vacation.

> **ugm6hr said:**
> What does *Now I dig that domain* mean?
I should have been more clear.  I meant the command line program dig.  as in: $dig [www.google.com](www.google.com)

> **ugm6hr said:**
> This sounds like a DNS resolution issue.
Can you get to the true IP in FireFox:
64.233.183.104
Yes I can.  If I have not clicked "Agree" on the start page I'm directed to it first, but once I click agree, I can get to google via straight ip address.

What should I do?

---

### Post by ugm6hr on 2008-06-10
> **defaulk said:**
> Yes I can.  If I have not clicked "Agree" on the start page I'm directed to it first, but once I click agree, I can get to google via straight ip address.

What should I do?

Try this: [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by defaulk on 2008-06-10
> **ugm6hr said:**
> Try this: [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)
That didn't work unfortunately.  I also tried disabling ipv6 on the whole system and rebooting, which didn't work either.

Any other possibilities?

---

### Post by defaulk on 2008-06-15
Bump. I still can't figure this out, so no internet.  Besides that, other people can get on just fine with windows.  That's just wrong.  :confused:

---


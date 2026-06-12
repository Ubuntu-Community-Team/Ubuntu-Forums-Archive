---
title: "ANNOYING Site Jackers"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by mistypotato on 2010-10-29
Hi,

There is a site I go to a LOT and I often forget to type .NET instead of .COM

when I do, I always go to the wrong site which is malicious.

I'm drawing a total blank on how to get a web address I enter to always open or go to a different web site so when I enter .COM instead of .NET, I will still go to the site I want to go to.

thx

---

### Post by Omnomnom on 2010-10-29
I think there's a script to do that but what I like to do is check the address bar after I type something into it. And if someone sends you a tinyurl like or the like, google it first.

---

### Post by MartyBuntu on 2010-10-29
Why not just bookmark the web page?

You really type the full address every time you go to this site?

---

### Post by mistypotato on 2010-10-29
> **MartyBuntu said:**
> Why not just bookmark the web page?

You really type the full address every time you go to this site?

Never ASSuME things.   I said I go to the site a LOT.  Can you show me where I said I always type it?

There may sometimes be more to a question than we first collect....or is easily ascertained.

Ciao !

---

### Post by MartyBuntu on 2010-10-29
So, why don't you bookmark the page?

---

### Post by NT4usB on 2010-10-29
Blacklist the IP address of the site(s) you don't want to load.

---

### Post by mistypotato on 2010-10-29
> **NT4usB said:**
> Blacklist the IP address of the site(s) you don't want to load.

ok,
that's one workable solution :KS

---

### Post by NickJones on 2010-10-29
Many Modems/Routers allow you to block certain IPs or URLs, or alternatley, you could just enter it correctly. You said the site is *mallicious *but as a Ubuntu users you should be relatively safe in terms of Viruses, Spyware and all of that fun stuff.

---

### Post by jroa on 2010-10-29
What he said.  If you have a router, just black list the site and you will not be able to go to it.

---

### Post by CharlesA on 2010-10-29
You could even go so far as blacklisting that domain name in the hosts file.

---

### Post by Vaphell on 2010-10-29
i don't see why bookmarking wouldn't work. If it's bookmarked and it shows up in suggestions when typing the address manually, there is a bigass star next to it in firefox. Also I don't bother with typing the whole thing, 2 chars are enough to get any site i frequently visit on the top spot of the suggestion list.

... unless it's a porn site that should not show up in suggestions :-)

---

### Post by mistypotato on 2010-10-29
> **NickJones said:**
> Many Modems/Routers allow you to block certain IPs or URLs, or alternatley, you could just enter it correctly. You said the site is *mallicious *but as a Ubuntu users you should be relatively safe in terms of Viruses, Spyware and all of that fun stuff.

I was really looking for a solution similar to the way you set up hosts in the local network.

But blocking the offending site at the firewall is one solution.  Just not as elegant as I had desired.

This isn't about bookmarking or creating a "shortcut".  You might be surprised to know I have plenty of those on my browser.
I'm trying to learn to accomplish something different here.

But thank you all for that suggestion.

I have my reasons for wanting to do it they way I desire, much as those who chose Windows are making their choice of operating system....although most of us would likely agree we disagree with that :P

---

### Post by NickJones on 2010-10-29
The other option is just to delete the bad site from your history, that way if you type it in (Which I assume you must do if you keep inadvertently entering .COM rather than .NET) it will suggest the bookmarked one first.

On a slightly related note, here in Australia the largest commerical TV station's website is a .com.au domain, whereas a porn site has the exact same name but with the .com.

---

### Post by mistypotato on 2010-10-30
> **NickJones said:**
> The other option is just to delete the bad site from your history, that way if you type it in (Which I assume you must do if you keep inadvertently entering .COM rather than .NET) it will suggest the bookmarked one first.

On a slightly related note, here in Australia the largest commerical TV station's website is a .com.au domain, whereas a porn site has the exact same name but with the .com.

:KS:KS:KS:KS:KS

That is EXACTLY the nonsense I'm trying to avoid....but not necessarily for those kinds of sites...but other sites that do that as well.

I'm not sure why Internet authorities allow such nonsense....kickbacks and under the table payoffs is all I can think of?
Where there are humans....there is corruption.

It's also a VERY good idea to always purchase all the other popular DOT names when you buy a domain name...especially .COM and .NET

Also, I type a URL  faster than I can click a bookmark if it's not right on the links bar...but I sometimes forget if it's .com or .net

---

### Post by fly-by-night on 2010-10-30
If you use Firefox you can set a keyword for the site in the bookmark properties.  Then you type, for example, **ubab** (enter) to get to Ubuntuforums Absolute Beginners.  (**17** for my router page etc etc.)

---

### Post by baddnady23 on 2010-10-30
> **CharlesA said:**
> You could even go so far as blacklisting that domain name in the hosts file.

how would one do that?

---

### Post by CharlesA on 2010-10-30
Add an entry for that site in /etc/hosts like so:

```
127.0.0.1	somedomain.com
```

---

### Post by mistypotato on 2010-10-31
> **CharlesA said:**
> Add an entry for that site in /etc/hosts like so:

```
127.0.0.1	somedomain.com
```

Does that work outside the local network?

I tried that and it didn't work?

It was actually the FIRST thing I tried.

---


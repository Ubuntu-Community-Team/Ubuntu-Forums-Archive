---
title: "Will the Firefox moonlight plugin ever catch up to Silverlight"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by philinux on 2009-04-26
Silverlight is already at version 2.0 as of last October. 
[http://searchwindevelopment.techtarget.com/news/article/0,289142,sid8_gci1347768,00.html](http://searchwindevelopment.techtarget.com/news/article/0,289142,sid8_gci1347768,00.html)

This website in the UK uses silverlight so I cant use their service. I've mailed them to complain but get the usual fob off.

[http://www.itv.com/ITVPlayer/?intcmp=NAV_1002](http://www.itv.com/ITVPlayer/?intcmp=NAV_1002)

It initially use flash to show the options but then needs silverlight 2.0

---

### Post by TigerCR1200 on 2009-04-26
Is moonlight not working on the site? 

I am not at home so I cant test for myself. The only experience I have had with silverlight required sites moonlight as worked fine but I haven't ran across alot of them.

---

### Post by philinux on 2009-04-26
The site in question uses silverlight 2.0. The linux version is at version 1.0 so there you go.

---

### Post by spikoley on 2009-04-26
> **TigerCR1200 said:**
> Is moonlight not working on the site? 

I am not at home so I cant test for myself. The only experience I have had with silverlight required sites moonlight as worked fine but I haven't ran across alot of them.

Moonlight is not working on that site.  Most sites I have tested do not work because they use Silverlight 2.0.  It sounds like we will have to wait a few months because I heard Moonlight 2.0 will not be out until August.

---

### Post by philinux on 2009-04-26
Thats the worry. Microsoft will probably have version 3 out by then.:(

---

### Post by RavanH on 2009-05-15
Have you tested with [http://go-mono.com/moonlight-preview/](http://go-mono.com/moonlight-preview/) already ?

---

### Post by directhex on 2009-05-15
The answer to the question depends on 3 things:

1) How frequently will MS release Silverlight updates

2) How many of the changes they make will be made under a Free Software license

3) How major are the changes?

The third question is important because it puts some limitations on how much work is involved in reimplementing them - SL1 to SL2 was an enormous change, but SL2 to SL3 much less so. In fact, the Moonlight 2.0 pre-alphas currently available include some SL3 functions ALREADY that were only a day's work to implement.

The second question is important because Microsoft HAVE released parts of Silverlight under a Free license - for example, the "Silverlight Controls" (the widget toolkit, think GTK+) is Free, so Moonlight simply re-uses them.

The first question is probably the most important, and has the most unknowns. How frequently do Microsoft need to release? Well, SL3 still has many weaknesses compared to Flash (but some advantages), so they need to keep adding features. SL3 isn't out yet, and I've not heard any word of an SL4 yet, but it's really hard to tell.

As for ITV Player: [https://bugzilla.novell.com/show_bug.cgi?id=434461](https://bugzilla.novell.com/show_bug.cgi?id=434461)

---

### Post by philinux on 2009-05-17
> **RavanH said:**
> Have you tested with [http://go-mono.com/moonlight-preview/](http://go-mono.com/moonlight-preview/) already ?

Yep and installed the codecs from the right click options. But this is the problem for now as linked above.

[https://bugzilla.novell.com/show_bug.cgi?id=434461](https://bugzilla.novell.com/show_bug.cgi?id=434461)

---


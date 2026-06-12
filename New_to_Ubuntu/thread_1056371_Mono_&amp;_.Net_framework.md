---
title: "Mono &amp; .Net framework"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by HarleyDude on 2009-01-31
Ok, I am in the dark here.  I had asked a question in the general section and didn't get much help so did some reading.

I am trying to run an online app that works with firefox but requires a special firefox form viewer.  The form viewer requires .Net framework to install so that is why I was looking at Mono.  I did the mono install but still can't get the viewer to load.

I am new to Ubuntu and I do really like it but I've gotta get this online app to work or I'm kinda dead in the water.

Any help is appreciated.

---

### Post by HarleyDude on 2009-01-31
No Ideas?

---

### Post by directhex on 2009-01-31
You're not exactly being very descriptive

Perhaps little things like, I dunno, gthe name of the site in question might help

---

### Post by jrusso2 on 2009-01-31
By any chance is this silverlight or moonlight?

---

### Post by HarleyDude on 2009-01-31
Sorry bout that, the site is zipformonline.com , it is a real estate online forms that we use.  When I log into the site, it automatically detects I'm not using IE and there is a dialougue to download a forms viewer for firefox which I have successfully done many times under windows, but can't make it fly with Ubuntu/Firefox.  When I attempt to install the viewer, it advises it requires .net framework to install and that is where I run into problems.

Trying to search here, I found references to Mono.

Thanks

---

### Post by jrusso2 on 2009-01-31
Crap I hate that I need a login just to see whats up here.

---

### Post by HarleyDude on 2009-01-31
I will pm you the login

---

### Post by HarleyDude on 2009-01-31
Once you log in you will see a list of names, go to the far right column where there is a drop down arrow and select "Open" that is where it goes south for me.

---

### Post by HarleyDude on 2009-01-31
What if I install wine and run the windows version of firefox?

Any thoughts.

---

### Post by directhex on 2009-01-31
What format is this "forms viewer" distributed in?

It would help if you could upload it someplace for analysis

---

### Post by HarleyDude on 2009-01-31
I can copy the .exe file but don't know where I can paste it up, any thoughts?  I will check the size of it, but I think it is small.

---

### Post by HarleyDude on 2009-01-31
I can copy and paste the .exe but it is 17.3 MB, don't know where to paste it.

---

### Post by directhex on 2009-01-31
I don't think this is gonna work.

Thinking about it properly, if we're talking about a browser plugin, then the plugin part (i.e. the part which sits in the Firefox plugins directory) is not cross-platform - it would need to be compiled for your Ubuntu system. Even if (big if) the bulk of it is completely cross-platform (no Windows-only .NET assemblies or windows-only .dll files used at all) then you'd still have the problem of the plugin component.

Sites like rapidshare.com are useful for uploading random things if you still want to try, though

---

### Post by HarleyDude on 2009-01-31
What about the wine and windows version of firefox?

---

### Post by directhex on 2009-01-31
> **HarleyDude said:**
> What about the wine and windows version of firefox?

Closer the mark, but no promises

---

### Post by HarleyDude on 2009-01-31
I didn't want a dual boot, but guess that's my only option.  Thank you to those that tried to help me.

---


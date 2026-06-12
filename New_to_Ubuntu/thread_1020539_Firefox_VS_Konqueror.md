---
title: "Firefox VS Konqueror"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by oilchangeguy on 2008-12-24
It's sad that Konqueror will work with no problem at [www.citicards.com](www.citicards.com) but Firefox will not. I'm using Kubuntu 8.10 with Firefox 3.0.5 and the page will load. But you cannot sign in. Any thoughts?

---

### Post by retskrad on 2008-12-24
You should use keep both. But I believe you should use firefox as your default. if some sites doesnt work with firefox, maybe it works in konqueror.

Pz.

---

### Post by LowSky on 2008-12-24
It loads up fine for me, can you get us some screenshots of the main citicards website (with FF and Konq)? To get a better understanding of the issue.

---

### Post by oilchangeguy on 2008-12-24
> **LowSky said:**
> It loads up fine for me, can you get us some screenshots of the main citicards website (with FF and Konq)? To get a better understanding of the issue.
in the lower left of the screen it says read [www.citicards.com](www.citicards.com). it never says done. it's like the page will not fully load. and the red x is grayed out. so you can't stop it.

---

### Post by gjoellee on 2008-12-24
I have no problems with that website in FF 3.0.5

---

### Post by flanagan on 2008-12-24
The login mechanism on that page uses flash for some reason. Are you using any Firefox add-ons like FlashBlock or NoScript? Does it work for you in Firefox safe mode?

Debug your flash installation according to [http://kb.mozillazine.org/Macromedia_Flash](http://kb.mozillazine.org/Macromedia_Flash)

---

### Post by oilchangeguy on 2008-12-24
> **flanagan said:**
> The login mechanism on that page uses flash for some reason. Are you using any Firefox add-ons like FlashBlock or NoScript? Does it work for you in Firefox safe mode?

Debug your flash installation according to [http://kb.mozillazine.org/Macromedia_Flash](http://kb.mozillazine.org/Macromedia_Flash)

no flashblock, or noscript installed. not heard of firefox safemode. i will read the info link you provided.

---

### Post by flanagan on 2008-12-24
Here's the explanation of safe mode: [http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode)

---

### Post by ajgreeny on 2008-12-24
Just out of interest I have tried the page in FF3.0.5 and though it appears to load fully, none of the links in the page are active and you can not go anywhere from that page to another.  The status bar at the bottom does show "Done", but it does not seem that the page is properly displayed.

I have also tried it in konqueror and there it appears to load OK until the very end when suddenly the whole page disappears, apart from just a few selection buttons, but there is no way to know what they are for.  It seems to me this is more of a bad page type being hosted than a specific linux, FF or konqueror problem.

---

### Post by flanagan on 2008-12-24
I have to agree that the citicards page has some of the poorest implemented Flash I have seen in a while. You may have to right-click on a Flash area of the page to bring up the Flash context menu and select Play. The second time I went back to that page it did not load properly at all, but once I selected Play, the rest of the page loaded.

---

### Post by oilchangeguy on 2008-12-24
> **flanagan said:**
> I have to agree that the citicards page has some of the poorest implemented Flash I have seen in a while. You may have to right-click on a Flash area of the page to bring up the Flash context menu and select Play. The second time I went back to that page it did not load properly at all, but once I selected Play, the rest of the page loaded.

I did the right click thing. And was able to sign in. The page still said read, not done. But it let me sign in. This still does not explain why it works ok on some little known browser like Konqueror, and not a well known browser like FF.

---

### Post by FreewheelinFrank on 2008-12-24
In firefox:

Help>Report Broken Web Site

---

### Post by flanagan on 2008-12-24
> **oilchangeguy said:**
> ...This still does not explain why it works ok on some little known browser like Konqueror, and not a well known browser like FF.
I have had a load of other problems myself with Flash in Firefox with both 3.04 and 3.05. Flash worked great for me prior to 3.04. Some Flash sites work OK; some are horrendously slow and cause freeze-ups. Mostly lagging and partially loaded pages. I have had a lot better results on Flash sites when using Konqueror or Epiphany. I think you have a combination going on here: both a poorly coded page and a version of Firefox that simply does not do Flash very well.

---

### Post by oilchangeguy on 2008-12-24
> **FreewheelinFrank said:**
> In firefox:

Help>Report Broken Web Site

i did. but this a long known problem that ff does not seem to want to do anything about.

---

### Post by Thelasko on 2008-12-24
Maybe it's an issue with nspluginwrapper?  Just a thought.

---

### Post by jerrylamos on 2009-01-03
> **flanagan said:**
> I have had a load of other problems myself with Flash in Firefox with both 3.04 and 3.05. Flash worked great for me prior to 3.04. Some Flash sites work OK; some are horrendously slow and cause freeze-ups. Mostly lagging and partially loaded pages. I have had a lot better results on Flash sites when using Konqueror or Epiphany. I think you have a combination going on here: both a poorly coded page and a version of Firefox that simply does not do Flash very well.

jaunty flash firefox is working very well with youtube etc. for me.  This is Firefox 3.1

How do you get Konqueror to use flash??  The typical adobe install didn't enable flash for youtube.

Thanks, Jerry

---

### Post by flanagan on 2009-01-04
> **jerrylamos said:**
> jaunty flash firefox is working very well with youtube etc. for me.  This is Firefox 3.1

How do you get Konqueror to use flash??  The typical adobe install didn't enable flash for youtube.

Thanks, Jerry

You're right. I meant Opera (not Konqueror). I have had better luck in the last few days since updating to Adobe Flash Player 10.0 r15 (previous version was 10.0 r12). It looks like a case of Adobe not testing r12 with Firefox 3.04+ and maybe Mozilla developers not testing with r12 (or both).

---


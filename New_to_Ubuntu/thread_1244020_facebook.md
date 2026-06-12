---
title: "facebook"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-08-19
so facebook work really slow.
not just load put scrolling and even typing.

all my other sites for great, i dont have ANY idea why.

plz help my wife needs her facepage.

---

### Post by isee on 2009-08-19
Do you have NoScript  installed?  What web browser are you using?

---

### Post by wlraider70 on 2009-08-19
no on the no script

firefox 3.0.13

---

### Post by isee on 2009-08-19
I would try through a different browser, like Opera.  If that doesn't work, I would suspect that Facebook is just busy, or there are scripts trying to load.

You could try NoScript addon in Firefox.  Sometimes waiting for web page scripts can slow your computer.  NoScript is a bit of a pain, it blocks everything until you allow, but as far as I know, to run Facebook you only need to allow two scripts.

---

### Post by wlraider70 on 2009-08-24
Can i get opera from the synaptic manager?

I can't seem to find another install for linux.

---

### Post by Mrandersonjr on 2009-08-24
Facebook works just fine on my firefox on ubuntu hardy.

---

### Post by Thelasko on 2009-08-24
It's probably on Facebook's end.  It's a very popular site and it gets slow from time to time.

---

### Post by mathay on 2009-08-24
> **wlraider70 said:**
> Can i get opera from the synaptic manager?

I can't seem to find another install for linux.
Yes, you can get Opera from Synaptic but it's also available from their [website]("http://www.opera.com/browser/download/"). It's simple to install since it's in a .deb format. If you want any explanation, let me know though it should be pretty simple. 

If you're looking for the new Firefox version, go to Synaptic and type "firefox-3.5." Should be in the repository. This is assuming you have that specific repo enabled.

---

### Post by stalkier on 2009-08-24
> **wlraider70 said:**
> so facebook work really slow.
not just load put scrolling and even typing.

all my other sites for great, i dont have ANY idea why.

plz help my wife needs her facepage.

I know for a fact the everytime I try to load facebook it is slow. Typing etc is fine. The games on there run slow from time to time. I believe your problem is your connection to them. I think their servers need to be upgraded to allow extra bandwidth. 

Trying a different web browser wont hurt but honestly I dont think it will help too much. (I could be wrong, of course)

---

### Post by SOULRiDER on 2009-08-24
> **mathay said:**
> Yes, you can get Opera from Synaptic but it's also available from their [website]("http://www.opera.com/browser/download/"). It's simple to install since it's in a .deb format. If you want any explanation, let me know though it should be pretty simple. 

If you're looking for the new Firefox version, go to Synaptic and type "firefox-3.5." Should be in the repository. This is assuming you have that specific repo enabled.

I believe Opera needs QT as one of its dependencies, but I should double check. If thats the case installing it wont be a double-click thing.

---

### Post by MrWES on 2009-08-24
> **wlraider70 said:**
> so facebook work really slow.
not just load put scrolling and even typing.

all my other sites for great, i dont have ANY idea why.

plz help my wife needs her facepage.

Add this to your /etc/X11/xorg.conf file under device section.
```
Option "AccelMethod" "exa"
	Option "MigrationHeuristic" "greedy"

```

That will solve your choppy scroll and slow use of FB.

Bill

---

### Post by mobocracyminded on 2009-09-06
Flash 10 confirmed as the culprit for me.
Using 9 - and is quick once again.
Mob

---

### Post by somking95 on 2009-09-06
Facebook has been very slow for me. I have also had some popups out of facebook that resulted in new firefox tabs going to random websites. I assume this is a facebook problem and not with my os. ??

---

### Post by PowerWCRulez on 2009-10-09
Hello there, I'm having problem with Facebook's end found it's "IFRAME" on it,  Facebook disabled my clickable, grayed out typebox and most games on facebook very messed up with my firefox browser it's very older version 1.5.0.11, I want to play Mob Wars and other game on the facebook grrr...

Should I get Opera Browser download on the Opera Site they have Breezy on it.

TG or TGZ?

I am still using on Breezy Ubuntu on my laptop, no way to get updated it.

I need help with opera installation, because I am totally forgot which command should I need to install opera browser, I have not used "Installation" command for long time for the laptop computer.

I cannot use my Mobile Video Phone's opera browser, because of facebook's game very heavy, MVP very small of memory that sucks.

Thanks :)

---

### Post by guriinii on 2009-10-09
Facebook is the problem not you computer. It occasionally goes slow for me.

---

### Post by PowerWCRulez on 2009-10-09
> **guriinii said:**
> Facebook is the problem not you computer. It occasionally goes slow for me.

Oh well, Facebook could've a server's ram or clogged system or miscongfigure on their ends.

Did you tried normal facebook on your firefox, does clickable, typebox working? Mines is not.. I use a facebook lite for awhile, I can post on the wall messages to let them know about mines..

Facebook lite works good :)

---

### Post by CatKiller on 2009-10-10
> **PowerWCRulez said:**
>  I am still using on Breezy Ubuntu on my laptop, no way to get updated it.

You should still be able to go Breezy &#8594; Dapper &#8594; Hardy to upgrade. If you change your sources.list to old-releases.ubuntu.com (where no-longer-supported repositories go) you should be able to get any final updates to Breezy, including the update to the update-manager that will let you upgrade to Dapper.

---


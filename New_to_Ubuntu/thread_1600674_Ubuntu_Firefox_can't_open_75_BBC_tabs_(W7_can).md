---
title: "Ubuntu Firefox can't open 75 BBC tabs (W7 can)"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by ekcutvncmskslcdlcfjt on 2010-10-19
In Firefox, when I click Bookmarks toolbar>Latest Headlines>Open All In Tabs, Firefox soon stops responding and never recovers. In Windows 7 with Firefox there's no problem. These are about 75 tabs. 

I'm not critical, just asking if there's an explanation for this. Seems to be an OS issue. Not network or hardware.

Dual core atom 330 2GHz, 4GB RAM, Ubuntu 10.10 netbook, classic desktop mode

---

### Post by Grenage on 2010-10-19
Out of curiosity, how many of those pages have flash content?

What happens if you disable the flash plug-in?

---

### Post by ubudog on 2010-10-19
> **Grenage said:**
> Out of curiosity, how many of those pages have flash content?

What happens if you disable the flash plug-in?

Yeah, most of the BBC pages have flash somewhere on them.  Try disabling it and see what happens.

---

### Post by ekcutvncmskslcdlcfjt on 2010-10-19
I don't have a flash plugin, because  I did a quick "try without installing" from CD.

But disabling javascript did the trick. They now load quickly. So thanks for getting me on the right path.

---

### Post by Grenage on 2010-10-19
Good call.

Such things can add a reasonable amount of overhead, which adds up when running many (many) tabs.  If all were opened at the same time, I could understand the bottleneck.

The fact that it works well in IE is quite impressive.

---

### Post by ekcutvncmskslcdlcfjt on 2010-10-19
In windows I also used Firefox, that's why I thought it might be OS related.

---

### Post by Grenage on 2010-10-19
Ah touché, I guess it's quite likely OS handling it all then.

---

### Post by ubudog on 2010-10-19
Is anything else slow?  eg, Login, Administration, etc?

---

### Post by ekcutvncmskslcdlcfjt on 2010-10-19
> **ubudog said:**
> Is anything else slow?  eg, Login, Administration, etc?

 No, it's just fine.

---

### Post by jward3010 on 2010-10-19
I mean I suppose you can (if it works) open 75 tabs in a browser, but in general, why?

I mean, you can probably run Crysis and Far Cry 2 at the same time on a well endowed machine, probably wont work that well, but you still could - but why would you?

If you're just benchmarking, then great, I'd love to hear the results - but do you honestly open 75 tabs frequently?

---

### Post by Joshwaa on 2010-10-19
Why would you ever need 75 tabs open in one browser?
Ctrl-W - use it!
Glad you've found a solution though :)

---

### Post by ekcutvncmskslcdlcfjt on 2010-10-19
> **Joshwaa said:**
> Why would you ever need 75 tabs open in one browser?
Ctrl-W - use it!
Glad you've found a solution though :)

 I was bored and it's a menu option in Firefox so why not?

---

### Post by Joshwaa on 2010-10-19
> **ekcutvncmskslcdlcfjt said:**
> I was bored and it's an option in Firefox so why not?
There's an option to open 75 tabs?

---

### Post by ekcutvncmskslcdlcfjt on 2010-10-19
> **Joshwaa said:**
> There's an option to open 75 tabs?

 As I said in my first post I clicked &quot;Open All in Tabs&quot;. That's a menu option under Bookmarks>Bookmarks Toolbar>Latest Headlines. Then they open all up.

---

### Post by erjoalgo on 2010-10-19
Yea Firefox in Ubuntu sucks so bad, with every resume from hibernation and such, it freezes for about a minute or so, its so annoying I'm using chrome. This doesn't happen at all using Firefox on Windows.
Chrome takes a long time to start, and there's some privacy issues, and there are few plugins for customization, but it works.

---

### Post by ubudog on 2010-10-19
There is also Chromium, it's completely free and open-source (no privacy issues), and super fast.

[http://www.chromium.org/](http://www.chromium.org/)

Check it out.

---

### Post by hell_rider on 2010-10-20
I have this problem too when I am browsing photos on flickr.  Sometimes I will have close to 30-40 tabs open with photos I have found interesting.  (Because I want to show them to my wife or sister before I close the tabs)  The slowdown is quite distinct.  In fact anything over 15 tabs and you can sense Firefox slowing down with respect to response time.

---

### Post by alphacrucis2 on 2010-10-20
Being curious, I just tried this in Ubuntu 10.10 64 bit with the Adobe 64 bit Flash player - Java script enabled.. It works fine. I'm replying to this thread with 83 tabs open (I already has several open in addition to the 75 BBC headline ones).

---

### Post by mastablasta on 2010-10-20
> **ekcutvncmskslcdlcfjt said:**
> I don't have a flash plugin, [SIZE=4]**because I did a quick "try without installing" from CD.**[/SIZE]
.
 
 
there's your culprint. :KS 
 
the whole system is run from CD and RAM. do you have any idea how much slower CD read speed is compared to hard disk? it is slower A LOT!
 
when you try to do this in windows then you will see that is not possible there. :-P no windows live CD to try before you buy, and that doesn't damage data on your computer.
 
if you ran it form hard disk now that is a different story as user **alphacrucis2** points out.

---


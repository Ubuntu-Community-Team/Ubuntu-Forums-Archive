---
title: "Flash being weird and stuttery and hulu not loading at all"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by nothilaryy on 2009-08-24
Ok so flash in general is being odd. Any games I try to load or youtube videos are very stuttery. You can't really see any motion but things do change so its definitely playing. It works on my other computers so I don't think its an internet connection problem. Also, Hulu doesn't work at all- neither the main scrolling images nor any of the videos.

So far I've tried two different variants of flash I believe, but neither fixed the problem. I can't quite figure out which ones because I didn't write it down and I'm sort of confused by what I did. Both times I clicekd on something in the browser in mozilla, couldn't figure what to do with whatever downloaded and then went to the package manager and updated something. The second I'm almost positive was the the adobe one from the site. I'm not sure what the first one was.

My computer is an HP mini 110 netbook and I'm running ubuntu netbook remix. If you need to know anything else let me know, and thank you a lot in advance... I hope I don't sound toooo stupid.

---

### Post by Revolutionary101 on 2009-08-24
> **nothilaryy said:**
> Ok so flash in general is being odd. Any games I try to load or youtube videos are very stuttery. You can't really see any motion but things do change so its definitely playing. It works on my other computers so I don't think its an internet connection problem. Also, Hulu doesn't work at all- neither the main scrolling images nor any of the videos.

So far I've tried two different variants of flash I believe, but neither fixed the problem. I can't quite figure out which ones because I didn't write it down and I'm sort of confused by what I did. Both times I clicekd on something in the browser in mozilla, couldn't figure what to do with whatever downloaded and then went to the package manager and updated something. The second I'm almost positive was the the adobe one from the site. I'm not sure what the first one was.

My computer is an HP mini 110 netbook and I'm running ubuntu netbook remix. If you need to know anything else let me know, and thank you a lot in advance... I hope I don't sound toooo stupid.

I don't know why it is but flash seems to act that way for me too. I think this may have to do with the design the Linux kernel or Ubuntu themselves.

---

### Post by nothilaryy on 2009-08-24
Ugh really? I might have to rethink this ubuntu decision if thats the case. I need to be able to at least kind of watch youtube. And hulu. What else will I do with my spare time?

---

### Post by fuzzyllama on 2009-08-24
I fought the good fight against Flash in Ubuntu 8.04 w/Firefox.  Flash was choppy and unusable - if it would load at all!   I found two options that worked perfectly (after literally days of tinkering):

1.) Run the Windows version of Firefox in a WINE session.
   - or -
2.) Upgrade from 8.04 to 9.04 (can't comment on 8.10 as I migrated right through it...)

Either of these solutions allowed me to view hulu/youtube etc as I would using ...um... you know...

---

### Post by y-lee on 2009-08-24
You should have no problems with  flash and firefox in ubuntu, if you do something is wrong. To the OP do you still have the problem? Are you using adobes flash plugin? Type [noparse]about:plugins[/noparse] into firefoxes address bar and check it. Also be sure you are not using more than one flash plugin, I helped someone on this forum actually doing that, lol.

---

### Post by nothilaryy on 2009-08-25
Umm yeah I'm still having problems. Under the about:plugins it says

> Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type                                Description                 Suffixes     Enabled
application/x-shockwave-flash      Adobe Flash movie      swf           Yes
application/futuresplash              FutureSplash movie     spl            Yes

---

### Post by inobe on 2009-08-25
flash requires video acceleration, much memory and cpu.

lets get some system information !

also lets not make comparisons :)

---

### Post by kerry_s on 2009-08-25
> **nothilaryy said:**
> Umm yeah I'm still having problems. Under the about:plugins it says

thats not the real flash player.

[B]sudo apt-get remove --purge swfdec-mozilla
sudo apt-get install flashplugin-installer[/B]

---

### Post by nothilaryy on 2009-08-25
[This]("http://microcenter.com/single_product_results.phtml?product_id=0312882") is my computer. 

And I might be just being really stupid but I can't seem to enter anything into the command line. I've tried clicking on the root terminal and then it had be login, but then nothing happened. I clicked on it again, it didn't have me log in but still nothing happened. I feel sort of really dumb. All I was trying to do was enter in what Kerry_s said to.

---

### Post by hubertofliege on 2009-08-25
> **kerry_s said:**
> thats not the real flash player.

[B]sudo apt-get remove --purge swfdec-mozilla
sudo apt-get install flashplugin-installer[/B]


Someone sticky this!  Thanks, I couldn't get Pandora to work, and a lot of other interactive video sites didn't work either.  I didn't realize I had Swfdec instead of Adobe.  Thank you so much!

---

### Post by hubertofliege on 2009-08-25
Oh, also, don't feel dumb, this stuff can be really tricky.  I've just been dealing with flash not working for weeks, I didn't get it right away either.

---

### Post by argos3016 on 2009-08-25
Try making a new firefox profile with:
firefox -ProfileManager
And add a new profile
Good?

---

### Post by juanoleso on 2009-08-25
I was having the same kind of trouble with flash 10 in Debian Lenny so I downgraded to the latest version of 9.  Its buried on the adobe website, but it is available.  Just my 2 cents.

---

### Post by nothilaryy on 2009-08-25
> **kerry_s said:**
> thats not the real flash player.

[B]sudo apt-get remove --purge swfdec-mozilla
sudo apt-get install flashplugin-installer[/B]

Oh my goodness! That completely worked. Thank you so much!

---

### Post by Skantch on 2009-08-25
Thanks for the help Kerry_s!

---

### Post by fuzzyllama on 2009-08-31
> **y-lee said:**
> You should have no problems with  flash and firefox in ubuntu, 


I highly disagree.  You could spend days sorting through all the complaints about the flash plug-in.  It just doesn't play nice in the majority of situations. Telling new users that it "should work" implies that they are doing something wrong... Admitting you have a problem is the first step.  

Save yourself hours of frustration; use the Windoze version in Wine.

---

### Post by y-lee on 2009-08-31
> **fuzzyllama said:**
> 
[QUOTE=y-lee;7841522]You should have no problems with  flash and firefox in ubuntu,

I highly disagree.  You could spend days sorting through all the complaints about the flash plug-in.  It just doesn't play nice in the majority of situations. Telling new users that it "should work" implies that they are doing something wrong... Admitting you have a problem is the first step.  

Save yourself hours of frustration; use the Windoze version in Wine.[/QUOTE]

Yes it is true many people often have problems with flash, it seems to be a common problem. But my original quote was:

> **y-lee said:**
> You should have no problems with  flash and firefox in ubuntu, **if you do something is wrong.**

And indeed i feel this is the case, that if flash is not working right there is some problem. This does not imply the new user has necessarily did something wrong. Altho in some cases they have. In some they haven't tho, the problem could be caused by some other issue like graphics card driver or whatnot. In either case if flash is not working right in firefox something is wrong and hopefully we can on this forum figure out the problem and help fix it.

I have installed ubuntu on alot of machines starting with Dapper Drake and never not even once had any problem whatsoever with flash not working right. I have had other problems webcams and wireless cards and whatnot but none with flash.

and to me the suggestion to > Save yourself hours of frustration; use the Windoze version in Wine.  is at best a last resort and at worst a really bad idea. To put it bluntly i never advise using Wine and while it may work for firefox and flash it has never worked right for any windows application I have wanted to use in linux, IMVU client for example.

---

### Post by josephpmh on 2009-08-31
I had the same problem.  I solved it by disabling adblock for hulu.  Apparently, they really want you to watch the ads:(

Still, the ads are less than broadcast/cable tv.  Guess I'll just have to unsuspend my disbelief when the ads popup.

---


---
title: "general software conflicts how can i resolve"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-14
hi, sorry the question is so vague.  i just want to know if there might be some software anybody can recommend that can work through my system and locate software/plugins etc that might interfere with the effective operation of ubuntu/applications.  i have searched synaptic etc and have come up dry so far.  i am an idiot so would prefer it to be gui based or reasonably simple command line.  or something to tell me if apps/plugins etc are missing.  stupid question i know but i thought it was worth a try.
cheers
nigel

---

### Post by Paqman on 2009-01-14
What actual problems are you having?

---

### Post by Terl on 2009-01-14
Paqman is right, we need specific questions in order to help better.  Are you having difficulties or errors with specific applications?  If so, one way to find out what is going on is to launch the program from the terminal (command line).  This will help identify some spots with errors.

Are you receiving errors or complaints from specific programs?

---

### Post by capnthommo on 2009-01-14
hi and thanks to you both.  i cant actually pin it down to specific problems except that, for example, i couldnt get dvds to play.  when i tried, the player (tried quite a few) would start the process and then close itself/disappear.  i eventually solved by installing a different/non free graphics card driver, but i thought at first that maybe one dvd player was interfering with another in some way.
what i suspect though is that i may have a bunch of different things loaded from synaptic and that some may conflict with others and i was just wondering if there was a simple way to get redundancies or conflicts or settings issues identified and hopefully cleared up.  for example, i read somewhere that on windows having more than one anti virus can mean that neither works properly - so i wanted to avoid this kind of thing happening with any of the apps i am running on ubuntu.
so i just want to be able to kind of 'pick up my computer and give it a good hard shake' so all the oddments and troublesome bits fall out!  yes, i know i'm looking for a kind of magic wand but it was definitely worth a shot.
thanks
nigel

---

### Post by Paqman on 2009-01-14
> **capnthommo said:**
> 
what i suspect though is that i may have a bunch of different things loaded from synaptic and that some may conflict with others

The good news is that that's pretty unlikely.

If you have trouble with an app (like a media player) then a good thing to do is try launching it from a terminal window. For example, if you were using VLC, open a terminal and type:
```

vlc

```

The when you (try to) play your DVD it'll spit out error messages into the terminal, and you can post them here.

Just a quick one though, have you got all the usual codecs installed? Try installing ubuntu-restricted-extras (or xubuntu- kubuntu if you're using that flavour)

---

### Post by PriceChild on 2009-01-14
> **Paqman said:**
> Just a quick one though, have you got all the usual codecs installed? Try installing ubuntu-restricted-extras (or xubuntu- kubuntu if you're using that flavour)For css encrypted dvds (pretty much anything you haven't burnt yourself) you'll need more than that. You'll need to install libdvdcss2 from [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) (unless it is illegal for you to do so of course)

If it is illegal for you to download and install libdvdcss2 you can buy it from [http://shop.canonical.com/product_info.php?products_id=243](http://shop.canonical.com/product_info.php?products_id=243)

---

### Post by capnthommo on 2009-01-14
okay folks, thanks again to everybody.  i'm afraid i seem to have lost the thanks button on the forum but i would have clicked it if it had been there.
i shall close this one now and if i have any further issues along these lines i shall raise them individually.
cheers everybody
nigel

---


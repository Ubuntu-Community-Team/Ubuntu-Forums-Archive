---
title: "Ubuntu 9.04 I need help with Itunes/my ipod! Please help a newbie!"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by xFlowx on 2009-06-30
Hi! This is my second day using Ubuntu. Earlier I had a problem with something else and some wonderful people helped me!

As the title says, I need help with itunes ooor my ipod.

You see, I have around 400 songs on my ipod, and at least one movie. I intended on using this tomarrow, but I haven't added new songs in a very long time, so I was hoping I could use Ubuntu to get this to work. And I don't really want to loose all my songs, because I've bought a lot of songs off of Itunes...and I just use itunes a lot.

I also have no idea how to use itunes in wine. Or how to use wine at all, lol.

Any and all help is appriciated!

Thanks!

---

### Post by aysiu on 2009-06-30
iTunes in Wine is difficult to set up and not fully functional.

Better to use a native Linux program like Banshee, AmaroK, Rhythmbox, Songbird, or GTKPod.

More details here:
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by xFlowx on 2009-06-30
> **aysiu said:**
> iTunes in Wine is difficult to set up and not fully functional.

Better to use a native Linux program like Banshee, AmaroK, Rhythmbox, Songbird, or GTKPod.

More details here:
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

Well, if I use those...I'm going to loose everything on my ipod, right?

I'd prefer to use itunes if at all possible...

---

### Post by BinaryFeast on 2009-06-30
Unfortunately, Wine will not run iTunes good enough to sync with an iPod. There are alternative programs for syncing such as gtkpod, but I tried that one and it corrupted my mp3's. Instead I suggest running iTunes on windows in VirtualBox. If you don't have a windows install cd, you could dowload the windows 7 rc for free on Microsofts site.

---

### Post by aysiu on 2009-06-30
> **xFlowx said:**
> Well, if I use those...I'm going to loose everything on my ipod, right?

I'd prefer to use itunes if at all possible...
Where are you getting this idea you'll lose everything on your iPod?

First of all, before loading any program, plug in your iPod, show hidden files (Control-H) and copy the songs from your iPod to your computer.

Once that's done, load the program. It will not automatically sync, as iTunes does by default (which does erase everything on your iPod).

---

### Post by balachandarlinks on 2009-06-30
Gtkpod ll be a good replacement...

---

### Post by xFlowx on 2009-06-30
> **aysiu said:**
> Where are you getting this idea you'll lose everything on your iPod?

First of all, before loading any program, plug in your iPod, show hidden files (Control-H) and copy the songs from your iPod to your computer.

Once that's done, load the program. It will not automatically sync, as iTunes does by default (which does erase everything on your iPod).

I keep thinking I'll loose everything because I'm a former windows user and that's what happened on Windows D: I'm overly paranoid.

When I do that...I can't find my songs...just weird files. It's odd.

---

### Post by BinaryFeast on 2009-06-30
> **xFlowx said:**
> I keep thinking I'll loose everything because I'm a former windows user and that's what happened on Windows D: I'm overly paranoid.

When I do that...I can't find my songs...just weird files. It's odd.

 If I remember correctly, the song names on an iPod are actually renamed to stuff like "AGXC.mp3" when synced with iTunes. Then the real names are decrypted when viewed on the iPod. I think.

---

### Post by Paqman on 2009-06-30
> **xFlowx said:**
> I keep thinking I'll loose everything because I'm a former windows user and that's what happened on Windows D: I'm overly paranoid.


I'm not surprised. The only times i've used iTunes i've found it a nightmare. Be glad you're rid of it. A good Linux music player like Banshee or Amarok will do a much better job of handling your iPod.

---

### Post by xFlowx on 2009-06-30
> **Paqman said:**
> I'm not surprised. The only times i've used iTunes i've found it a nightmare. Be glad you're rid of it. A good Linux music player like Banshee or Amarok will do a much better job of handling your iPod.

But you see, I buy things off of itunes and that means the money I have on it is gonna go to waste! And I have my favorite movie on my ipod that I bought on itunes.

But if I copy/paste everything on my ipod and store it to my computer, can I access it? You seem to know a lot about this...This is starting to upset me XD

---

### Post by balachandarlinks on 2009-06-30
Hippo Ipod management tool is also satisfactory...

---

### Post by xFlowx on 2009-06-30
> **balachandarlinks said:**
> Hippo Ipod management tool is also satisfactory...

Edit: It says that it doesn't have one that will support my Ubuntu? [http://www.getdeb.net/app.php?name=hipo](http://www.getdeb.net/app.php?name=hipo)

How does it work? O___o

---

### Post by Paqman on 2009-06-30
> **xFlowx said:**
> But you see, I buy things off of itunes and that means the money I have on it is gonna go to waste! And I have my favorite movie on my ipod that I bought on itunes.

But if I copy/paste everything on my ipod and store it to my computer, can I access it? You seem to know a lot about this...This is starting to upset me XD

Depends, if you bought DRMed music and movies, you're prossibly scuppered. There may be ways to strip the DRM out, but I wouldn't know, and doing so could be illegal, depending on what the law says in your country.

This is why DRM is bad. It ends up putting people in the position where they can't use stuff they've paid for.

---

### Post by xFlowx on 2009-06-30
> **Paqman said:**
> Depends, if you bought DRMed music and movies, you're prossibly scuppered. There may be ways to strip the DRM out, but I wouldn't know, and doing so could be illegal, depending on what the law says in your country.

This is why DRM is bad. It ends up putting people in the position where they can't use stuff they've paid for.


Lol, in America most things are illegal. Then again, I'm not familiar with all the laws because I'm only sixteen.

I can't figure this thing out and it's bothering me greatly...someone else told me about [http://www.getdeb.net/app.php?name=hipo](http://www.getdeb.net/app.php?name=hipo) but it looks like it doesn't have a version for Ubuntu...

---

### Post by Paqman on 2009-06-30
> **xFlowx said:**
> 
I can't figure this thing out and it's bothering me greatly...someone else told me about [http://www.getdeb.net/app.php?name=hipo](http://www.getdeb.net/app.php?name=hipo) but it looks like it doesn't have a version for Ubuntu...

The first place to look for Ubuntu software is always Synaptic. Go to System > Admin > Synaptic and install Hipo.

However, any of the normal media players such as Rhythmbox, Banshee, Amarok, Exaile, etc can all talk to most iPods without needing any extra software. Up to you what you use, really.

---

### Post by balachandarlinks on 2009-06-30
> **xFlowx said:**
> Edit: It says that it doesn't have one that will support my Ubuntu? [http://www.getdeb.net/app.php?name=hipo](http://www.getdeb.net/app.php?name=hipo)

How does it work? O___o
Im using it in Ubuntu 8.10 .Working fine.May be you ll get the upgraded version soon.You can try that version too.It may support.

---

### Post by powel212 on 2009-06-30
I use virtualbox to run a windows guest in Jaunty.

Then I have iTunes running natively in windows and sync my ipod from there.

This is the best way I have found.

Here is what it looks like

[http://www.flickr.com/photos/sunrisefoto/3567107074/](http://www.flickr.com/photos/sunrisefoto/3567107074/)

Sun Virtualbox is awesome.

I use it to run photoshop natively in windows without having to run a dual boot.

It requires some pretty decent hardware but if you have that there is nothing stopping you. Have fun.

I hope that helps.

Powel

---

### Post by tobiasolesen on 2009-06-30
Hi

I just started using Banshee this moment... put my ipod in and it said it had to make it ready for banshee to use...

I did this and after it was done the songs on my ipod was not deleted... I own a nano 8GB.. do not have any pictures (or movies of course) so not sure about that...

seems to work great though..

tobias

---

### Post by sadaruwan12 on 2009-06-30
Yes Banshee is good and don't be afraid to try things in the free world where theres no bills and gates to corner you. And check out free sites where you can get grate free mp3s for your IPOD.

And remember Google is your friend ask him first.

---

### Post by xFlowx on 2009-06-30
> **Paqman said:**
> The first place to look for Ubuntu software is always Synaptic. Go to System > Admin > Synaptic and install Hipo.

However, any of the normal media players such as Rhythmbox, Banshee, Amarok, Exaile, etc can all talk to most iPods without needing any extra software. Up to you what you use, really.

I think I found Hipo...Thank you.

---

### Post by xFlowx on 2009-06-30
> **tobiasolesen said:**
> Hi

I just started using Banshee this moment... put my ipod in and it said it had to make it ready for banshee to use...

I did this and after it was done the songs on my ipod was not deleted... I own a nano 8GB.. do not have any pictures (or movies of course) so not sure about that...

seems to work great though..

tobias

Hmmm...okay! Thanks...this helps.

---

### Post by xFlowx on 2009-06-30
> **Paqman said:**
> Depends, if you bought DRMed music and movies, you're prossibly scuppered. There may be ways to strip the DRM out, but I wouldn't know, and doing so could be illegal, depending on what the law says in your country.

This is why DRM is bad. It ends up putting people in the position where they can't use stuff they've paid for.


I have no idea what that means. o___O; But it means that I'm out a lot of songs I could've bought...

---

### Post by aysiu on 2009-06-30
*DRM* stands for *Digital Rights Management*. iTunes, until recently, sold songs only with the stipulation that they had to be played on a limited number of "authorized" computers or devices. If you bought stuff from iTunes last year or earlier, then it's very likely you'll be unable to play that stuff without iTunes.

---

### Post by xFlowx on 2009-06-30
> **aysiu said:**
> *DRM* stands for *Digital Rights Management*. iTunes, until recently, sold songs only with the stipulation that they had to be played on a limited number of "authorized" computers or devices. If you bought stuff from iTunes last year or earlier, then it's very likely you'll be unable to play that stuff without iTunes.

Nope! I just bought the stuff...But now I understand what you mean. But...I'm pretty sure I still have a few computers I can authorize to play the stuff.

Thank you! I'm going to try Hipo right now!

Edit: I can't seem to get Hipo to work!

---

### Post by TSWMIN85 on 2009-07-21
> **BinaryFeast said:**
> If I remember correctly, the song names on an iPod are actually renamed to stuff like "AGXC.mp3" when synced with iTunes. Then the real names are decrypted when viewed on the iPod. I think.

That is indeed correct.

---


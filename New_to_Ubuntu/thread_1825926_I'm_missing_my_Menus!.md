---
title: "I'm missing my Menus!"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by AbeFM on 2011-08-16
Howdy folks. So I'm not new to ubuntu, but I'm new to the latest version - and with the slick new interface comes a big problem: I can't find all that awesome free software I keep trying to tell people about!

In the old menus - I could go to "Games" or "Internet" and find lots of... you guessed it, games, or internet. Now... I have to remember the names of every one of 150 games? Nope. I don't have time to memorize all that.

So I switch back to the classic interface, then I miss the search. The truth is, I'd like to work with the new system - but I want to at least be able to find things by their classic groupings.

Can anyone help??
              -Abe.

---

### Post by Alwimo on 2011-08-16
Oh, I responded to you in a different thread but I misunderstood you there.
 
Well, you can use something like this in Unity but it is not as good, so the classic interface is better for your workflow. But those menus do exist in Unity. You just have to click on the applications lens, then in the top right you'll see "All Applications". You can click on that and look at "Games" or "Internet".
 
You can add the searching to the classic interface by installing Synapse. There's also GNOME Do, Kupfer and perhaps some others. It's really good, and I think it's the best option for you to install one of these in the classic Gnome interface.

---

### Post by beew on 2011-08-16
You can install classical menus in Unity.

[http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html](http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html)

---

### Post by prshah on 2011-08-16
> **AbeFM said:**
> I'd like to work with the new system - but I want to at least be able to find things by their classic groupings.

In the list of applications, next to the search box, you will find an option "Refine search". If you click this, it will open a category selection (where you will find the classic categories, eg Games, Internet, etc). Tick the category/(ies) that you want and only those relevant applications will be displayed.

If you leave the refine search option open (Eg, don't collapse it), it will appear everytime you open the applications selection screen.

---

### Post by beew on 2011-08-16
> **prshah said:**
> In the list of applications, next to the search box, you will find an option "Refine search". If you click this, it will open a category selection (where you will find the classic categories, eg Games, Internet, etc). Tick the category/(ies) that you want and only those relevant applications will be displayed.

If you leave the refine search option open (Eg, don't collapse it), it will appear everytime you open the applications selection screen.

Don't think that is the "menu" that OP is looking for. You can't have a glance of all apps by category easily. I launch applications with the dash, but if I just want to see a list of what is installed I would still prefer the classic menu (see my link above)

---

### Post by AbeFM on 2011-08-16
Ah, thanks. That's sort of the situation I thought I was in - but there's some good suggestions which might just make this livable.

The fact the filter stays up is handy. If it's one extra click, I can live with it for all the advantages that Unity does have.

I added some search thing to the classic interface for a bit, but kept being on the fence. I'll try some of these suggestions and perhaps be better off. (It'd be nice if the filters could automatically apply by typing - i.e. "games" would filter on games. games(space)pong, etc...

---

### Post by AbeFM on 2011-08-16
Huh. Home now. No "refine search" and no "all applications".

This is a several-times-upgraded OS. For that matter, I've tried both interfaces. Maybe something got lost along the way?

---

### Post by AbeFM on 2011-08-16
Ah! That Classicmenu thing works awesome. 

> Update: there's now a PPA too:
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

Fantastic - it even has all the sub-menus!

---

### Post by Astrals on 2011-11-05
Classicmenu.

This works for me making my work flow faster!
The basic applications menu should be available from default installation for desktop users!

The only thing one should beware of is the disclaimer from launchpad Personal Package Archive [COLOR=Blue]["**Important:** The contents of Personal Package Archives       are not checked or monitored. You install software from them at your own       risk."]("https://launchpad.net/%7Ediesch/+archive/testing")[/COLOR]

[COLOR=Blue][https://launchpad.net/~diesch/+archive/testing]("https://launchpad.net/%7Ediesch/+archive/testing")

[COLOR=Black]Click on[/COLOR][/COLOR] "Read about installing"

If you miss your classic menu for faster navigation then this does the job nicely.

---

### Post by 3rdalbum on 2011-11-05
The "Refine filters" was added in 11.10. Judging from your description I imagine you're using 11.04?

In 11.04 it's actually a little easier IMHO. Right-click on the Applications icon toward the bottom of the Launcher (the bar on the left). Click on Games from the menu and it will show a list of games. Choose any other category instead and it will show only that category - it's pretty similar to the old-style menu in this regard.

---

### Post by AbeFM on 2011-11-18
From what I've found, at BEST it's a slower way to accomplish the same thing. The menus are a well thought out way to organize a large amount of information.

As a general rule, you could use the slogan "Takes Longer in Linux!" to describe what I feel each time I "upgrade" the OS.

There's lots of clever stuff in each release, but the experience goes downhill by removing functionality.

It'd be like removing all paved roads and saying how you can still get to Burger King by cutting across that field. Possible? Sure. Slower? Definitely. Guaranteed to work, where it always worked before? No, not really.

If you want to hide the menus by default, fine. But make it a nice simple system option to turn them back on. With both installed, I use the menus about 50% of the time on my desktop, about 15% of the time on the laptop.

---

### Post by winjeel on 2011-11-18
> **AbeFM said:**
> Ah! That Classicmenu thing works awesome. 

> Update: there's now a PPA too:
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator                      Fantastic - it even has all the sub-menus!


I just updated from 11.04 (using classic desktop) to 11.10 and would have absolutely regretted it  if I hadn't found this plugin / application alternative. It looks like it also gives the best of both worlds, too. However, it's fair to also say that I might drop Ubuntu in the future because I want a quick and easy access menu system, and I don't want to always be searching for things.

---

### Post by mlentink on 2011-11-19
> **AbeFM said:**
> As a general rule, you could use the slogan "Takes Longer in Linux!" to describe what I feel each time I "upgrade" the OS.

I disagree. I didn't use Unity in natty, felt I didn't care for it much. Only recently upgraded to oneiric, because I wanted t avoid it (Unity i.e.), but installed it on a USB-disk to play around with it. Then found out about Quicklists. Makes doing what I need to do regularly a whole lot faster. No more Applications>Audio and Video>OpenShot, but leftclick-rightclick bang!

Think of me as a power-user who doesn't think Unity is that bad after all. Come precise I might even start to like it!

---

### Post by AbeFM on 2011-11-21
I'll have to mess with quicklists some! It sounds awesome.

But... It's the anti-solution to what I'm talking about. I've got a bazillion installed apps. Anything I want to do, there's something there for it. It rocks, it's taking advantage of all the available free goodies.

The issue is, I need a way to find them categorically - without knowing their name - only their function.

I'd also like it if my i3 were supported. :-(

Anyway, if you have a better shortcut/suggestion on that, I'd love to hear it. I'm ALL for making stuff faster for things you do regularly, but, I'm talking about... "browsing my OS".

---


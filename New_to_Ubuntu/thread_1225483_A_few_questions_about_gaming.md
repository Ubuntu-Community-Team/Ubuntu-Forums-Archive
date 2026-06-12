---
title: "A few questions about gaming"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-07-28
Is Daemon tools or a similar program available? I have been trying to find out, but most of the info I've come across is a few years out of date. If such a program does not exist, I have the impression there is a command I can run (though I've had no luck whatsoever in trying to interact with the terminal). Will that command mount anything other than iso type files? 

More specifically, will it mount, allow me to install, and then run something like Sims 2 from a disc image? Will anything, or are games like this not allowed on Ubuntu? I keep reading things about copy protection which have given me the impression that this free software will only play other free software, and "linux is not for gaming" and whatnot.

---

### Post by CLomax on 2009-07-28
```
sudo apt-get install Gmount-iso
```

It can only mount .iso files as far as I'm aware.

Also, according to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633) Sims 2 doesn't work with WINE but there are many that do. That site is a good resource for finding out what works and what doesn't.

---

### Post by TeoBigusGeekus on 2009-07-28
Linux is made by hackers man!
No problems with copy protection - the problem is that 99.9% of the games in the market are made for windows. Now, you can install wine and try to play some (but not all of them).
For info about which windows apps works with wine, go to
[http://appdb.winehq.org/appbrowse.php]("http://appdb.winehq.org/appbrowse.php")
About mounting images:
Check this tutorial
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")
as well as AcetoneISO
[http://www.acetoneteam.org/]("http://www.acetoneteam.org/")

---

### Post by CatKiller on 2009-07-28
> **rahrahmah said:**
> I keep reading things about copy protection which have given me the impression that this free software will only play other free software, and "linux is not for gaming" and whatnot.

Not at all. The games that I run in Linux run much better than they did in Windows. It's just that that isn't all the games that I used to run in Windows. Copy-protection is designed to stop the game working, after all. That is its entire purpose.

The number of non-Free Linux-native games is quite small. So you're probably talking about using [Wine]("http://www.winehq.org/") to play your games with. You don't need any particular software to use an image as a drive in Wine. Just mount your image and tell Wine (through winecfg) to treat the place that you've mounted your image as a drive for your pretend Windows environment.

In normal running you don't need to go through any weird steps to tell Linux that an image is a drive. Linux doesn't have drives.

EDIT: There are some tools in the repositories for converting some other image file types into .iso files. You might find those useful.

---

### Post by starcannon on 2009-07-28
> **rahrahmah said:**
> Is Daemon tools or a similar program available? I have been trying to find out, but most of the info I've come across is a few years out of date. If such a program does not exist, I have the impression there is a command I can run (though I've had no luck whatsoever in trying to interact with the terminal). Will that command mount anything other than iso type files? 
 
More specifically, will it mount, allow me to install, and then run something like Sims 2 from a disc image? Will anything, or are games like this not allowed on Ubuntu? I keep reading things about copy protection which have given me the impression that this free software will only play other free software, and "linux is not for gaming" and whatnot.
 
gisomount is my favorite disk image mounting utility, it has a gui and everything.
Running windows games on linux is possible; however, not all games will work, and of those that do work many of them will not perform as well as they do on their native OS.
 
One of the more successful windows games running on linux is World of Warcraft. You will need a windows compatibility layer, there are 3 to choose from.
[LIST=1]
[*][Wine]("http://www.winehq.org/")
[LIST]
[*]Advantages
[LIST]
[*]Free as in beer
[*]Highly configurable
[*]Available in the Ubuntu Synaptic Package Manager
[/LIST]
[*]Disadvantages
[LIST]
[*]Requires a learning curve to really get things set up just right.
[/LIST]
[/LIST]
[*][Crossover Games]("http://www.codeweavers.com/products/cxgames/")
[LIST]
[*]Advantages
[LIST]
[*]Try before you buy option.
[*]I can't really say, I've not used it, perhaps someone can fill this in?
[/LIST]
[*]Disadvantages
[LIST]
[*]It costs money.
[*]I can't really say, I've not used it, perhaps someone can fill this in.
[/LIST]
[/LIST]
[*][Cedega]("http://www.cedega.com/")
[LIST]
[*]Advantages
[LIST]
[*]Great gui for mounting disk images.
[*]Great gui for tuning for a particular game, with game detected pretunes available, and drop down menu to choose a game pretune from.
[*]Ability to vote on what games you would like to see made "officially supported" in future releases of Cedega.
[*]The gui really does make installing windows games in linux pretty painless.
[/LIST]
[*]Disadvantages
[LIST]
[*]It costs money, indeed its on a subscription. The nice thing is, if you decide to quit paying the subscription, your Cedega still works, it just won't recieve updates, and you won't be able to vote any longer.
[*]Support is flaky or non existent.
[*]Some games are problematic, and can require a lot of fiddling with the gui to get working
[*]Some games must be turned way down graphically in order to have a playable frame rate; the more ram you have, the better things will work.
[/LIST]
[/LIST]
[/LIST]So thats just my 2 bits on it all; my advice would be read, read, read, and then choose the best one for you. I keep meaning to try crossover games out, but really haven't had time for gaming lately, so its been put on the back burner until this winter most likely.
 
GL and let the games begin.

---

### Post by rahrahmah on 2009-07-29
Well, that's kind of disappointing, but thanks for the good info.

---

### Post by Clorow on 2009-07-29
Crossover Games:

[LIST]
[*]Advantages
[LIST]
[*]If you buy it, a small portion helps fund Wine.
[*]Usually better support for games than Wine.
[/LIST]
[/LIST]

---

### Post by binbash on 2009-07-29
you can mount via

sudo mount -o loop asdasd.iso /mount/point/here/

this command easily.Better than daemon tools

---

### Post by MelDJ on 2009-07-29
or you could install windows xp under virtualbox and install the games there. But you cant play many high graphic game. I play Age Of Empires 2 on it (quite old game) and it works fine

---

### Post by starcannon on 2009-07-29
> **MelDJ said:**
> or you could install windows xp under virtualbox and install the games there. But you cant play many high graphic game. I play Age Of Empires 2 on it (quite old game) and it works fine

Yeah, any 3d intensive games this won't work for... "yet", virtual machine vendors are working on graphic card pass through like they have for cpu's, and have some limited 3d support even now. I reckon in 3yr's or perhaps 5, we'll see some cool stuff happening with virtual machines and directX; of course, with Microsoft's recent turn towards embracing towards open source (yeah, I know, keep our guard up), we may see a DirectX native client; that'd be the shiznizzle no? Hell, I'd pay for a native DirectX client (pay heed MS, theres money to be made, I'm not the only Linux gamer).

GL and HF

---

### Post by Crunchy the Headcrab on 2009-07-29
> **starcannon said:**
> Yeah, any 3d intensive games this won't work for... "yet", virtual machine vendors are working on graphic card pass through like they have for cpu's, and have some limited 3d support even now. I reckon in 3yr's or perhaps 5, we'll see some cool stuff happening with virtual machines and directX; of course, with Microsoft's recent turn towards embracing towards open source (yeah, I know, keep our guard up), we may see a DirectX native client; that'd be the shiznizzle no? Hell, I'd pay for a native DirectX client (pay heed MS, theres money to be made, I'm not the only Linux gamer).

GL and HF

There's a lot of stuff I'd pay for in Linux.  Namely legal codecs etc.  If a company like Canonical had a secure way to buy _directly_ from them (not a third party), I would do it for sure.

---

### Post by MelDJ on 2009-07-29
i have read that vmware has directX 8 support. not sure. might need to read it up again:)

---

### Post by Crunchy the Headcrab on 2009-07-29
> **MelDJ said:**
> i have read that vmware has directX 8 support. not sure. might need to read it up again:)
That's a good start, but I need 9 at least.  I have a feeling I'll be installing windows again within a years time just so I can play StarCraft 2. :guitar:

---

### Post by MelDJ on 2009-07-29
hope the guys at sun or vmware can find a way to get directX support for virtual machines. then i won't have to keep my windows xp anymore:popcorn:

---

### Post by CatKiller on 2009-07-29
> **Crunchy the Headcrab said:**
> There's a lot of stuff I'd pay for in Linux.  Namely legal codecs etc.

You mean like [this]("http://shop.canonical.com/index.php?cPath=19")?

---

### Post by MelDJ on 2009-07-29
cant we just download the codecs form the restricted packages?

---

### Post by starcannon on 2009-07-29
> **MelDJ said:**
> cant we just download the codecs form the restricted packages?

Yes, but they are not official, and not um.. sanctioned? is that the word I'm looking for? Licensed? Whatever, they are not Hollywood Approved anyway. Fluendo and Linux PowerDVD are what you want if you would like the final word in industry standard/approved codecs and DVD playback/decryption.

---

### Post by MelDJ on 2009-07-29
whats the difference other than licensing? Is the sound/video quality different?

---

### Post by CatKiller on 2009-07-29
> **MelDJ said:**
> whats the difference other than licensing?

That is the difference. Mathematics is illegal in the USA, Australia, and a couple of other places. Paying for the codecs makes it legal, even there. If you live in a country where mathematics is legal you don't need to pay for them.

It's not that the restricted-extras codecs aren't official, or sanctioned by Canonical. It's that they can't legally distribute them to countries where mathematics is illegal. So they'd need to either not include them anywhere, and let users install them themselves if they have determined the codecs to be legal, or distribute many different versions for each of the different countries that have laws on mathematics. They chose the easy one.

---

### Post by MelDJ on 2009-07-29
i think it all makes sense to me now
:o

---

### Post by frunns on 2009-07-29
It doesn't make sense to me. I've just accepted it before, now that I hear an explanation, I'm clueless. Illegal mathematics?

---

### Post by CatKiller on 2009-07-29
> **frunns said:**
> It doesn't make sense to me. I've just accepted it before, now that I hear an explanation, I'm clueless. Illegal mathematics?

Software patents.

Software is just mathematics. It isn't "like" mathematics, it **is** mathematics. Anyone that suggests otherwise hasn't studied mathematics.

Patents provide a government-backed monopoly to the patent holder. This means that no one else can use whatever invention is covered by the patent, even if they come up with it themselves.

Patents on software mean that there are classes of mathematics that can neither be studied nor used without the blessing of the patent holder. Since the monopoly is provided by the government, doing so would be illegal.

---

### Post by frunns on 2009-07-29
Ok, thanks for a clear explanation on how you meant.

---


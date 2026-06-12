---
title: "UT2004 and Steam games?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-14
Can these run with a basic install, or would I need WINE to run them? Basically, my Windows install is *only* there for iTunes and a few games. If I can switch to songbird for Music/media and have my games running in Ubuntu, I will literally have no need for Windows at all (A dream come true. :p)

So - how can I run my games in Ubuntu?

---

### Post by LowSky on 2009-04-14
you will need Wine to access steam. I cant guarantee the games will work, some will, some wont, its the facts of life using Linux

---

### Post by Noise... on 2009-04-14
> **LowSky said:**
> you will need Wine to access steam. I cant guarantee the games will work, some will, some wont, its the facts of life using Linux

Where can I get Wine?

---

### Post by barisurum on 2009-04-14
You may download it via synaptic package manager. Find package wine and install. Or write in a terminal:

[COLOR="Red"]sudo apt-get install wine[/COLOR]

---

### Post by darthmob on 2009-04-14
keep windows for games! my experience is that you have to spend a lot of time (that means hours of searching and testing) to get one game to run. and that does not mean it will run properly.

a dualboot with windows is the simplest solution to play windows games! even more if you already have it installed.

---

### Post by deepwave on 2009-04-14
Please note there are Loki installers to get UT2004 running natively under Linux.  I highly recommend those installers.

---

### Post by Noise... on 2009-04-14
> **darthmob said:**
> keep windows for games! my experience is that you have to spend a lot of time (that means hours of searching and testing) to get one game to run. and that does not mean it will run properly.

a dualboot with windows is the simplest solution to play windows games! even more if you already have it installed.

I don't have many games. Basically just UT2004, a few Steam games (HL, HL2, Garry's Mod), TESIII: Morrowind, and TESIV: Oblivion.

Would it be worth it to work things out to get those running in Ubuntu? Basically, UT2004 already works, Steam is supposed to work fairly well in Wine, and Morrowind and Oblivion shouldn't be that tough. Oblivion isn't even that important to me - Morrowind was WAY better.

---

### Post by Noise... on 2009-04-14
> **deepwave said:**
> Please note there are Loki installers to get UT2004 running natively under Linux.  I highly recommend those installers.

Where can I get those? Are they in Package Manager?

---

### Post by LowSky on 2009-04-14
[http://www.lmgtfy.com/?q=loki+ut2004](http://www.lmgtfy.com/?q=loki+ut2004)

---

### Post by darthmob on 2009-04-14
> **Noise... said:**
> Would it be worth it to work things out to get those running in Ubuntu?I don't know. go ahead and give it a try!
what I meant to say is that you should not immediately format your windows before trying to get things working with wine. in case it does not work out as you expected it you can still boot up windows and play that way.

you won't get around using a lot of google though! :p

---

### Post by barisurum on 2009-04-14
> I don't have many games. Basically just UT2004, a few Steam games (HL, HL2, Garry's Mod), TESIII: Morrowind, and TESIV: Oblivion.

You can have a good clue about if a game will run or not from wine's homepage: [www.winehq.org](www.winehq.org)

---

### Post by deepwave on 2009-04-14
> **LowSky said:**
> [http://www.lmgtfy.com/?q=loki+ut2004](http://www.lmgtfy.com/?q=loki+ut2004)

Be nice LowSky. :D

[http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

I personally had to own a Midway copy of UT2004, so the installer was a bit different.  In general all Loki installers for various games can be found on [http://www.liflg.org/](http://www.liflg.org/)

As for Steam, you can try Wine but it is not fun.  And in a past life, I tried to get HL2 running under Wine but I got a laggy and buggy HL2.  Maybe things have improved.  I'd also try out the for-pay Cedega or Crossover products.

And for adventurous, you can try to install Windows on a brand new spanking VirtualBox VM.  And run your games through there.  I've even managed to get decent performance from OpenGL games on Windows guests in the past.  The newest version of VirtualBox supposedly can do hardware accelerated Direct3D.

---

### Post by Noise... on 2009-04-14
> **deepwave said:**
> Be nice LowSky. :D

[http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

I personally had to own a Midway copy of UT2004, so the installer was a bit different.  In general all Loki installers for various games can be found on [http://www.liflg.org/](http://www.liflg.org/)

As for Steam, you can try Wine but it is not fun.  And in a past life, I tried to get HL2 running under Wine but I got a laggy and buggy HL2.  Maybe things have improved.  I'd also try out the for-pay Cedega or Crossover products.

And for adventurous, you can try to install Windows on a brand new spanking VirtualBox VM.  And run your games through there.  I've even managed to get decent performance from OpenGL games on Windows guests in the past.  The newest version of VirtualBox supposedly can do hardware accelerated Direct3D.

That sounds like a lot of work for little payoff. :(

I have my games running fine in Windows now, so I guess I'll just strip down the Windows partition to the bare minimum and leave it for games. I've spent the past two hours messing around with trying to uninstall a small handful of programs I won't use anymore thanks to Ubuntu Studio's programs. It's quite a bit of shellshock to go from Ubuntu where everything works flawlessly back to Vista where...well...nothing works flawlessly. :p

Oh well. I guess I can't completely ditch Vista just yet. 

Any chance of Adobe Photoshop CS4 working in Wine? The site says CS3 works fine - should the same work for CS4?

---

### Post by deepwave on 2009-04-14
> **Noise... said:**
> That sounds like a lot of work for little payoff. :(

... 

Any chance of Adobe Photoshop CS4 working in Wine? The site says CS3 works fine - should the same work for CS4?

Such is life.  Technology isn't perfect and involves a lot more work than it ought to. :(

The general rule for Wine is: install wine and try to run said app under Wine.  If it works great!  If not see if there are any tips to fix things on winedb or Frank's Corner.  If not, well then you are out of luck.

And to make things more fun, with every new version of Wine... well lets just say: I hope more of your apps works in the newer version than the older one.  Running with Wine is really hit and miss. :(

Consider learning the finer points of Gimp or Krita rather than fighting to get Photoshop to work. :)

---

### Post by starcannon on 2009-04-14
I have UT2k4 Editors Choice Edition on DVD, it came with a linux installer, works great, patches work fine after install.

I don't use steam, but have seen some success reported when run under Cedega, so Wine should work fine as well.

GL and have fun

---


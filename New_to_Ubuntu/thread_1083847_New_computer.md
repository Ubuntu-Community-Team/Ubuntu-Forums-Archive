---
title: "New computer"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by XanderPansy on 2009-03-01
So, I'm looking to buy a computer soon, because the school I am going to requires me to have one for engineering... So, I work at Best Buy part time and I have had my eye on a few of the models that have blown through the store, and i think the one that I like (price being a large factor in that I have no money) is the Asus "X83Vb-X2"

Now, the reason that i like this one is because I am a huge gamer be heart, so I would like it to have the video card that is capable of playing some of the new games like Star Craft 2, WoW, and Crysis in low res. Now I know that this computer is not going to be the *best* for these games, but I am content with function.

Now on to the real question: Can i get Ubuntu on this effectively? My brother has said that there could be a problem with the wireless card that is in it, and I was wondering if there was any possible way to get around that?

In any effect, I would really like to get this computer because it is at a competitive price point for me, and it has a graphics card that I can live with. But, if there is some other model that has a graphics card that is going to be able to get the gaming done, and isn't crappy, I could live with it.

By the way, I am not a programmer or anything, so the terms and such will most likely blow right over my head. Please talk to me as if I know nothing. (because I most likely do know nothing)

---

### Post by joey-elijah on 2009-03-01
Wireless shouldn't be a major bug bear - but perhaps find out the model/make of the card inside the 'puter you're looking at getting and ask on here or check in the hardware lists.

It'll either work out of the box or you can use the windows driver for it using ndiswrapper. I currently use the Windows XP x64 driver for my wifi dongle this way in Ubuntu. It works fine.

---

### Post by DownTown22 on 2009-03-01
Well, I always recommend pretty much anything Asus makes.  I have an Asus laptop (M51Sn) and I couldn't be happier with it.

Do you know exactly which wireless chip is in it?
If it's Intel's 4965, it's the same that's in my laptop, and I've had zero problems with it.
The only problem I had when installing Ubuntu on mine, was that I had to boot into safe graphics mode first, did the install, then after that everything was peachy.

---

### Post by pparks1 on 2009-03-01
As far as wireless goes, that's always a touchy area with Linux and laptops.  However, I think this model has an Intel wireless card and I believe that those tend to work quite well under Linux.    Worst case scenario, you could always get a wireless usb adapter down the road that has known support.  They are pretty cheap.

The laptop does have an Nvidia card which have always been a better choice as far as I am concerned with Linux.

---

### Post by my window broke on 2009-03-01
I'm trying to find out this things wifi-card, but nobody is really helping. I did see that this laptop comes with 64-bit OS, make sure the games you want come in 64-bit support, otherwise you might run into some issues.

---

### Post by thtrgremlin on 2009-03-01
Great, easy way to check what works / will work flawlessly.

Grab an ubuntu Live CD ant boot the computer with it. Best buy has most its computers on display working, so this is easy, but you need internet. If you can even scan for wireless networks, you are likely good there. check the Restricted Drivers under System -> Administration -> Hardware to see if there is anything it "needs" in that respect. From System -> Preferences -> Appearence -> Visual Effects enable Extra Efects. If that doesn't fail, then you know you have working 3D. Nexd, open up Firefox and go to Youtube.com. Follow the instructions to install Flash Player. If video plays and you get sound, then you are absolutly golden. Of any and all problems you might run into, you would run into them trying to do all those things.

I, personally, would not worry about any compatability issues if all those tests were passed.

As far as playing windows games, checkout [winehq.org]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true") to see how to get those games running.

[Crysis - Rated Silver (fails with Ati cards, need nvidia 8XXX+ minimum to get ANYTHING even at lowest settings)]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880")
[World of Warcraft - Gold / Platnium (plays flawlessly for me)]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154")
Starcraft: Broodwar - Rated Gold (appears to require some tweaking)

Good luck. Let me know if you have any further questions, or need more detail for those tests.

---

### Post by XanderPansy on 2009-03-01
OK thanks guys, glad to hear that the support on the OS i want to use is good.

Yeah the Asus I'm looking at has some intel wireless chip, so if those are good, i guess im set... 
also, it has a nvidia 9300 w/ 512MB dedicated (should be good enough)

That is just what i know off the top of my head, I'll get a better look at what it is running next time I'm in to work... plus i may have to get somthing different, because I'm having trouble coming up with the cash to get the thing... best buy pays good, but not good enough...

---

### Post by linux_tech on 2009-03-01
Before purchasing you may also want to check a hcl to verify the hardware
[http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php)
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by remembermyname on 2009-03-11
i just bought an asus x83vb-x2 and loaded ubuntu 8.10 onto it. most everything except cam worked out of box. but as soon as i updated the kernel to 2.6.27-11-generic, i lost all sound and wireless :(

---

### Post by remembermyname on 2009-03-11
huh... nevermind. i went to this thread:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

to update the alsa drivers and got the sound back. and the wireless as well? :)

---


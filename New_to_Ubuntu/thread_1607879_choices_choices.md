---
title: "choices choices"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by minimad127 on 2010-10-28
ok i know this could cause a whole host of conflicting information however probably wont make me any more ocnfused than i am at the moment
 
so i am currently running Ubuntu 9.10 on a dell latitude X300 ultra portable laptop with 1.2ghz CPU, 640mb RAM, 40GB HDD and the dreaded intel i855 graphics chip.
 
now although i am generally happy with the system, i have got the upgrade/change itch. i only use the system for the absolute basics of browsing/youtube/facebook games and IM, stepdaughter only uses MSN so am currently using aMSN because it has the same 'feel' as windows MSN
 
now i am leaning towards Lubuntu 10.10 and have had a play with the liveCD and everything initally appears to be working as i need it, however one of my mates is pushing Xubuntu due to it being an official version and less likely to get screwed up during a update and my boss keeps going on about Puppy being the quickest he has used
 
so what does everyone think about these options? i am planning on having a play on the liveCD's of Xubuntu and Puppy over the next few days with the plan of doing a full install on Sunday, so i want to get it right first time as being honest i do not have the time or inclination to spend hours pouring over fixes for things so want the fastest and most stable OS i can get

---

### Post by coffeecat on 2010-10-28
You have more than enough RAM and an adequate CPU for running the full version of Ubuntu with the gnome desktop, so don't let anyone tell you otherwise - but I see you are running an earlier gnome Ubuntu anyway. So why not try Ubuntu 10.10? You can't get more "official" than that.

Where you might come adrift is with the i855 graphics. That's an old chipset and newer versions of xserver and the Intel chipset may not play well with it. Why not boot up from the live CD and see if you can get a usable desktop?

**Edit:** just remembered that the Intel driver was going through some sort of transition when 9.10 was being developed and some Intel chipsets were really problematic. Perhaps the i855 will be better in 10.10, perhaps worse. But the proof of the pudding is in the eating - give the 10.10 live CD a whirl.

---

### Post by minimad127 on 2010-10-28
well i have thought about it since i am running Ubuntu but its more the case of wanting more speed as well as stability which is what is making me look beyond just Ubuntu, the problem seems to come from the sometimes conflicting information about 
such that Xubuntu isnt actually 'that much' less resource hungry than the full Ubuntu, Lubuntu still being non offical so prone to instability and Puppy requiring more effort than Ubuntu/Xubuntu/Lubuntu to get set up

---

### Post by minimad127 on 2010-10-28
> **coffeecat said:**
> **Edit:** just remembered that the Intel driver was going through some sort of transition when 9.10 was being developed and some Intel chipsets were really problematic. Perhaps the i855 will be better in 10.10, perhaps worse. But the proof of the pudding is in the eating - give the 10.10 live CD a whirl.
 
well thats why i am still on 9.10, however as i said having tried Lubuntu 10.10 on LiveCD it seems to be working alright, although i didnt do the full update to make sure none of the patches and updates havent killed it since, it was just a quick test to see if it actually showe anything as the 10.04 LiveCD's wouldnt

---

### Post by Daveth on 2010-10-28
I would suggest doing a clean install, as I never entirely trust upgrade paths. You should make yourself a separate /home partition whilst you are at it, then you can swap and change to your heart's delight.

---

### Post by Rubi1200 on 2010-10-28
There are 2 problems with the i855 Intel chipset on 10.10 that you need to be aware of:

1. Compiz (desktop effects will not work at all with it)

2. there are 5-10 second constant CPU spikes

I have been testing this and have not found any workarounds yet.

However, on 10.04 there is a way to deal with this:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Use the workaround from the Glasen PPA.

---

### Post by uRock on 2010-10-28
Please keep in mind that the Puppy Linux site strongly discourages installing the OS. It was designed to be run from the LiveCD. 

As for choosing between Xubuntu and Ubuntu, they are very similar in their use of hardware, because Xubuntu uses a lot of GNOME packages. I use Ubuntu Desktop on my netbook and it uses about 250MB of RAM with Firefox running, so I think you have plenty of RAM.

After reading Rubi1200's post on the Intel GPU, I recommend using 10.04 as it has a work around and you won't have to worry about upgrading for a couple of years.

---

### Post by 4Orbs on 2010-10-28
Kubuntu is like a Rolls Royce.
Ubuntu is like a Cadillac.
Xubuntu is like a Jeep.
Lubuntu is like a motorcycle.

---

### Post by amjjawad on 2010-10-28
I guess your question has been answered already. However, I suggest to have a look at

[http://distrowatch.com/](http://distrowatch.com/)

If this will confuse you even more, then forget it.

You have enough RAM to run Ubuntu as already mentioned. LXDE versions (Lubuntu) require 128MB of RAM as the minimum requirement. XFCE (Xubuntu) versions require a little bit more. GNOME versions require more RAM than LXDE but usually 512MB is enough. KDE versions (Kubuntu) require more if I'm not wrong.

There are more than 300 Linux Distribution and I've been through this confusion not long time ago. Now, I don't need to try anymore :) I'm happy with what I have (I have 9 OS's installed on my PC). Today, I tried 6 distributions and I didn't like any.

Bottom line: It's all up to you. Whatever works well for you, go for it. After all, I might like Ubuntu but you might like Xubuntu. It doesn't mean one of them is better than the other, it's a personal choice :)

You need to check each Distribution's website for more info about the hardware requirements.

:)

---

### Post by sandyd on 2010-10-28
> **minimad127 said:**
> ok i know this could cause a whole host of conflicting information however probably wont make me any more ocnfused than i am at the moment
 
so i am currently running Ubuntu 9.10 on a dell latitude X300 ultra portable laptop with 1.2ghz CPU, 640mb RAM, 40GB HDD and the dreaded intel i855 graphics chip.
 
now although i am generally happy with the system, i have got the upgrade/change itch. i only use the system for the absolute basics of browsing/youtube/facebook games and IM, stepdaughter only uses MSN so am currently using aMSN because it has the same 'feel' as windows MSN
 
now i am leaning towards Lubuntu 10.10 and have had a play with the liveCD and everything initally appears to be working as i need it, however one of my mates is pushing Xubuntu due to it being an official version and less likely to get screwed up during a update and my boss keeps going on about Puppy being the quickest he has used
 
so what does everyone think about these options? i am planning on having a play on the liveCD's of Xubuntu and Puppy over the next few days with the plan of doing a full install on Sunday, so i want to get it right first time as being honest i do not have the time or inclination to spend hours pouring over fixes for things so want the fastest and most stable OS i can get

maybe crunchbang (openbox) would be lighter.

---

### Post by snowpine on 2010-10-28
> **minimad127 said:**
> ok i know this could cause a whole host of conflicting information however probably wont make me any more ocnfused than i am at the moment
 
so i am currently running Ubuntu 9.10 on a dell latitude X300 ultra portable laptop with 1.2ghz CPU, 640mb RAM, 40GB HDD and the dreaded intel i855 graphics chip.
 
now although i am generally happy with the system, i have got the upgrade/change itch. i only use the system for the absolute basics of browsing/youtube/facebook games and IM, stepdaughter only uses MSN so am currently using aMSN because it has the same 'feel' as windows MSN
 
now i am leaning towards Lubuntu 10.10 and have had a play with the liveCD and everything initally appears to be working as i need it, however one of my mates is pushing Xubuntu due to it being an official version and less likely to get screwed up during a update and my boss keeps going on about Puppy being the quickest he has used
 
so what does everyone think about these options? i am planning on having a play on the liveCD's of Xubuntu and Puppy over the next few days with the plan of doing a full install on Sunday, so i want to get it right first time as being honest i do not have the time or inclination to spend hours pouring over fixes for things so want the fastest and most stable OS i can get

Hi Minimad, please understand that all of the Buntu family are the same "core" system (kernel, xorg, intel video drivers, etc) differing mainly in the "desktop environment" (Gnome for Ubuntu, Xfce for Xubuntu, LXDE for Lubuntu, etc). If your Intel i855 is supported by one of the variants, then it should be equally well supported by all of them.

You can experiment with different desktop environments in your existing Ubuntu install. For example if you want to try LXDE, just 'sudo apt-get install lxde' (or use the Software Center) then log out and from the login screen choose Sessions, LXDE. You can even have multiple desktop environments installed, and choose which one you want depending on how you're feeling that day!

That being said, there may be differences in performance between different 'Buntu *releases* (9.10, 10.04, 10.10) as drivers will be 6 months newer with each progressive release. This can be a good thing or bad thing, depending.... new software often fixes old bugs, but it can introduce new bugs.

ps You mention a desire for "the fastest and most stable OS" you can get. Ubuntu 10.04 is the Long Term Support release. This means it will be supported through April 2013 with an emphasis on stability. For pure speed, you might have to look outside the 'Buntu family (but you'd give up Ubuntu's user-friendliness).

---

### Post by kurok on 2010-10-28
puppy Linux (turbo derivative) is fast as heck on my old viao 233mhz processor 128 mb ram 2 gb hd. Full install just like buntu.
There is a version called Lucid 5.1.1 that is said to use the lucid repoes. Its only around 100mb to dl and can run as a live cd id suggest you give it a try.
 My only problem is that it runs in root, and there are said to be problems with intel chips. 
 Is it for you? IDK but it cant hurt to run it as a live cd and try out.

---

### Post by minimad127 on 2010-10-29
thanks everyone for your input, i decided i would do a full install of Lubuntu last night (and pee of the Mrs by getting lost in the world of computers again) and i have found it great very fast on boot and opening windows etc - other than Flash on youtube which juddered every now and then and couldnt even consider going full screen, i am hoping it is just down to the CPU spikes in 10.10 mentioned above.
 
might have a go with one of the 10.04 versions over the weekend with the work around to see if i can get things better otherwise i guess i will have to move back to 9.10 and hope that 11.04 can fix the intel i855 problems without a work around

---

### Post by snowpine on 2010-10-29
> **minimad127 said:**
> i have found it great very fast on boot and opening windows etc - other than Flash on youtube which juddered every now and then and couldnt even consider going full screen, i am hoping it is just down to the CPU spikes in 10.10 mentioned above.

Flash performance is determined, not by Ubuntu, but by the proprietary (closed-source) Adobe Flash plugin. Take a look at the [Flash System Requirements]("http://www.adobe.com/products/flashplayer/systemreqs/"); for 480p playback in Linux they recommend the following:

> Intel Pentium 4 2.33GHz, AMD Athlon 64 2800+ processor (or faster)

512MB of RAM

64MB of graphics memory

I would recommend upgrading your graphics card and/or processor if Adobe Flash playback is an important part of your computing experience.

---

### Post by minimad127 on 2010-10-29
well this is the strange thing as in Ubuntu 9.10 flash on you tube was generally fine or at least i didnt have the random stops (every 15-30 seconds) that i am having at the moment hence why i think i will probably have to try one of the 10.04 versions with the work around and hope that works otherwise its going to be a case of going back to 9.10 for a little while and just hope 11.04 is better

---

### Post by ironic.demise on 2010-10-29
Why not install Ubuntu 10.04.
Use the workaround for the graphics.
then [code] sudo apt-get install LXDE XFCE KDE.
Then choose on startup, Or if you want to try and entire new distro, try LinuxMINT, it's apparantly another 'light' version.

---

### Post by snowpine on 2010-10-29
> **minimad127 said:**
> well this is the strange thing as in Ubuntu 9.10 flash on you tube was generally fine or at least i didnt have the random stops (every 15-30 seconds) that i am having at the moment hence why i think i will probably have to try one of the 10.04 versions with the work around and hope that works otherwise its going to be a case of going back to 9.10 for a little while and just hope 11.04 is better

I believe this is because 9.10 used an older version of the Flash plugin, which may have had lower system requirements (as well as some glaring security flaws).

The Flash plugin is closed-source software. There is nothing the Ubuntu developers can do to "make it better for 11.04." We are basically at Adobe's mercy. :(

---

### Post by Omnomnom on 2010-10-29
Linux mint is based off ubuntu, it's pretty much a linux made for people who are beginners to computers as a whole.

---

### Post by minimad127 on 2010-11-03
hey guys, just a quick update, after having tried to boot up with both Xubuntu 10.04 and ubuntu 10.04.1 last night finding that i couldnt actually get into either (blank screen left for 5 mins with nothing happening, disk drive didnt spin up) i decided to start playing with my Lubuntu install
 
so having followed this [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus) and then done the upstream patch for the i855 in the link it is now running without any CPU spikes which means i can now listen and watch youtube videos without it stopping, ok so i cant get full screen but i havent really managed to get (acceptable) full screen flash on it since i moved to Linux so no biggy there
 
cheers for all the help (especially pointing me in the direction of the CPU spikes)

---


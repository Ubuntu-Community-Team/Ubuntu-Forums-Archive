---
title: "My Ubuntu Journey, and I Must Say I'm Impressed!"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by DracoJesi on 2009-04-07
I do have Q's skip the story if you want lol...

The journey began on my Sony Vaio laptop, running Windows Vista. For some reason, completely beyond my comprehension, yet another Windows update was in progress, only this time, it corrupted windows. I looked the damage, every single file in the /system32 folder had been corrupted. Being quite disgusted at how an official windows update would render this system useless. I went to the system restore utility, which had somehow been disabled, with no restore points... I did what I could but realized the damage so severe, especially since various repair functions just didn't do it, they were to far gone, I'd have to replace them, and since I didn't  have the specific files, I'd have to use the repair feature on the disc....

I had done repairs via the Windows disk before(the sad thing is, despite all my windows hacking/modding over the years, only once was it my fault), but this time was different, the repair feature was built into the laptop, I had a feeling that windows wouldn't boot in normal mode, but come to find out, the repair utility was built into safemode for some ill-designed reason... and yep you guessed it, safemode didn't boot..

so there I was, my laptop a paperweight, and I knew it would continue to be as long as I didn't have an install disk, and I wasn't about to go pay 100-$150 for a windows disk, especially when they should have given me one to begin with... I then glanced over at my mandrake 7.2 install disk, thinking, I could boot from that, but I still wasn't sure how I'd repair the damage without the needed files, and even if I did fix it, if this was done my Microsoft itself, well that didn't leave much hope for the future, how many times would I have to do this? and how long until it was more severe, and I lost everything? or worse, somehow corrupting my MBR and leaving my actual HD corrupted... unlikely yes but so is a company corrupting it's own software...

I thought about making the conversion, I had used Mandrake 7.2 before, I remember it's violet-lilac like colors (which was sweet because my favorite color is purple, well and black, could have been darker though...), it's incredible speed (well compared to XP and Vista) and always cool ability of multiple desktops (it had 6 right?). I would have made the conversion to mandrake then if I wasn't worried about software and game compatibility.... and if it wasn't for an OEM restore disk for my desktop (making it very anal about sharing), I would have done a dual-boot long ago... 

so I looked up my options, I wanted to see if there was anyway to run my windows programs (especially my Star Trek Games), and found references of Wine, so I thought to myself, I'll try this...and if it works on my laptop, I can see going Linux completely..., I also started looking at various flavors of Linux (well not to long and I did look at knoppix), realizing that by now, Mandrake 7.2 must be pretty old... I then heard Ubuntu(I had seen the name mentioned before but never paid much attention), mentioned as not only easy for the beginner but encompassing many features for the more advanced user.. so I looked it up, and looked for videos on youtube, and after seeing how uniform the interface is, with virtually all programs matching the applied theme, and the grace and speed of the interface with no lag despite the many programs up on all the desktops, I was amazed, then I saw the 3d cube and I was sold! :lolflag:

I installed fired up Ubuntu not with the dread of the work set before me, but with vast excitement, like I was trying out a piece of software/hardware I had been waiting to arrive in the mail for months, yet I had only research the program a day earlier...

I couldn't believe how fast it was running, on a cd no less!, I was a little disappointed that I didn't have the cube or those other two desktops, but that wasn't a huge disappointment, realizing that I just had to set up Beryl, and besides, I was working with speed and agility that would make windows curse... and despite all the apps I opened to try out, it didn't lag and I was only using up 400mb of memory, only 40% of my total 1GB, and many times it was at only 30%, did I mention this was all from the cd? lol

the only problem I had (and have had) was the built in wireless, which I figured was just the driver, so with an ethernet cable and a Google search, I had wireless access, I had to install it via the terminal, but I managed lol...

I did have trouble accessing the HD via the cd-boot, even trying to mount manually, but I don't think it was Ubuntu, it was probably either the HD or ignorance on m part.. it did try to mount to something, giving me a "is not a brick device" or whatever error

so I decided to install on the hd, I lost all my stuff but I figured I probably would anyway as by this time I had decided to take the leap... and well, the rest as they say, is history, it's been about a week and I'm staying with Ubuntu :)

---------------------------------------------

now as for the questions, 

I've noticed that not only are there obviously updated versions 1.0, 2.0 ect. of Ubuntu but different flavors like Kubuntu what are the differences, I didn't see a .iso for each one, I just installed the latest Ubuntu iso, so how do you end up with a certain one? does it determine which one to use on install?

luckily I use Firefox and Thunderbird so thats not a big change but I use Dreamweaver for my web design, I downloaded Kompozer, but other than the cool icon, it's lacking, there no auto-complete or color chooser for the hex.... among other more important things, I've also heard a distribution of Kompozer, for some reason the numnber of reports about Kompozer breaking code when opening a file and various problems from the plugins, also, on my installation of Kompozer, the program closes/crashes when I open the insert and (I the other one is the tools) menu.... I've heard god things about BlueFish, anyone here use it or know of a good alternative that hopefully is just as good if not better than Dreamweaver, if I can't get it to work in Wine. I here BlueFish isn't WYSISWYG, but thats not a problem for me, I usually work in code view anyway...

Gnome vs KDE, it's my understanding that theres not much difference in functionality, that the main difference is the coding languages and that gnome isn't as limited do to it's coding and licensing correct?

gtk+ themes, the themes like most things in gnome are done in gtk+ right?
I'm using a theme, a darker one that came with my install, but in some programs, some of the text colors are hard to see, not often but sometimes... how do I edit the theme file and where are they?


Xchat, I clicked transparency in xchat and it crashed, it wont startup, it tries but doesn't make it, reinstalling it doesn't help, I read that reinstalling doesn't change the configuration settings file and that I need to fix or delete that, but I don't know where my programs are, where is the Programs folder/Equivalent in Ubuntu?

I've heard of some people having trouble with installing Beryl, can anyone recommend a good install guide? maybe one for Wine as well?

Sorry for all the questions and thanks in advance :)

---

### Post by billgoldberg on 2009-04-07
**I've noticed that not only are there obviously updated versions 1.0, 2.0 ect. of Ubuntu but different flavors like Kubuntu what are the differences, I didn't see a .iso for each one, I just installed the latest Ubuntu iso, so how do you end up with a certain one? does it determine which one to use on install?**

Kubuntu, Xubuntu, Fluxbuntu ... use differnt Desktop Enviroments or Window Managers

Ubuntu uses [Gnome]("http://gnome.org"), Kubuntu uses [KDE]("http://kde.org"), Xubuntu used [XFCE]("http://xfce.org"), Fluxbuntu uses [Fluxbox]("http://fluxbox.org"), ...

You can transform Ubuntu to Kubuntu, ... using Synaptic or a simple commend (sudo apt-get install kubuntu-desktop) and then in the login window you go to session and switch to KDE.


**luckily I use Firefox and Thunderbird so thats not a big change but I use Dreamweaver for my web design, I downloaded Kompozer, but other than the cool icon, it's lacking, there no auto-complete or color chooser for the hex.... among other more important things, I've also heard a distribution of Kompozer, for some reason the numnber of reports about Kompozer breaking code when opening a file and various problems from the plugins, also, on my installation of Kompozer, the program closes/crashes when I open the insert and (I the other one is the tools) menu.... I've heard god things about BlueFish, anyone here use it or know of a good alternative that hopefully is just as good if not better than Dreamweaver, if I can't get it to work in Wine. I here BlueFish isn't WYSISWYG, but thats not a problem for me, I usually work in code view anyway...**

Bluefish is great. Give it a shot. 

**Gnome vs KDE, it's my understanding that theres not much difference in functionality, that the main difference is the coding languages and that gnome isn't as limited do to it's coding and licensing correct?**

Gnome and Kde both are under the gpl, just like the kernel.

The difference between Gnome and Kde is pretty big, try it out to see for yourself.

[B]gtk+ themes, the themes like most things in gnome are done in gtk+ right?
I'm using a theme, a darker one that came with my install, but in some programs, some of the text colors are hard to see, not often but sometimes... how do I edit the theme file and where are they?[/B]

The themes are in /home/username/.themes

Google you away for guides on changing themes.

Either way, most people use different themes. See the link in my signature called "customizing Ubuntu" for more info.

This thread shows some of the Ubuntu users setups:
[http://ubuntuforums.org/showthread.php?t=1112416](http://ubuntuforums.org/showthread.php?t=1112416)
[B]
Xchat, I clicked transparency in xchat and it crashed, it wont startup, it tries but doesn't make it, reinstalling it doesn't help, I read that reinstalling doesn't change the configuration settings file and that I need to fix or delete that, but I don't know where my programs are, where is the Programs folder/Equivalent in Ubuntu?
[/B]

In a terminal, run

```
sudo apt-get autoremove --purge xchat
```

The config files should be in /home/username/.

But they will be hidded (putting a "." in front of it), press ctrl+h to view it.

Either way, the --purge tag should remove the config files.


**I've heard of some people having trouble with installing Beryl, can anyone recommend a good install guide? maybe one for Wine as well?**

Beryl is outdated and no longer used. The new project is called Compiz Fusion and it's installed by default in Ubuntu.

Well the base of it is, not the manager.

The link in my signature called called "customizing Ubuntu" has all the info on Compiz Fusion you'll need, as does it got instruction on setting up the cube and some other effects.

---

### Post by Dynaflow on 2009-04-07
I'll grab a couple questions.

The differences between Gnome and KDE are mostly their looks (from the user's perspective) and their philosophies (from their devs' perspective).  See [http://en.wikipedia.org/wiki/Comparison_of_KDE_and_GNOME](http://en.wikipedia.org/wiki/Comparison_of_KDE_and_GNOME).  Kubuntu, Ubuntu, Xubuntu, etc., are pretty much the same under the hood.

CS3 Dreamweaver is working well under Wine now, I've heard.  See [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694).

---

### Post by DracoJesi on 2009-04-08
> **billgoldberg said:**
> **I've noticed that not only are there obviously updated versions 1.0, 2.0 ect. of Ubuntu but different flavors like Kubuntu what are the differences, I didn't see a .iso for each one, I just installed the latest Ubuntu iso, so how do you end up with a certain one? does it determine which one to use on install?**

Kubuntu, Xubuntu, Fluxbuntu ... use differnt Desktop Enviroments or Window Managers

Ubuntu uses [Gnome]("http://gnome.org"), Kubuntu uses [KDE]("http://kde.org"), Xubuntu used [XFCE]("http://xfce.org"), Fluxbuntu uses [Fluxbox]("http://fluxbox.org"), ...

You can transform Ubuntu to Kubuntu, ... using Synaptic or a simple commend (sudo apt-get install kubuntu-desktop) and then in the login window you go to session and switch to KDE.

wait, are you telling me i can simply choose which one I want each time I log in, therefore not having to commit to either one? thats really neat... no having choose one for the other :)

> 
**luckily I use Firefox and Thunderbird so thats not a big change but I use Dreamweaver for my web design, I downloaded Kompozer, but other than the cool icon, it's lacking, there no auto-complete or color chooser for the hex.... among other more important things, I've also heard a distribution of Kompozer, for some reason the numnber of reports about Kompozer breaking code when opening a file and various problems from the plugins, also, on my installation of Kompozer, the program closes/crashes when I open the insert and (I the other one is the tools) menu.... I've heard god things about BlueFish, anyone here use it or know of a good alternative that hopefully is just as good if not better than Dreamweaver, if I can't get it to work in Wine. I here BlueFish isn't WYSISWYG, but thats not a problem for me, I usually work in code view anyway...**

Bluefish is great. Give it a shot. 

ok :), 

> 

**Gnome vs KDE, it's my understanding that theres not much difference in functionality, that the main difference is the coding languages and that gnome isn't as limited do to it's coding and licensing correct?**

Gnome and Kde both are under the gpl, just like the kernel.

The difference between Gnome and Kde is pretty big, try it out to see for yourself.



alright I will, as soon as I get gnome all configured the way I want... thanks for clearing that up 

> 
[B]gtk+ themes, the themes like most things in gnome are done in gtk+ right?
I'm using a theme, a darker one that came with my install, but in some programs, some of the text colors are hard to see, not often but sometimes... how do I edit the theme file and where are they?[/B]

The themes are in /home/username/.themes

Google you away for guides on changing themes.

Either way, most people use different themes. See the link in my signature called "customizing Ubuntu" for more info.

This thread shows some of the Ubuntu users setups:
[http://ubuntuforums.org/showthread.php?t=1112416](http://ubuntuforums.org/showthread.php?t=1112416)
[B]


thanks for the links, I've noticed some themes don't allow the human desktop "wavy-ness" feature, are there other themes hat are compliant with the human desktop model other than the ones included with Ubuntu, or am I better off designing my own from the default theme?
 
> 
Xchat, I clicked transparency in xchat and it crashed, it wont startup, it tries but doesn't make it, reinstalling it doesn't help, I read that reinstalling doesn't change the configuration settings file and that I need to fix or delete that, but I don't know where my programs are, where is the Programs folder/Equivalent in Ubuntu?
[/B]

In a terminal, run

```
sudo apt-get autoremove --purge xchat
```

The config files should be in /home/username/.

But they will be hidded (putting a "." in front of it), press ctrl+h to view it.

Either way, the --purge tag should remove the config files.


ok thanks again, you think perhaps the transparency issue is driver based? I think I need an updated one, I forget what graphics chipset I have though, it's a via chip, but I'm not sure which, which reminds me, what kind of diagnostics are there for Linux for detecting that, and what about defragging?


> 

**I've heard of some people having trouble with installing Beryl, can anyone recommend a good install guide? maybe one for Wine as well?**

Beryl is outdated and no longer used. The new project is called Compiz Fusion and it's installed by default in Ubuntu.

Well the base of it is, not the manager.

The link in my signature called called "customizing Ubuntu" has all the info on Compiz Fusion you'll need, as does it got instruction on setting up the cube and some other effects.

thanks, I got all the plugins working but when I have compiz set up, the minimize,maximize and exit buttons disappear, and the windows become stuck and wont move... I'm hoping a driver update will fix it, if i cand just find out where to get the right graphics driver,  

> **Dynaflow said:**
> I'll grab a couple questions.

The differences between Gnome and KDE are mostly their looks (from the user's perspective) and their philosophies (from their devs' perspective).  See [http://en.wikipedia.org/wiki/Comparison_of_KDE_and_GNOME](http://en.wikipedia.org/wiki/Comparison_of_KDE_and_GNOME).  Kubuntu, Ubuntu, Xubuntu, etc., are pretty much the same under the hood.

CS3 Dreamweaver is working well under Wine now, I've heard.  See [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694).

thanks for the info, I tried to get Dreamweaver 8 to work, but I got a error- reinstall message, although I tried running it over the network so that might have something to do with it...

and yeah, I've been looking at the install packages and it seems to me, that one really doesn't need to worry which flavor of Ubuntu they get (as far as Ubuntu vs Ubuntu Studio vs Kubuntu vs Ubuntu Server is concerned) because they can just install all the components anyway?

and dang it, another bird just flew into my window, they really aren't that bright...

---

### Post by LowSky on 2009-04-08
> **DracoJesi said:**
> 
thanks, I got all the plugins working but when I have compiz set up, the minimize,maximize and exit buttons disappear, and the windows become stuck and wont move... I'm hoping a driver update will fix it, if i cand just find out where to get the right graphics driver,  




 Press F11 when this error happens, it should fix it temporarily.
I assume you mean while using Firefox/Thunderbird, its a known issue and easily fixed. Use CCSM (compiz's manager), go to the general tab ( I think, sorry using Windows at work) find the "legacy option" and un-tick or tick  it, just do the opposite of what is in the box, like I said I'm using Windows and cant for the life of me remember

---

### Post by Jakey_TheSnake on 2009-04-08
Dreamweaver now runs under WINE: [http://appdb.winehq.org/appview.php?appId=183](http://appdb.winehq.org/appview.php?appId=183)

```
sudo apt-get install wine
``` 

Then install how you would anyway, 

Default system themes are in /usr/share/themes/, only installed themes are in ~/.themes/

You can install Beryl Emerald if you want, 

```
sudo apt-get install emerald
``` 

But if you want to use an emerald theme you'll have to add "emerald --replace" to your System > Preferences > Sessions.

---


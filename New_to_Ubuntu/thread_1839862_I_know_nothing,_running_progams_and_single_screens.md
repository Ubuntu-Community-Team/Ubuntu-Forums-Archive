---
title: "I know nothing, running progams and single screens!"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by mokabistro on 2011-09-06
Hi there! I'm pretty new to the whole ubuntu-scene. 
I'm finding it more and more appealing, I love the feeling that** I'm** actually doing something!

But, of course I'm running in to some problems.I did get my wireless working and it felt like a real accomplishment. But now I'm having other problems. (I'm running Kubuntu 11.04)

Videos in general lag like hell, on youtube and from the my windows-partitions as well. I installed VLC, as described on their website. It lagged as much as with dragon(?)-player. 

My computer _do_ suck. It's an Fujitsu Siemens Amilo Li1718, it has a 2.0 GHz CPU and 128 MB ati-graphics card (Xpress 200M). I'm not expecting wonders, just not crap.

I'm also experiencing problems getting my screen working the way I want it to. I want the one on the laptop to be switched off and only my BenQ dispalying stuff. But if it doesn't freeze, it keeps flickering all the time, it's really annoying.
  I tried having the BenQ as primary screen, but as a copy of the original, while the original was turned off. It looked as if it was going to work, but then nothing happened.

Last but not least I want to know if there's a way to run windows-installed software in kubuntu? Is Wine the answer? if so, would it work if the program is already installed?

Thanks, (and sorry if I'm being really stupid here),
Jacob

---

### Post by blade4 on 2011-09-06
Hi Jacob . About your problems - I can relate to several of them cuz my laptop sucks too ( 1.8 Mhz processor with intel gfx ) . But I've tweaked around with ubuntu long enough to make it comparable to XP in performance , so I think I can help yours do the same . Let's tackle your troubles : 

1) About the vidoe lag - flash player is quite heavy on resources and so is VLC on linux . For the flash player try to tweak your firefox settings - there are several guides on the net for this . As for the video player - I recommend smplayer . Also , try updating your graphics drivers from the ati site - I think they have a section for linux drivers . 

2)I'm not really sure about your monitor problem so its better I not say anything here . 

3) About running windows software of kubuntu - wine is but one solution . There are many other wrappers out there - cedega and playonlinux to name a few . It really depends on what you want to run , or rather how much effort you are willing to put in to make it run . In that respect , I think wine is more configurable . 

About running software that's already installed , it again depends on the software . From my personal experience with wine -some work and some don't . You can't really know unless you try .  

I know the answers seem a little vague . That's because I don't know much about Kubuntu . I'm only answering based on my experience with kde desktop on lucid . But the tweaks I mentioned should work . 

I'll try to search a bit more about these . 

Till then Ciao !

---

### Post by mokabistro on 2011-09-06
Thanks for the reply! 

It seems playing the files from my kubuntu partition reduces the lag (even in 720p, which I've been having troubles with when running win7!) 

Haven't tried smplayer yet, I fail to install it... 

about tweaks I haven't been able to find anything of use, have you got any examples of what to search for?

It's CS5 I want to run, I read about it on some [URL="http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/"] site 
[/URL], do you think it's possible to use that guide for an installed version of not just PS but also Illustrator and Dreamweaver?

From what I gather the only difference between ubuntu and kubuntu is gnome/KDE... I thought the difference between those two were the layout and interface, etc.. But perhaps there are other differences as well?

I found this site: [http://www2.ati.com/drivers/linux/linux_8.16.20.html](http://www2.ati.com/drivers/linux/linux_8.16.20.html) about ati drivers, and at linux-forums I read something about X.org... I think x.org has something do do with the drivers?

---

### Post by 369uday on 2011-09-06
this is uday and i am new here on this forum.

------------------
uday
[36uday]("http://www.google.com")

---

### Post by migs73 on 2011-09-06
Hi there, I'm not an expert with Kubuntu but a great add-on/plug-in for Firefox is Flash-Aid.
It sort you out with the best available flash plugins, and should help with your youtube issues.
I have an Xpress 200M card on a 1.8Ghz processor and it is watchable, but sometimes a little bit blocky at full screen.

Anyway to get Flash-Aid go here; [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

It is always best to try to run native apps rather than using wine (great as it is most software has some limitations on it), so try this website as well for alternatives to what you used on MS;  [http://www.osalt.com/](http://www.osalt.com/)

Good luck

Mike  :)

---

### Post by snip3r8 on 2011-09-06
Bad video playback is usually due to a CPU that isn't fast enough,in relation to the screen problems,have you installed the appropriate graphics drivers?

---

### Post by snip3r8 on 2011-09-06
> **369uday said:**
> this is uday and i am new here on this forum.

------------------
uday
[36uday]("http://www.google.com")

Hello uday and welcome to the forum,I suggest you maybe start your own thread or visit a thread where you can contribute.

---

### Post by blade4 on 2011-09-07
Taken off the net : 

This will force the flash player to bypass its GPU validity checks, improving performance.

In a terminal type:
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > /tmp/mms.cfg
sudo mv /tmp/mms.cfg /etc/adobe/

Don't expect the hack to be a magical speed boost option but it does help with tearing and choppiness. Hopefully Adobe will one day fix flash in Linux instead of giving us workarounds.

The above was for ubuntu but should work on kubuntu as well . 


About the firefox tweaks - just google "firefox performance tweaks" or something of that sort - making firefox faster will surely help your system . 

As for your query about Xorg - yes it is related to drivers . Xorg is in fact the crux of linux graphics and affects performance too . You can improve performance by tweaking your xorg.conf file ( its usually in /etc/X11 ) . If its not there , there are guides on the net on how to create them specific to your needs , but be warned - the wrong entries could destabilize your system . If you're interested , look here to create the file: 

[http://ubuntuforums.org/showthread.php?t=1437980](http://ubuntuforums.org/showthread.php?t=1437980)


and here for the tweaks : 

[http://www.tuxradar.com/content/modify-xorgconf-better-performance](http://www.tuxradar.com/content/modify-xorgconf-better-performance)

[http://phoronix.com/forums/showthread.php?14253-Tuning-xorg.conf-to-get-the-most-out-of-your-ATI-card-using-any-driver](http://phoronix.com/forums/showthread.php?14253-Tuning-xorg.conf-to-get-the-most-out-of-your-ATI-card-using-any-driver)

Hope these help 

Cheers !

---

### Post by mastablasta on 2011-09-07
> **mokabistro said:**
> >  
It's CS5 I want to run, I read about it on some [URL="http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/"]site 
[/URL], do you think it's possible to use that guide for an installed version of not just PS but also Illustrator and Dreamweaver?
 
Heh why would you want to run CS5 on such a computer? unless you are into some serious design that really require that... Even on windows CS5 might struggle as you would need some good CPU and GPU to use all it's potential.
 
No i suggest you give a look at GIMP for photos (a very good and powerfull photo editor) and Inkscape for vector graphics. There are a few others out there.
 
Instead of Dreamweaver there are a few WYSIWYG editors floating arround. Not that much choice but still some seem descent enough to do the job well (blue fish, Kompozer and there is another one in development i forgot it's name).
 
[QUOTE]
From what I gather the only difference between ubuntu and kubuntu is gnome/KDE... I thought the difference between those two were the layout and interface, etc.. But perhaps there are other differences as well?
 
Yes there are some other smaller differences as well. since the whole philosophy behind desktop is different. GNOME is minimalistic with few GUI option, KDE has plenty options. There are also differences in packages used and native programmes. though most work in both desktop environments, some do not.
 
> 
I found this site: [http://www2.ati.com/drivers/linux/linux_8.16.20.html](http://www2.ati.com/drivers/linux/linux_8.16.20.html) about ati drivers, and at linux-forums I read something about X.org... I think x.org has something do do with the drivers?
 
 
It was already explained a bit about x.org. another interesting site to keep an eye out is x-org edgers PPA which will install latest opensource drivers for ATI cards. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) Sometimes they might mean a difference betwee stuttering video and smooth play. if you decide to use them make sure you read the instructions well.
 
also lay off the special desktop effects to reduce the usage of graphics card for cool yet unnecessary functions.

---


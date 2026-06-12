---
title: "More than absolute beginner.. no GUI"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by drud on 2009-02-05
Hello all, I am quite new to linux and also to forums. I downloaded and installed 'ubuntustudio-8.10-alternate-i386.iso' in my acer travelmate laptop
CPU celeron 1.4 gh
RAM 2nos 256mb and 512 mb.
I have Windows Xp already installed.
The Lan card was also supported during installation.

But after that I am facing a huge problem and it goes like this. When I boot ubuntustudio, i land up at the kernel mode (or text mode?) and no GUI or desktop. I searched lot through the forums and found many are having the same problem. I tried almost everything I could find in the forums.
But, ultimately nothing is working. I am still at the text mode.
So, how can I get the desktop? Some help said to install xserver. I did not that but still no good.
My question is why it did not take the x server from its own installer. Or ubuntustudio does not come up with a desktop!!!
I am finding linux very tough.... I believe its not my cup of tea.
Any help from anyone? While giving advice please remember I am absolutest newbieto linux. I dont even know what is a kernel mode.. 
:(

---

### Post by albinootje on 2009-02-05
> **drud said:**
> When I boot ubuntustudio, i land up at the kernel mode (or text mode?) and no GUI or desktop.

Can you please post the output of the following :
```

sudo lshw -C video

```
specifically the line which starts with "product:".
Then we can see whether your video card is supported, and how this can be made to work.

---

### Post by drud on 2009-02-06
[I]Hi, Thanks for the quick response. 
I did the command and here is the full response:[/I]

*-display:0 UNCLAIMED
**product: 82852/855GM Integrated Graphics Device**
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33 MHz
capabilities: pm bus_make cap_list
configuration: latency=0 
*-display:1 UNCLAIMED
**product: 82852/855GM Integrated Graphics Device**
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 02
width: 32 bits
clock: 33 MHz
capabilities: pm cap_list
configuration: latency=0

So, that is it. I have made bold the product. As you wanted to know that.
Thanks.

---

### Post by kimberlite on 2009-02-06
Hi drud,

Would you please try this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hyper_ch on 2009-02-06
any reason why you used ubuntustudio instead of the default ubuntu isntallation disc?

---

### Post by tnd on 2009-02-06
I use Ubuntu studio and I think I know what you may have done, having made this mistake myself in the past. The text-based installer can be a bit confusing.

When it offered you the different "bundles" to install (sound apps, video apps, etc), did you select "ubuntustudio-desktop"? Not sure if that's the exact name but it's something similar.

You have to press the space bar to select each item you want, then press enter when you're done - if you didn't select the desktop, you will have no desktop environment so will be stuck at a text console.

If this isn't what you did... then I'm not sure, there was a problem with some Nvidia cards and the realtime kernel but I don't think the newest versions use the rt kernel anymore.

> **drud said:**
> 
I am finding linux very tough.... I believe its not my cup of tea.

Obviously I'm biased, but as someone who has had a fair few problems setting Ubuntu up in the past - I'd really say it's worth sticking with it. 
(But as a beginner, it's probably best to keep a dual boot of Windows if possible until you're sure you've got it set up right.)

---

### Post by lakersforce on 2009-02-06
```
gdm start
```

---

### Post by drud on 2009-02-06
Thanks to you guys.. You guys rock.. I have to answer so many question.. Here it goes..

I had tried linux with live cds earlier and also in my virtual PC. I needed some good softwares to work with multimedia, so when I searched the ubuntu, I found that ubuntustudio comes preinstalled with almost everything I need. So, I chose ubuntustudio. I thought it would be easy for me!!! I still hope that, and I mean it!!

I have tried that 'sudo dpkg-reconfigure xserver-xorg', but it says that xserver-xorg is not installed (I don't remember the exact error, but it was something like this).

As tnd said, I believe I have not installed the one with a "must have" thing added at its end. And that is not my fault. I tried to select that but I could not *(as there is no mention how to select each one, as you said by 'space' key)* and probably only the first option is installed. 
But I have selected that in my virtualbox installation, there also the problem is some. But I am going to reinstall again with that thing. And, yes till now my laptop is dual boot. 
But a request to the ubuntu developers kindly put a line on that part how to select them.

Lastly, I am going to try with 'gdm start' right now and let you know what comes up. I don't hope much though, as I think I have messed up while selecting that "must have" thing. Will be back in a moment after trying that.

And, sorry I made this reply so big. And how to put that quote thing? Had i knew that, writing this would be so easier.

Thank you all again.... I am blessed to have so wonderful people here.

---

### Post by drud on 2009-02-06
Is there to no way to install the 'desktop environment' and other software packages from the ubuntu dvd now?

---

### Post by hyper_ch on 2009-02-06
try
```

sudo apt-get install ubuntustudio-desktop

```

---

### Post by tnd on 2009-02-06
Drud - just to clarify, the regular (non-Studio) version of Ubuntu has a different, graphical installer which is easier to use. The Studio installer is not very helpful, though, I agree - like I said, I did the same thing earlier.

In reply to the above post: that depends on his internet connection. If you have any problems with this, maybe a better way would be to add the DVD as a repository? 

```
sudo apt-cdrom add
``` 
then run
```
sudo apt-get install ubuntustudio-desktop
```

Or just reinstall, it'll take a while but it'll overwrite anything else you've tried which might just pop up later and start causing trouble (although I can't see anything that would).

---

### Post by drud on 2009-02-06
Believe it or not.... I am posting this from my ubuntu desktop with my firefox browser. Just one mistake and everything seemed so bleak.... 

Not now.. my ubuntu is up and running.

:D:D:

Sorry, there are no dance icons!!!

Well, now lets talk serious.

I blame the ubuntu developers for this misadventure of mine. They could put just a small tip in the ´Select and install software´ section to use the space key for selecting the option. This would reduce lot of harrassment for properly installing the desktop for idiots like me.

In my virtualbox install also, I made the same mistake in selecting. I brought the red mark to the ´ubuntu desktop (must have)´ but I did not confirm it by ´space´ key and that created the whole mess.

I appeal to the developers of the installer to kindly put this. It is going to take the frustration out of many first time users like me. I believe they could add there:
¨Select by up and down key, use ´space´ to confirm¨
and this would take away all problems.

But I believe this had a bright side too... Because I learnt a lot about the kernel mode because of this from you people and also from other forums. I am actually feeling like a linux geek. ;) 

About installing ubuntu-studio from the ´sudo apt-get install.....´, I tried that too but I was a real idiot to try only ubuntu-desktop, not ubuntustudio-desktop. Probably that could solve my problem..

One last question, it may be out of topic for this forum, how to install the other software packages from the cd. I installed only desktop and 2d&3d packkages.... I´ll search the forums, no doubt.

Thanks to all of guys... You people are really really wonderful.

---

### Post by igknighted on 2009-02-06
Well... any reason you used the "alternate" install CD?  The liveCD is the standard install for a reason... it's really easy.  You can click "ok" to everything and have a working system in no time.  The alternate CD is for those who want to dig a little deeper and do a more customized install.  That's why on the download page, it is buried deep so it is harder to get.

There is also the case of some people needing the alternate CD because of a bug that completely stops the liveCD from loading (rare, but it happens), but in 99% of cases, you should install from the liveCD.

---

### Post by hyper_ch on 2009-02-06
> **drud said:**
> I blame the ubuntu developers for this misadventure of mine. They could put just a small tip in the ´Select and install software´ section to use the space key for selecting the option. This would reduce lot of harrassment for properly installing the desktop for idiots like me.
I tend to say people like you would normally not install ubuntu studio but the actual ubuntu desktop cd and there you can't de-select the gnome environment. The blame does not go to the devs. In the end, linux offers choices and if you don't know what the choice are, then inform yourself.

---

### Post by drud on 2009-02-06
And tnd, thanks a lot. I actually reinstalled the whole ubuntu, messed up things with grub, but managed to repare that. I was just too impatient to wait for more reply to install the desktop. I tried installing the desktop-environment from kernel mode, it failed (well, not exactly failed. The installer wanted to download something above 100 mb from the net, and I did not allow it, &#263;oz I knew it must be in the dvd). My idiocy is to be blamed again... I typed the install package as ¨ubuntu-desktop¨ not ¨ubuntustudio-dektop¨...:wink:
Anyway.. things are fine now.

Thanks again...

---

### Post by drud on 2009-02-06
Please don´t take blaming the developers so seriously, it was not meant that way. I understand there must be some reason for that. But definitely they could just add a little tip in that window because many trying to use linux are like me and sometimes we have only the alternate cd.

I could not find live cd for ubuntustudio, stating that running ubuntustudio as live cd is not going to be productive, so I had to select the alternate cd.

But I loved the alternate installation except the misadventure :;-):

Hey... 
We all learn by mistakes... don´t we?

---

### Post by tnd on 2009-02-06
Glad it's all fixed - granted, they could be more helpful on the install. 

I don't know why they don't just offer a LiveCD for Studio, but hey. As long as it's working!

---

### Post by albinootje on 2009-02-06
> **drud said:**
> 
I blame the ubuntu developers for this misadventure of mine. They could put just a small tip in the ´Select and install software´ section to use the space key for selecting the option. This would reduce lot of harrassment for properly installing the desktop for idiots like me.

Suggestions for Ubuntu developers should be posted here : [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)
And bug-reports should be posted here : [http://launchpad.net](http://launchpad.net)

Why ? Because there's very very little Ubuntu developers reading+writing here on this forum, and something like the "brainstorm" website is easier to follow for them.

---

### Post by igknighted on 2009-02-06
> **tnd said:**
> Glad it's all fixed - granted, they could be more helpful on the install. 

I don't know why they don't just offer a LiveCD for Studio, but hey. As long as it's working!

As I look at the page, I think it is because there is simply too much stuff to put on a CD.  And they want the install to be able to be tailored to the user, as a sound artist may not want the graphical tools, and vice versa.  The Ubuntu liveCD installer simply dumps the whole CD image to disk, and with all the apps UbuntuStudio has on the DVD, that's a ton.

---

### Post by drud on 2009-02-06
Yes. That may be the reason. Even it is mentioned on that part that the desktop must be installed. I made a mistake in thinking that if the red mark is there, that part will be installed. One has to confirm it by the space key. Mentioning it there would be very helpful indeed, otherwise installing ubuntustudio was hassle free.
But what I could not understand is that there are so much forums discussing this issue, but nowhere it is mentioned. Probably, no one thought that something so foolish was actually the reason.

---


---
title: "Ubuntu, old computer, and kids - request advise"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Kal Sho on 2011-06-12
I have an old computer (Celeron processor [32-bit], only 500 megs of RAM) That I'd like to set up for the kids (7, 9, 11, and 13 years old) to use. It'll be used mostly (I assume) by the youngest, who likes to play with Tux (Racing, Paint, Typing, Math). I have a few questions. Please bear with me, since I'm still mostly a n00b. I've only been using Ubuntu for a couple months.

1) How can I make Ubuntu (or another distro that's as easy-to-use) as resource-light as possible, so that it will run smoothly on an old machine?

2) What parental control options are there, and which is the best (if extra software is even needed)? I'm talking not just about restricting installs, but also web filters, time limits, things like that.

3) Is there a way I can see what they're up to from my own machine, and, if so, how do I set it up? I'm thinking something where I can remotely view/control. I'm pretty sure something like this is out there, but I'm not sure what to use.

4) What other kid-friendly games/apps can you recommend?

Thanks for reading this far. Any help is appreciated.

---

### Post by amanchesterman on 2011-06-12
Hi I am new to Ubuntu too. Before I installed it on the machine I am using now I put it on a very old laptop which has only 256 RAM. I installed Xubuntu which is designed for low-spec machines, I believe there is a version called Lubuntu which is similar.

I found that Xubuntu runs well: I can use the old laptop to surf the internet, do wordprocessing etc. But I found that videos are very 'jerky' on it, I can't get smooth action at all. I suspect that isn't the fault of the software, the machine just isn't up to it.

So before you do a lot of work, my advice would be to try Xubuntu or Lubuntu by running them as a live CD, just to make sure that you can get reasonably smooth moving graphics. If you can't, you may find that your kids aren't too enthusiastic about using the machine ...

---

### Post by walt.smith1960 on 2011-06-12
> **amanchesterman said:**
> 
.....................................................
So before you do a lot of work, my advice would be to try Xubuntu or Lubuntu by running them as a live CD, just to make sure that you can get reasonably smooth moving graphics. If you can't, you may find that your kids aren't too enthusiastic about using the machine ...

Flash may be the deal-killer if you need it.  The only liveCD distro I can think of  that may play flash would be Mint and I don't know Mint is all that light.  I have a notebook similar to what I think Kal Sho is talking about running Lubuntu.  It'll do web browsing and office-type stuff okay.  Web videos are much closer to slide shows; Flash is a resource pig and I don't know a way around it.

---

### Post by terrykiwi83 on 2011-06-12
> **Kal Sho said:**
> I have an old computer (Celeron processor [32-bit], only 500 megs of RAM) That I'd like to set up for the kids (7, 9, 11, and 13 years old) to use. It'll be used mostly (I assume) by the youngest, who likes to play with Tux (Racing, Paint, Typing, Math). I have a few questions. Please bear with me, since I'm still mostly a n00b. I've only been using Ubuntu for a couple months.

1) How can I make Ubuntu (or another distro that's as easy-to-use) as resource-light as possible, so that it will run smoothly on an old machine?

2) What parental control options are there, and which is the best (if extra software is even needed)? I'm talking not just about restricting installs, but also web filters, time limits, things like that.

3) Is there a way I can see what they're up to from my own machine, and, if so, how do I set it up? I'm thinking something where I can remotely view/control. I'm pretty sure something like this is out there, but I'm not sure what to use.

4) What other kid-friendly games/apps can you recommend?

Thanks for reading this far. Any help is appreciated.

Hi there,
I to setup an old computer for my kids.

1. I installed Ubuntu 11.04 on an old Semperon (32bit) processor, 512MB RAM, 40GB HDD and although it won't run Unity it runs Gnome classic and actually runs pretty smoothly.

2. Parental control wise am not to sure as I use a squid proxy server here and that does all the filtering for me. I have heard of DansGuardian [http://dansguardian.org/?page=whatisdg](http://dansguardian.org/?page=whatisdg) and Willow [https://wiki.ubuntu.com/ContentInternetFiltering/Willow](https://wiki.ubuntu.com/ContentInternetFiltering/Willow) so give them a whirl

3. I use vncviewer to view my linux desktops, but this pops up with a warning on the other users desktop.

4. There are hundreds of games out there, my kids like Hedgewars (like worms), 4-in-a-row and Pingus.

Hope that helps

---

### Post by pqwoerituytrueiwoq on 2011-06-12
+1 for hedgewars (google playdeb)
you can turn off the notice off
system->preferences->remote desktop or
vino-preferences from the command line
i heard of a app called nanny you may want to use

never had issues with xubuntu and videos being choppy on my 1gb ram p4 @ 2.8ghz

---

### Post by candtalan on 2011-06-12
A light  version is xubuntu or Lubuntu however, as mentioned, flash and other apps are heavy, it may depend on other things too such as the graphics card. I would try Ubuntu anyway, to see how it runs first.

Be sure to set up user account/s for the children (non admin), keep your install (admin level) password to yourself.

control: I have used firefox filter procon-latte which is useful and basic enough for me to understand.... I use it with a password, it may be enough to get started. Other/more controls can I think be put in at the router, I do not know.

Remote viewing usually requires the user to explicitly consent to  being looked at. 

I would seriously consider where the PC is located. If it is in a very public area there will be a different feel to its use rather than in a 'private' bedroom or whatever.


Games:
I use synaptic package manager and look at the games lists on pick out stuff. Some games do need a more powerful PC.
good luck

---

### Post by Kal Sho on 2011-06-12
I installed Ubuntu 11.04 on it when I got some free time tonight. It'll run unity, but I'll probably set it up to run classic. Just a personal preference, really. I installed the nVidia proprietary drivers (I don't actually remember what model nVidia card is in it. I'll have to check some time). I installed the Tux games available in the software center, except Supertuxkart, which I forgot to look for. I'll do that tomorrow.

I'll start looking into your other suggestions after work tomorrow.

Many thanks for the input all. Now it's bed time.

edit: The computer is located in a public area, but there are times when I have to work on the computer in my office. The view/control option is more to lend assistance without walking away from my work all the time than a lack of trust. In any case, I like to keep my options open and be prepared.

---

### Post by fremantle on 2011-06-12
seems to me you need to start from a minimal desktop, with xfce or lxde. then you add the softwares you need and set up everything.

---

### Post by fremantle on 2011-06-12
check it [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

---

### Post by JohnBonne on 2011-06-12
> **walt.smith1960 said:**
> Flash may be the deal-killer if you need it.  The only liveCD distro I can think of  that may play flash would be Mint and I don't know Mint is all that light.  I have a notebook similar to what I think Kal Sho is talking about running Lubuntu.  It'll do web browsing and office-type stuff okay.  Web videos are much closer to slide shows; Flash is a resource pig and I don't know a way around it.

I hear this is the problem withlight versions. I had Ubuntu on an external drive and it ran alright. I have mint installed as an alternative to a heavy system, but it isn't all that heavy nor light. It makes the machine run hot.  am installing xubuntu next.

---

### Post by Paqman on 2011-06-12
> **Kal Sho said:**
> 
1) How can I make Ubuntu (or another distro that's as easy-to-use) as resource-light as possible, so that it will run smoothly on an old machine?

You could try out one of the lighter desktop environments, check out Lubuntu or Xubuntu, and run lightweight apps on it. The other option is to build your own system using the [minimal image]("https://help.ubuntu.com/community/Installation/MinimalCD"). You start with a bare command line system and add only the packages you want. See the link in my sig.

> 
2) What parental control options are there, and which is the best (if extra software is even needed)? I'm talking not just about restricting installs, but also web filters, time limits, things like that.


Check out Gnome Nanny, it's in the repos. It does filtering and time limits. I've looked at Squid/Dansguardian in the past, but it's a not fun to set up.

---

### Post by manzdagratiano on 2011-06-13
The lightest window manager easily available and not too hard to use is Fluxbox (I personally use Blackbox for its elegance, though most may prefer convenience over elegance). It is very low on resources compared to Gnome and also fires up lightning fast. It is certainly faster than xfce, which though fast, cannot beat it.

You should leave Gnome installed, which will allow you to use simple features like gnome-power-manager inside of Fluxbox, etc. Moreover, I recommend using at least 2 GB of swap space on the system, which will ensure you are always comfortable with memory even when playing games. If you push it to 4GB, you can push the games to even more extreme levels!

---

### Post by Perfect Storm on 2011-06-13
You could also try eOS. It's based on ubuntu 10.10 but fast and uses less resources.

---

### Post by mastablasta on 2011-06-13
The computer is capable of running Gnome. well Gnome 2.x at least.
 
XFCE (xubuntu) is a good lighter alternative but still with plenty  applications that were specifically made for it. eOS, LXDE, openbox (which is not even a DE i think) are good alterantives for realyl old mashcine. really really old. and they iwll be limited with applications or will have to run gnome for them. so if system is capable to run XFCE why run weaker DE especially if kids are involved.
 
Aside from GNOME nanny there is also Mint nanny.

---

### Post by Kal Sho on 2011-06-14
Thanks again for all your input. 

I installed x11vnc and set up ssh. Now I can just ssh in and start the vnc server whenever I need to.

Had some problems getting it to work, but eventually I ran a cat-5 to the router instead of connecting wirelessly. For some reason I couldn't connect, or even ping, the machine until I wired it to the router. Probably a setting on the router I'd need to change. In any event, I worked around it.

Next step is setting up one of the nanny options you great folks suggested. After that I'll dig around and find some more games/educational software.

Thanks again.
Sho

edit: I guess  the next step is actually figuring out how to mark this "solved" ;)

edit2: That was easy.

---

### Post by I2k4 on 2011-06-15
I agree with the advice to test out versions on "Live USB" if your old machine will permit booting from a USB socket (my oldest Dell won't.)  You should test with "Persistence" so as to save installations and settings between reboots.

I very much like Lubuntu as a lightweight install.  However, I do not like experimental "Chromium" the very buggy open source browser that comes with it.  If you install plain vanilla Google Chrome, it comes with Flash preinstalled and is about as slick a browser as you'll find for older equipment.  

There is a very rich selection of add on extensions to Chrome, that may include some parental supervision, but I've never looked for it.  (I personally install the privacy enhancer "Click & Clean" because I don't want Google to keep an eternal record of my internet activity.)

By and large, for kids who are not already trained on Windows, I don't think Lubuntu is any harder for them to figure out than any other operating system, and it's much more resource-efficient for older machines than ordinary Ubuntu.  I recommend Lubuntu 10.10, since the new Lubuntu 11.04 (like the new Ubuntu) requires much more powerful hardware without any gain in functionality.

UPDATE:  re comment below, and not to drag this out, I don't say Lubuntu 11.04 doesn't run "okay" but it is simply not slick and snappy like 10.10 - and for life of me I couldn't see anything different in Lubuntu 11.04 other than slowness.  At least with Ubuntu 11.04, you get Unity if you like it, which really is different and might be worth a performance trade off for some.

---

### Post by walt.smith1960 on 2011-06-17
[QUOTE=I2k4;10943525
<snip>
 I recommend Lubuntu 10.10, since the new Lubuntu 11.04 (like the new Ubuntu) requires much more powerful hardware without any gain in functionality.[/QUOTE]

I can't speak to Lubuntu 10.10 but Lubuntu 11.04 works okay on a 9 year old R31 thinkpad with 1 ghz. P3 and 512 MB. RAM.

---


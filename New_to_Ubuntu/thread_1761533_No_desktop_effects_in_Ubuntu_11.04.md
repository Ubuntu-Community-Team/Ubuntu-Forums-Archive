---
title: "No desktop effects in Ubuntu 11.04"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by deshmukh on 2011-05-18
I am planning to switch from KDE to GNOME. I currently use KDE 4.6.2 on Kubuntu 11.04.

In order to try GNOME, I installed 'Gnome' package from the repositories (1:2.30+7ubuntu3).

Installation went well and gave me multiple options at the KDM login screen. When I select Ubuntu Classic, all goes well and I get the GNOME Desktop with two panels, etc.

However, there is no desktop effects tab in System - Pref - Appearance. I have Compiz and CCSM installed and gconf-editor shows compiz as the window manager in /desktop/gnome/applications/window_manager.

So, what do I need to do? I like GNOME otherwise and will be quite frustrating to revert back to KDE simply because of desktop effects.

---

### Post by deshmukh on 2011-05-19
Any help here??

It may seem that so what if the effects are missing. But I find them useful especially when cycling through windows, etc.

Thanks in advance.

---

### Post by vickoxy on 2011-05-19
You should install Ubuntu Tweak. Then from there you activate wobble windows... Then you can manipulate also with other effects in CCSM.
Don´t know why is that, but it works...

---

### Post by StrayEddy on 2011-05-19
Open compiz, take a screenshot and post it here plz

---

### Post by DigitalAlcatraz on 2011-05-19
Visual Effects Are moved in Natty Narwhal. Have you  enabled unity in ccsm? If you haven't, do so, then transition becomes simple and aesthetically pleasing at the same time without taxing your graphics much.:)

---

### Post by wildmanne39 on 2011-05-19
> **DigitalAlcatraz said:**
> Visual Effects Are moved in Natty Narwhal. Have you  enabled unity in ccsm? If you haven't, do so, then transition becomes simple and aesthetically pleasing at the same time without taxing your graphics much.:)

Hi, if he enables unity and tries to get the cube to work it will break his system, there is additional steps that must be taken if you do it in unity, but with classic it works as long as you do not activate the unity plug in.

---

### Post by deshmukh on 2011-05-20
> **vickoxy said:**
> You should install Ubuntu Tweak. Then from there you activate wobble windows... Then you can manipulate also with other effects in CCSM.


vickoxy, thanks for your help. 

I tried that route. No effect still. Appearance tab still does not show. CCSM shows all the required add-ons selected. :( :(

---

### Post by deshmukh on 2011-05-20
> **StrayEddy said:**
> Open compiz, take a screenshot and post it here plz

StrayEddy, thanks for your help. Enclosed is the screenshot of CCSM (assuming thats what you want to see. I tried running compiz for the screenshot - but no window launches on starting compiz)

Let me know if you need something more/ different.

---

### Post by deshmukh on 2011-05-20
> **DigitalAlcatraz said:**
> Visual Effects Are moved in Natty Narwhal. Have you  enabled unity in ccsm?

Thanks for your help. Visual Effects are moved to where in Natty Narwhal??

I have not enabled Unity in CCSM. In fact, I checked, Unity is not even installed. As I mentioned, I installed 'Gnome' package. That does not require Unity.

If I install Unity, will Visual Effects be available even in Ubuntu Classic option?

Also, is not there a way of enabling effects WITHOUT installing Unity?

---

### Post by deshmukh on 2011-05-20
> **wildmanne39 said:**
>  but with classic it works as long as you do not activate the unity plug in.

Thanks! In Classic how does it work?? I do not want to enable Unity plugin :)

---

### Post by wildmanne39 on 2011-05-20
> **deshmukh said:**
> Thanks! In Classic how does it work?? I do not want to enable Unity plugin :)

Hi, you install ccsm and you make sure you have your video card driver enabled it is in additional drivers, then you can go into ccsm and if you want the cube you can type cube in the box and it will bring up the cube for you to check. Go here and red on how to set it up [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695) it is not exact because I think you said you are running natty,so there is no setting to set in the appearence preferences like before. For the most part you can follow those instructions some settings you will have to look for like I did because they are different also in natty.

---

### Post by wildmanne39 on 2011-05-20
> **deshmukh said:**
> Thanks! In Classic how does it work?? I do not want to enable Unity plugin :)

Hi, I forgot also make sure you intsallon the extra plugins and things for compiz.

---

### Post by mastablasta on 2011-05-20
just one mroe thing to mention that you should get used to unity as classic Gnome will get dropped with 11.10. so you might want to start learning unity now since you are moving from KDE anyway.

---

### Post by deshmukh on 2011-05-20
> **wildmanne39 said:**
> Hi, you install ccsm and you make sure you have your video card driver enabled it is in additional drivers, then you can go into ccsm and if you want the cube you can type cube in the box and it will bring up the cube for you to check. Go here and red on how to set it up [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695) it is not exact because I think you said you are running natty,so there is no setting to set in the appearence preferences like before. For the most part you can follow those instructions some settings you will have to look for like I did because they are different also in natty.

Thanks, Wildmanne. CCSM is installed. Video card driver is enabled (fglrx for my AMD. Also, my login manager is still KDM and when in KDE, all effects and compositing works quite well).

I have enabled all the desired effects in CCSM (Scale, etc)

> **wildmanne39 said:**
> it is not exact because I think you said you are running natty,so there is no setting to set in the appearence preferences like before.

Where in Natty is the question I am seeking an answer for :)

---

### Post by deshmukh on 2011-05-20
> **mastablasta said:**
> just one mroe thing to mention that you should get used to unity as classic Gnome will get dropped with 11.10. so you might want to start learning unity now since you are moving from KDE anyway.

Do you mean to say that Gnome 3 will NEVER be part of Ubuntu repositories?? I thought it was just the case of what is the 'default' desktop environment and Gnome will always be available as an option like XFCE, E17, etc

---

### Post by wildmanne39 on 2011-05-20
> **deshmukh said:**
> Do you mean to say that Gnome 3 will NEVER be part of Ubuntu repositories?? I thought it was just the case of what is the 'default' desktop environment and Gnome will always be available as an option like XFCE, E17, etc
Hi, the next release is suppose to be built on gnome3, I was told you would have to get it from the ppa for some reason not sure why.

---

### Post by wildmanne39 on 2011-05-22
> **deshmukh said:**
> Do you mean to say that Gnome 3 will NEVER be part of Ubuntu repositories?? I thought it was just the case of what is the 'default' desktop environment and Gnome will always be available as an option like XFCE, E17, etcThe actual tab for that says visual effects is not in natty, set most everything in ccsm.

---

### Post by deshmukh on 2011-05-23
The solution is to run 'compiz --replace'.

This will ensure that all compiz plugins are available.

Marking the thread as solved.

---

### Post by beew on 2011-05-23
> **vickoxy said:**
> You should install Ubuntu Tweak. Then from there you activate wobble windows... Then you can manipulate also with other effects in CCSM.
Don´t know why is that, but it works...

You don't need Ubuntu tweak for that, just install CCSM (Compiz configuration Settings manager)  However, wobbly windows should be enabled by default. Probably the hardware is not sufficient to run Unity (and you shouldn't need proprietary graphic card for that, if use Nvidia, should be able to use Unity if install the package libg1-mesa-dri-experimental)

---


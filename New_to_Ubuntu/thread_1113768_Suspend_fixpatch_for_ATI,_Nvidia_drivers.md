---
title: "Suspend fix/patch for ATI, Nvidia drivers"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Incredible.Pie on 2009-04-02
This is a post from 2006...:

> Hi everyone. I just found out that a single change in a text file has enabled both my PC's -a desktop with Nvidia and an Inspiron 9300 laptop with Ati- to successfully resume after suspending to ram, using binary/proprietary drivers.
Edit the file /etc/default/acpi-support and change the line:
Code:

```
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

```
to
Code:

```
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false
```

reboot X (or the whole computer) and try suspend to ram.
Hope it helps you 

It works fantastically. Everything's fine for me with my Nvidia card. Which in all honesty is very, very disappointing. This fix/patch has been floating around these forums for three years, and still the developers haven't implemented it. The suspend problem is a *huge* issue with Ubuntu, and I'm absolutely positive it's why many people haven't adopted Ubuntu. Really, this frustrates me to no end.

A note: Nvidia users will need to add this to their device section of their /etc/X11/xorg.conf file

```
Option "NvAGP" "1"
```

(original thread: [http://ubuntuforums.org/showthread.php?t=327868](http://ubuntuforums.org/showthread.php?t=327868))

---

### Post by pme 72 on 2009-04-02
Thank you, Incredible.Pie. I tried the suspend fix/patch on my desktop pc with an ATI Radeon x1550 graphics card using open source drivers and it appears to work.

---

### Post by Incredible.Pie on 2009-04-05
> **pme 72 said:**
> Thank you, Incredible.Pie. I tried the suspend fix/patch on my desktop pc with an ATI Radeon x1550 graphics card using open source drivers and it appears to work.

No problem. Sometimes there's some networking problems that occur after you resume from suspend because certain network modules and drivers aren't stopped or resumed properly. I'll post a way to fix that here soon, too.

---

### Post by pme 72 on 2009-04-07
I'm on a stand alone machine, no network. Suspend continues to work. It is a nice feature to have available. I was getting used to just turning the machine off on weekends.

---

### Post by Incredible.Pie on 2009-04-14
Yeah, I got used to not using standby since I left Windows. I just left my machine on for months on end. Obviously that used up a hell of a lot of energy...

---

### Post by Lazy-buntu on 2009-04-14
I never tried suspend before today because I was avoiding a potential problem. I didn't have any problems with Ubuntu and I didn't want any :P


Without any changes to config files, my suspend works fine. My wireless, sound, nvidia drivers, etc. works flawlessly.

Haven't tried hibernate, but it probably will work :p

---

### Post by bobisculous on 2009-05-15
Suspend will always be the bane of my existence. Each time I install Ubuntu on my main desktop computer I try all these fixes and patches hoping for some reason it will begin to work. 
Once again, I have reinstalled Ubuntu to upgrade and once again it doesn't work. 

When I implement these fixes I get the exact same outcome as I do without the fixes. 

I suspend, the computer pretends like it does it. It shuts down all fans and HDDs. About 1 second afterwords it starts back up without me touching a thing. 
Once it starts back up and I try it again, (the second time, without doing a restart or such) it will just black out. Nothing works. No buttons, no awake. I hit the power button it instantly turns off. 

Ugh. 

-Cameron

---

### Post by ironhorse99 on 2009-05-29
I cannot save the file. It says I don't have permission to save the change. I run across this from time to time. Can someone explain how to get this permission.
I just installed a new nvidia 6200a agp 256-MiB card which works wonderfully(thank the Lord I'm finally finished with that horrid integrated VIA chip set.....man did that thing suck) The suspend function work fine before I installed the card. Thanks, mike

---

### Post by ironhorse99 on 2009-05-29
I just found something called Authorizations. It looks like I can  make changes to permissions here but I can't find the folder/file. Does anyone know anything about this. Mike

---

### Post by Incredible.Pie on 2009-05-29
> **ironhorse99 said:**
> I cannot save the file. It says I don't have permission to save the change. I run across this from time to time. Can someone explain how to get this permission.
I just installed a new nvidia 6200a agp 256-MiB card which works wonderfully(thank the Lord I'm finally finished with that horrid integrated VIA chip set.....man did that thing suck) The suspend function work fine before I installed the card. Thanks, mike

Sorry. I should have been a bit more detailed in this. You'll need to type in:

```
sudo gedit /etc/default/acpi-support
```

into a terminal. This will ask for your root (administrator) password. After you type that in, the text editor will open up and you'll be able to save and edit the file.

The reason why you can't edit the file the way you would a file in your home folder is because everything (or nearly everything, I'm not sure) outside of your home folder is not owned by you. The computer wouldn't allow you to read or write to the file for security reasons. It's a lot like Windows in that way. Hope this helps. If you have a problem with your network card after resuming from standby, just PM me again.

---

### Post by Incredible.Pie on 2009-05-29
> **bobisculous said:**
> Suspend will always be the bane of my existence. Each time I install Ubuntu on my main desktop computer I try all these fixes and patches hoping for some reason it will begin to work. 
Once again, I have reinstalled Ubuntu to upgrade and once again it doesn't work. 

When I implement these fixes I get the exact same outcome as I do without the fixes. 

I suspend, the computer pretends like it does it. It shuts down all fans and HDDs. About 1 second afterwords it starts back up without me touching a thing. 
Once it starts back up and I try it again, (the second time, without doing a restart or such) it will just black out. Nothing works. No buttons, no awake. I hit the power button it instantly turns off. 

Ugh. 

-Cameron

I can try to help with this. I'm not a super-techie, but I'll give it a whack. But I'll need to know more about your PC specs.

---

### Post by jdc.84 on 2009-08-06
Hi,

I tried Ubuntu 8.04 late last year. There were a few problems, one of which it would not resume from suspend, so I ditched it and went back to xp in wait for the new version and in hope that Ubuntu would resolve some of the issues.

Thus I am very new again to the whole Ubuntu world.


Just installed 9.04 and the resume from suspend problem is still here:
When trying to resume from suspend, on of the fans in the comp goes into overdrive and that's about it. Blank screen and fan overdrive.

I have now spent another who knows how long trolling through the forums looking for an answer to no real conclusion.


Here are the specs for my, HP xw4600 Workstation:

3gig ram
2 internal HDD (250gig each)
intel core 2 processor, 2.66gHrz
512mb Nvidia graphics card


I have come across this thread which seems to have the answer but am a little cautious to give it a go:
Does this solution sound like it will solve my suspend issue on my computer??


Thanks,
John

---

### Post by tehtrk on 2010-03-25
> **Incredible.Pie said:**
> 
Edit the file /etc/default/acpi-support and change the line:
```
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false
```  A note: Nvidia users will need to add this to their device section of their /etc/X11/xorg.conf file
```
Option "NvAGP" "1"
```

Wow, it's 2010 and one or both of these just fixed a problem I was having with my Inspiron 8600 nVidia FX5200 Go on Karmic while resuming from suspend. When I would resume, I would get a "bloom" of white and then the entire screen would just alternate between red, green, blue, black, and white colors.

Thanks!

---


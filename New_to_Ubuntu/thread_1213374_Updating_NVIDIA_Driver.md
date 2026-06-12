---
title: "Updating NVIDIA Driver"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by carl_76 on 2009-07-14
Hi.

I'm having video problems when using OOo Writer so I thought I might need to update my NVIDIA graphics driver.  They have released a version 185 for Linux 64-bit AMD, which is what I have.  I'm running Ubuntu 9.04.  NVIDIA released the new version as a .run file that I cannot run out of a terminal because the X window is still running.  Is there another way to update the driver?

Thanks.

---

### Post by ptn107 on 2009-07-14
The safe[r] way would be to add this PPA[1] to your software sources and just update Ubuntu:

```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
```

Don't forget to import the signing key.

[1] [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

---

### Post by carl_76 on 2009-07-15
Hi ptn107.

Thanks for your help.  I followed the instructions from the link you provided me and was able to update Ubuntu.  It appears that the problem with the disappearing tabs has been solved.  

The problem of text overlapping and merging when I'm typing into an existing paragraph is still there though.  Do you have any other suggestions?

Also, I saw that the update was for the 180 version of the nvidia driver.  Will the newer 185 version be added to the updates in the future?  I'm curious how the driver update cycle works.

Thanks!

Carl

---

### Post by ptn107 on 2009-07-16
The nvidia-glx-180 package you upgraded to actually installs version 185.18.14.  The package is just called nvidia-glx-180 because the driver is in the 180 series.  You can verify by typing the following in a terminal:

```
dpkg -l | grep nvidia-glx
```

Which will return something like this:

```
ii  nvidia-glx-180           185.18.14-0ubuntu1
          NVIDIA binary Xorg driver
```

---

### Post by carl_76 on 2009-07-16
Hi.

You're right, it is the 185 driver that's installed.  I guess I'll have to wait for them to finish working out the bugs before it completely works with OOo Writer.  Thanks for the help.  I won't have to go back to MS for the time being.

Carl

---

### Post by coffeecat on 2009-07-16
> **carl_76 said:**
> I guess I'll have to wait for them to finish working out the bugs before it completely works with OOo Writer.


Hmm... It may not be the nvidia driver that's causing your OOo Writer video problems. It may be a completely different issue. Is there a problem with video in any other apps? Can you post a screenshot to demonstrate exactly what the problem is?

---

### Post by carl_76 on 2009-07-16
Hi.

Here are four screen shots.  The first shows the graphics error at the end of the third line.  The second is the same text after I minimized the window and brought it back.  

The third screen capture is where the more significant errors are.  It shows errors at the end of the third line and in particular at the bottom right of the paragraph where several words are merged together.  There is also some extra graphics under the paragraph to left.  That is not from clipping the screen capture image.  The fourth is the same text after I minimized the window and then brought it back.

I hope these are helpful.  Thanks for all the suggestions.

Carl

---

### Post by coffeecat on 2009-07-16
I've had odd display issues with earlier versions of OOo where consecutive lines would occasionally get squashed together. It was a screen only artefact. Not the same as what you're seeing, but I always managed to clear the distortion by scrolling up or down a page or two. You seem to be able to clear the distortion by minimizing and restoring the window.

It's late here so I might be missing something, but this sounds like a Open Office issue, not a graphics driver one. Surely a graphics driver bug wouldn't concatenate some words and not others, and not display other video artefacts?

One suggestion: try installing Abiword from the repositories. It's a nice little word-processor - not nearly as full-featured as OO, but quite usable. It can import .doc documents and I'm fairly sure it can import OO .odt ones as well. Try using that for a time and see if you get the same problem. If you don't, then it's an OO issue and at least we know where to look for the cause.

---

### Post by carl_76 on 2009-07-17
Hi coffeecat.

Scrolling the distortion off the screen clears it for me, too.  I tried the OOo forum with this thread and was told it was more likely an ubuntu/nvidia problem than a Writer problem.

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=20661](http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=20661)

Using the updates suggested by another member earlier in this forum appears to have corrected the problem with the tabs on file menus disappearing, so possibly it is not a Writer problem.  The only other graphics problem I have is one of the title bars of an overlapping window occassionly allowing the title bar underneath to show through a little.  That one is nearly as inconvenient as this one, but because of that I can see this being an ubuntu/nvidia issue but I'm willing to try another suggestion.  I'd like to keep using Writer though.  Thanks for your help.

Carl

---

### Post by coffeecat on 2009-07-17
> **carl_76 said:**
> I'd like to keep using Writer though.

Oh, sure. I don't use Abiword much at all. I simply suggested it for an experiment. If you get similar artefacts in Abiword, then the suggestion that this is a nvidia driver problem is possible. If not, then this is down to Open Office itself.

By the way, I'm not getting this problem in OpenOffice in Jaunty with a nvidia GeForce 8400GS card. But I'm using the 173 version of the nvidia driver, which works OK. Long story, but the 180 driver was giving me different problems with this particular nvidia-chipsetted machine. Strangely, on another machine with the same PCIe graphics card and (an admittedly different) nvidia motherboard chipset, the 180 driver worked just fine.

You could try downgrading to the 173 driver in System > Adminstration > Hardware Drivers, if you really think the nvidia driver is the problem. It's easy enough to revert back to the 180, so that might be worth trying.

---

### Post by Sean-Michael on 2009-07-28
I've got this problem with open office as well using the latest driver.

Things that helped where going back to the 173 driver, or using the latest driver I disabled desktop effects/compiz I think.

Do you by chance not see some files when saving a document also, mine do but if I scroll threw the files the show up...

Hope this gets fixed soon, it's annoying lol

---

### Post by carl_76 on 2009-07-29
Hi.

I've got some psychological issue with going back to an earlier revision of something, so I won't be doing that.  :)

I took a look in synaptic and found a handful of items containing the name compiz.  Can you tell me which one specifically that I need to uninstall?

I just discovered a problem with OOo and tables when saving into a .doc format.  I think I'll do a search and maybe open a new thread for that one.  It seems to be unrelated to this one.

Thanks for the help!

Carl

---

### Post by coffeecat on 2009-07-30
> **carl_76 said:**
> I took a look in synaptic and found a handful of items containing the name compiz.  Can you tell me which one specifically that I need to uninstall?

Interesting that it could be a compiz problem. Anyway, you don't have to uninstall compiz, merely switch it off. Go to System > Preferences > Appearance > Visual Effects Tab, and click on the none button. Or if the 'extra' option was selected, you could try 'normal' and see if that helps.

If you really want to uninstall compiz, I'm not sure exactly what to remove. I've got quite a few compiz packages showing up in a Synaptic search, although I did install some compiz bits that don't come with a default install, and I'm not sure which of the compiz dependencies that show up in a search can be uninstalled safely.

Another reason for leaving the compiz packages intact but merely disabled is that it may be a particular compiz effect, rather than compiz itself, that's causing the problem. If that comes to light later, you could simply disable that effect with the compix-config-settings-manager, rather than the lot.

---

### Post by carl_76 on 2009-07-30
Hi coffeecat.

I'm going off of [Sean-Michael]("http://ubuntuforums.org/member.php?u=83263")'s posting just before mine.  I left compiz intact and turned off the visual effects as you suggested.  I will post again in a couple days about the results as I continue to use OOo.  I have to get to their forum now to ask about that issue with tables I hinted at in my earlier posting....

Thanks for the help.

Carl

---


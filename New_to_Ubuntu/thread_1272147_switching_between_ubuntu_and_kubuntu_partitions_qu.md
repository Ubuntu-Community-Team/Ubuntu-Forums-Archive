---
title: "switching between ubuntu and kubuntu partitions question"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-21
I installed kubuntu on a partition of the hd that has ubuntu on the larger partition.

How do I switch between the 2 once kubuntu has booted the system.

How do I select Ubuntu to boot initially.

Do most programs (firefox, limewire, etc...) run/have the same version as what one dowloads for ubuntu?

Is kubuntu basically a different graphics interface (GUI) for ubuntu?  Is ubuntu basically running kubuntu behind the scene/in the background?

---

### Post by mjp29 on 2009-09-21
installed kubuntu on a partition of the hd that has ubuntu on the larger partition.

How do I switch between the 2 once kubuntu has booted the system.

How do I select Ubuntu to boot initially.

Do most programs (firefox, limewire, etc...) run/have the same version as what one dowloads for ubuntu?

Is kubuntu basically a different graphics interface (GUI) for ubuntu?  Is ubuntu basically running kubuntu behind the scene/in the background?

---

### Post by oboedad55 on 2009-09-21
> **mjp29 said:**
> I installed kubuntu on a partition of the hd that has ubuntu on the larger partition.

How do I switch between the 2 once kubuntu has booted the system.

How do I select Ubuntu to boot initially.

Do most programs (firefox, limewire, etc...) run/have the same version as what one dowloads for ubuntu?

Is kubuntu basically a different graphics interface (GUI) for ubuntu?  Is ubuntu basically running kubuntu behind the scene/in the background?

Kubuntu uses KDE for a DE while Ubuntu uses Gnome. I'll get flamed for this, but it seems preferences are split. Use whichever you prefer. I'm assuming from your post that you installed Kubuntu second. In either case Grub should have picked up the other Ubuntu and added it to the menu. If this is not the case post back and someone will either explain how to re-run Grub or edit your menu.lst, which is a text file that tells Grub where each OS is.

---

### Post by ChrT on 2009-09-21
You do realise you can install kubuntu from ubuntu with 

```
# apt-get install kubuntu-desktop
```

And switch between the two without requiring seperate installs or rebooting, right? :confused:

---

### Post by mjp29 on 2009-09-21
i did know you can install kubuntu from within ubuntu but i didn't know you could do it without partitioning the hd for 2 seperate operating systems.  oh well, i downloaded kubuntu on the mac and burned an image and installed it on the ubuntu box and had it partition so kubuntu takes up about 1/4 the space that ubuntu is taking up.  no big deal, i'm just testing things out now (testing the water) to see what i like and so forth.  i plan to put a larger hd in the ubuntu box and all will be wiped out in the end anyways when i decide what to do.

i am a newbie, so i have never heard of kde for a de (but i have read about gnome many times.  I guess it comes back to my ultimate question which is will most programs that run in ubuntu also work in kubunti (programs like firefox, limewire, etc...)

p.s. anyone know how i can delete my duplicate post here [put it as kubuntu] but just received an infraction for duplicate posting in the apple forum and ubuntu absolute beginner forum here, so probably going to get another infraction for this duplicate post - as homer simpson would say - D'oh!

---

### Post by mjp29 on 2009-09-21
> **oboedad55 said:**
> Kubuntu uses KDE for a DE while Ubuntu uses Gnome. I'll get flamed for this, but it seems preferences are split. Use whichever you prefer. I'm assuming from your post that you installed Kubuntu second. In either case Grub should have picked up the other Ubuntu and added it to the menu. If this is not the case post back and someone will either explain how to re-run Grub or edit your menu.lst, which is a text file that tells Grub where each OS is.

Your assumption is right - I installed Ubuntu first and then installed Kubuntu second (installed it from a downloaded disk image and partitioned the hd to have kubuntu on about 1/4 or 1/5 of the hd).

2 questions

1) which menu in kubuntu do i click to switch over to ubuntu

2) upon turning on computer/booting how do i choose which to go into (since the hd is partitioned now for both)

thank you so much for your reply to me

---

### Post by Iowan on 2009-09-21
> **mjp29 said:**
> p.s. anyone know how i can delete my duplicate post here Looks like it's already done - moved (to this thread) anyway.

---

### Post by oboedad55 on 2009-09-21
> **mjp29 said:**
> Your assumption is right - I installed Ubuntu first and then installed Kubuntu second (installed it from a downloaded disk image and partitioned the hd to have kubuntu on about 1/4 or 1/5 of the hd).

2 questions

1) which menu in kubuntu do i click to switch over to ubuntu

2) upon turning on computer/booting how do i choose which to go into (since the hd is partitioned now for both)

thank you so much for your reply to me

Do you have each one installed separately or do you have both desktops installed on one installation?

---

### Post by mjp29 on 2009-09-21
> **Iowan said:**
> Looks like it's already done - moved (to this thread) anyway.

D'oh!

I noticed that too - probably will receive another infraction (another private message and another point taken away).  Not that I know what points taken away means but I promise I won't keep doing it.  I have an old G4 Mac (os x) and am installing Ubuntu (or Kubuntu) on a newer (yet old still) Pentium 4 box to replace the Mac with.  I just thought posting in the Mac Ubuntu forum and duplicate posting it in the Ubuntu absolute beginner forum here would get me more information for my network file migration questions (via ethernet).  Now I know it's a big no no to duplicate post in any Ubuntu forums here.  Now I've done the ultimate no-no by posting 2 duplicate posts in beginner forum here (chose one as Kubuntu and thought it would go into a Kubuntu forum but noticed it showed up side by side to my Ubuntu post here).

D'oh!

All I can say is that I will stop doing it and thank the Ubuntu forums person for the warning(s).  I suppose while the rest of you are working your status/level up in the forums I am working my way down (losing points).  D'oh!  [I'll have to find an avatar with homer simpson saying that to represent my stupidity)  The one at [http://en.wikipedia.org/wiki/D'oh](http://en.wikipedia.org/wiki/D'oh)! comes to mind.

---

### Post by oboedad55 on 2009-09-21
> **mjp29 said:**
> D'oh!

I noticed that too - probably will receive another infraction (another private message and another point taken away).  Not that I know what points taken away means but I promise I won't keep doing it.  I have an old G4 Mac (os x) and am installing Ubuntu (or Kubuntu) on a newer (yet old still) Pentium 4 box to replace the Mac with.  I just thought posting in the Mac Ubuntu forum and duplicate posting it in the Ubuntu absolute beginner forum here would get me more information for my network file migration questions (via ethernet).  Now I know it's a big no no to duplicate post in any Ubuntu forums here.  Now I've done the ultimate no-no by posting 2 duplicate posts in beginner forum here (chose one as Kubuntu and thought it would go into a Kubuntu forum but noticed it showed up side by side to my Ubuntu post here).

D'oh!

All I can say is that I will stop doing it and thank the Ubuntu forums person for the warning(s).  I suppose while the rest of you are working your status/level up in the forums I am working my way down (losing points).  D'oh!  [I'll have to find an avatar with homer simpson saying that to represent my stupidity)  The one at [http://en.wikipedia.org/wiki/D'oh](http://en.wikipedia.org/wiki/D'oh)! comes to mind.

Not a big deal. I don't think anyone will come and cut your fingers off. What you were thinking made a kind of sense. Now you know and you'll never screw up again! :P

---

### Post by oldos2er on 2009-09-21
"I guess it comes back to my ultimate question which is will most programs that run in ubuntu also work in kubunti (programs like firefox, limewire, etc...)"

 Any program will work under any desktop environment, it's just a matter of getting the proper libraries installed. If you use a package manager, this will be taken care of automatically.

---

### Post by mjp29 on 2009-09-21
> **oboedad55 said:**
> Do you have each one installed separately or do you have both desktops installed on one installation?


not in one installation i suppose

i downloaded ubuntu and burned a disk image of ubuntu on mac os x and installed it on pc box

then wanted to try out kubuntu (read it looked more like mac or vista) and downloaded it on mac and burned a disk image on mac and installed it on pc box - but partitioned it (is suppose that's what it is called) and gave kubuntu about 1/4 o 1/5 of hd space on pc box to run it side by side on pc box

---

### Post by mjp29 on 2009-09-21
> **oldos2er said:**
> "I guess it comes back to my ultimate question which is will most programs that run in ubuntu also work in kubunti (programs like firefox, limewire, etc...)"

 Any program will work under any desktop environment, it's just a matter of getting the proper libraries installed. If you use a package manager, this will be taken care of automatically.

then i guess my question is which is easiest to download and install lynix (ubuntu) programs in for someone that doesn't want to enter a lot of code (i screwed up ubuntu once by entering too much into terminal and did a complete ubuntu reinstall).  the question should be then, which would one use if they want to download programs and install them more easily without entering as much code or any code.  from my initial thoughts of kubuntu it looks really pretty but noticed it didn't seem to come with firefox, had problems dowloading firefox and getting it to work, haven't tried limewire yet in kubuntu, and last thought the email progrm wasn't easy to find (evolution?).  one last thought is that kubuntu is almost too much eye candy but if i use it a while might like all that eye candy and get use to it.

---

### Post by oboedad55 on 2009-09-21
> **mjp29 said:**
> then i guess my question is which is easiest to download and install lynix (ubuntu) programs in for someone that doesn't want to enter a lot of code (i screwed up ubuntu once by entering too much into terminal and did a complete ubuntu reinstall).  the question should be then, which would one use if they want to download programs and install them more easily without entering as much code or any code.  from my initial thoughts of kubuntu it looks really pretty but noticed it didn't seem to come with firefox, had problems dowloading firefox and getting it to work, haven't tried limewire yet in kubuntu, and last thought the email progrm wasn't easy to find (evolution?).  one last thought is that kubuntu is almost too much eye candy but if i use it a while might like all that eye candy and get use to it.

I'm sorry, but your post is pretty hard to read with no punctuation. I think you're looking for program installation. If so, go to, System>Administration>Synaptic Package Manager. There you can find the programs you need. Just use the search function. If there's something you want that's not there post back and someone will help you.

---

### Post by oldos2er on 2009-09-22
It's not necessary to use the command line to manage software; instead use Add/Remove, or Synaptic (in Gnome), or Adept (in KDE).

---


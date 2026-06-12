---
title: "nvidia 8600 gt desktop effects and other problems"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by cobaltseeker on 2009-05-20
Okay so i've just installed Jaunty and am ready to ditch windows assuming i can get everything working properly ... so here goes my first major problem thus far.

I've been searching for a good hour or two to no avail, i'm completely lost on this one!

I first noted a problem when i tried changing desktop effects - says i can't do that.
"Desktop effects could not be enabled"

then i tried playing a video - no good (it says i need to download a decoder that it can't find for one reason or another?)

so mpg mp3 etc files cannot be played because they need the proper decoder which the program could not find (is this related? If not i'll need to create a seperate thread i think?)

So after some searching i found "compiz-check" ... that didn't help any either - 

```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600M GT (rev a1)
 Driver in use:         nv
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: nv driver in use 

```so it seems i can't run compiz-check because i have a nvidia card?

i don't have anything listed under "proprietary drivers" except for my broadcom wireless driver (which i got to work after a touch of tweaking) so i'm not sure if maybe a different driver would help.. thing is even if it would - i don't know how to go about FINDING said driver to test it!

I'm a total newbie here and any help would be greatly appreciated - doubly so if it makes any sense :P I used to think i knew a whole lot about computers... then i started playing with linux. So please go easy on me!

if it helps any - i have a Dell XPS m1530 and card is Nvidia 8600 GT as stated above

so my problem - i can't change desktop effects, i can't play videos (both online and mpgs... nor was i able to download the decoders) , and compiz-check just gives an error. Help!

-CS
CobaltSeeker

---

### Post by Joeb454 on 2009-05-20
Have you tried under System &#8594; Administration &#8594; Hardware Drivers?

This will tell you if you have the nvidia drivers installed. If not, it sounds like all you need to do is install them :)

---

### Post by cobaltseeker on 2009-05-20
> **Joeb454 said:**
> Have you tried under System &#8594; Administration &#8594; Hardware Drivers?

This will tell you if you have the nvidia drivers installed. If not, it sounds like all you need to do is install them :)

yep - only shows my broadcom driver, no others (and the broadcom wireless works)

how, btw, would i go about (re-)installing the drivers? i wonder if it just didn't install them or some such and i have to do that manually?....

---

### Post by Joeb454 on 2009-05-20
Try installing the [latest nvidia driver](apt://nvidia-glx-180) from the repo's (the 180 driver). I'm surprised it didn't prompt you to install when you first booted.

If, when you try to install that package, you get a message saying it is installed, we can try and reinstall :)

---

### Post by cobaltseeker on 2009-05-20
i just get an error that says "could not find package nvidia-glx-180" ?

happens when i click the link

---

### Post by durand on 2009-05-20
Have you tried enabling all the repositories in System > Administration > Software Sources?

---

### Post by cobaltseeker on 2009-05-20
durand - 
everything is checked except source code and the "install from cd-rom" jaunty jackalope bits? 

check those as well? (i don't think i need source codes... but the other one? hmm)

---

### Post by Duskao on 2009-05-20
Have you updated your system? Make sure you do that. Then try the hardware drivers again. If that doesn't work then give EnvyNG a try, google it. 
As for your video and stuff, go to add/remove then search for "restricted" it will show ubuntu restricted modules. That should help with your mp3 and video problems, as well as install flash and java. Oh, and before you do the search, make sure "all available applications" is selected (at the top of the window). That should get you going. If you are going to be using wine, then make sure you check out winehq.org the app db for the best way to get games going if it's possible. 
Hope this helps. Good luck.

---

### Post by durand on 2009-05-20
> **cobaltseeker said:**
> durand - 
everything is checked except source code and the "install from cd-rom" jaunty jackalope bits? 

check those as well? (i don't think i need source codes... but the other one? hmm)

Thats quite strange. Open synaptic package manager and search for nvidia-glx and see what packages are there. Check what happens when you select nvidia-glx-180 and install it. As for your restricted extras, you need to install ubuntu-restricted-extras. When you play a movie or file that isn't supported, a coded install box should pop up.

---

### Post by cobaltseeker on 2009-05-20
Durand - that same one (nvidia-glx-180) isn't present, but i did find nvidia-180-modaliases. Should i try that one?
Duh, how do i install ubuntu-restricted-extras?


duskao - gosh i feel so stupid... how/where do i update my system? (edit :: System - administration - update manager ... ? installing those seems to be a bunch there... for all the hell i'm having getting everything working, this is oddly fun :P ... in a twisted kinda way )

---

### Post by durand on 2009-05-20
No, nvidia-180-modaliases is different. To update, press the reload button in synaptic. After that, find the two packages with the search though you can just use the codec installer which should handle it automatically.

---

### Post by cobaltseeker on 2009-05-20
codec installer?

Nvidia-glx-180 still doesn't show even after hitting reload.

---

### Post by cobaltseeker on 2009-05-20
update!

Looks like i could find nvidia-glx-180, i had to use the "search" button, not the 'quick search'

 i wonder what the difference is there? installing now will re-update in a second...

---

### Post by durand on 2009-05-20
With quick search, it will only search in the category you're currently looking at. You need to select the "All" section first.

---

### Post by cobaltseeker on 2009-05-20
mind if i kiss you?

All of that is working now. music and movies and desktop effects.

for some reason it also decided to connect/download required codecs. (i'm not sure if this is because of system-update or this driver or both? but hey it works!!)

Deepest gratitude :) Thanks again!!

---

### Post by durand on 2009-05-20
It would have been the update. It goes through all the repositories and adds the file descriptions to its offline database. You need to update whenever you add a new repository.

---

### Post by cpacheco on 2009-06-04
Cobaltseeker, one question, when you shutdown/reboot does your screen blanks and "burns" (fades) to black? I have the M1530 with the nVidia 8600, with the NVidia Hardware Driver 180 and it wont shutdown (also tried the 173 Driver and had the same problem). Any help would be greatly appreciated.

---


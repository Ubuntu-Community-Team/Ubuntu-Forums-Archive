---
title: "Kubuntu 10.4 Loads black screen"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Mr. Hyde on 2010-08-22
I'm having some trouble with a Kubuntu install. I've installed Kubuntu 10.04 in a dual boot environment with windows XP on one of my old laptops (basically for my wife to use, for internet browsing etc). I've never installed Linux with windows before, so I might have done something wrong... here is what I did:

1) downloaded the ISO and mounted it as a CD using Daemon Tools (this computer's CD ROM doesn't work, so loading it from start up wasn't an option unless I used the USB method, which seemed more involved)
2) ran Wubi and installed it from within the windows environment
3) it has it's own partition of 10GBs with nothing else except the kubuntu OS on there

When I start up the laptop, it can run windows normally. When I run Kubuntu in normal mode, I get the splash screen and tht's it, no sounds no nothing. When I run it in safe mode, I get a black screen with a mouse cursor that I can move around... but still no sounds. When I hit ctr+alt+F1 in safe mode, the computer gets put into an infinite loop where some text is flashed in the upper right hand portion of the screen, but it blinks too fast for me to see what's happening.

Any help would be great.

---

### Post by Rubi1200 on 2010-08-22
Hi,
could you please tell us how much RAM the laptop has and what graphics card is installed?

Also, take a look here and see if anything fits with your situation: [https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

But first provide the information before taking any other actions.

Thanks.

---

### Post by Mr. Hyde on 2010-08-22
> **Rubi1200 said:**
> Hi,
could you please tell us how much RAM the laptop has and what graphics card is installed?

Also, take a look here and see if anything fits with your situation: [https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

But first provide the information before taking any other actions.

Thanks.

752 MB of RAM
Intel 82852/82855 GM/GME Graphics Controller (definitely nothing special)

Unfortunately, it doesn't look like any of the topics in that faq apply to me.

---

### Post by Rubi1200 on 2010-08-22
> **Mr. Hyde said:**
> 752 MB of RAM
Intel 82852/82855 GM/GME Graphics Controller (definitely nothing special)

Unfortunately, it doesn't look like any of the topics in that faq apply to me.
Thanks for the information.

As things stand, I suspect it may be a graphics issue. There is a known problem with Intel chipsets in the 10.04 release (all versions).

This link has a workaround for the chipset you have:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

(If I am not mistaken, you need to use Workaround F, but check to make sure).

Disclaimer: I know that most, if not all, workarounds have been effective for regular installs. I do not know what will happen with a Wubi install, but I assume the principal is the same since you would be working within that environment. In any event, I just wanted you to be aware of this.

---


---
title: "Graphics driver for EeePC 1001PE"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-09-25
Hi,

I have a EeePC 1005PE notebook, whose graphics card is a Intel GMA X3150. Ubuntu 10.04's default graphics driver is sub-par for this notebook, and the operating system tells me as much every time I log in; moreover Compiz effects cannot be enabled unless a proper graphics driver is activated. I don't know where to look for the correct driver - can anyone please help? Oh, and I am only comfortable with the GUI so far, so I prefer not to rely on a command-line solution.

Thank you.

Kind Regards,

Robert

---

### Post by formaldehyde_spoon on 2010-09-25
You know the title says 1001?

 I have a 1005PE and haven't had any trouble...
Pretty sure I didn't install any other drivers, and never got any messages.

Have a look in System > Administration > Hardware Drivers.  If Ubuntu knows of drivers you should be using you should be able to install them wit a single click there.

---

### Post by Robert Buckmaster on 2010-09-25
Yes, I am aware of the mistake. However, the forum wouldn't allow me to change the title once I committed the error.

I tried opening Hardware drivers, as you suggested. After a search, the system said something to the effect that no proprietary drivers were being used, and there weren't any drivers to choose from.

Where else should I look for drivers?

---

### Post by Robert Buckmaster on 2010-09-25
Hi,

I have a eeePC 1005PE with a GMA 3150 graphics card. Ubuntu says it doesn't support this card and no proprietary drivers are available. The default driver doesn't allow compiz effects to be enabled. Where can I find a driver that will support my graphics card and allow me to use compiz?

Thanks,

Robert

---

### Post by mrhhug on 2010-09-25
try something from here : 

[http://ubuntuforums.org/showthread.php?t=1413295](http://ubuntuforums.org/showthread.php?t=1413295)

before you start ndiswrapper

---

### Post by formaldehyde_spoon on 2010-09-25
I just checked mine, and I'm not using any proprietary drivers either (I get the same as you at System > Admin > Drivers). 

I'm running 10.04, and never had any trouble or any messages about drivers.

---

### Post by waynefoutz on 2010-09-25
there are no proprietary drivers for Intel graphics cards. What's installed out of the box is basically as good as it gets.

---

### Post by Robert Buckmaster on 2010-09-26
So, there isn't any way of getting rid of the message on my start up saying that the graphics effect are degraded for lack of an optimal graphics driver? That is, I can't get my computer to work efficiently as far as my graphics card is concerned? And is it not possible to enable my computer to effect compiz effects? Whenever I try to change the settings of visual effects, a window comes up saying the system is looking for available drivers; then there is an error message, saying the effects could not be enabled.

---

### Post by Robert Buckmaster on 2010-09-26
I should prefer to avoid using ndiswrapper, if I can help it. Is there anywhere I can check for available drivers to support my graphics card? Many were promising, on other pages, that Lucid would solve all the issues around this driver's lack of support.

---

### Post by overdrank on 2010-09-26
Hi and welcome. Please do not create multiple threads on the same issue. Threads merged.

---

### Post by QLee on 2010-09-26
[QUOTE=Robert Buckmaster]...
 That is, I can't get my computer to work efficiently as far as my graphics card is concerned? [/QUOTE]
This is not the conclusion I would draw from this experience.


[QUOTE=Robert Buckmaster]And is it not possible to enable my computer to effect compiz effects? Whenever I try to change the settings of visual effects, a window comes up saying the system is looking for available drivers; then there is an error message, saying the effects could not be enabled.[/QUOTE]

Well, it is a netbook after all, meant to easy to carry around and not meant to be a platform for "cool" effects. I had a quick look at a couple of reviews for your specific single core machine. I have no data on the reviewers' ability but they do lead me to believe that what you are seeing is not completely unreasonable.

CNET review:
**"The good:** First Netbook with new Intel Atom N450 CPU; fantastic battery life.
 **The bad:** Lacks modern Netbook upgrades such as HD display, extra RAM; only minor performance boost over previous versions.
 **The bottom line:** As  the first next-gen Intel Atom Netbook, Asus' Eee PC 1005PE offers  amazing battery life, but otherwise feels like a last-gen system.
 [B]...
[/B] Nvidia's Ion GPU is also becoming a go-to part for upscale Netbooks, but is not included here. 
..."

Engadget review:
"...
It's a similar story with the Intel's GMA 3150 GPU, which is now  integrated into the Pineview CPU. Like previous Atom-based Eee PCs  netbooks (excluding the [1201N]("http://www.engadget.com/2009/12/18/asus-eee-pc-1201n-review/"))  you aren't going to want to put a 1080p video anywhere near it, but a  720p Quicktime clip played back quite smoothly, but we had the same old  choppy issues playing an HD YouTube video. 3DMark06 scores also show  that graphics gain is minimal: the 1005PE notched 157, which is higher  than the GMA945-based 1008HA's 102, but not by such a significant amount  that you'd notice real world differences.
...
f you've been waiting for Pine Trail netbooks  hoping for noticeably better performance and graphics, you're not going  to get it -- and the truth is you  probably won't even notice the difference between the 1005PE and older  Diamondville-based Eee PCs until you start using it on battery power  alone."


So, if it were mine, I would not try to use compiz effects. But of course you may do what you choose.

---


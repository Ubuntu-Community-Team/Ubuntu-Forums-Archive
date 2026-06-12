---
title: "Triple Monitors"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by trevzilla on 2010-07-06
I have a triple monitor set up with my computer, however I don't know which video cards I'm using off hand.  I just installed over a windows xp installation where my triple monitors were all working fine.  Does any one know how to get them working in Ubuntu 10.04?  I have two of them working now, but the third one is blank.

When I am booting up, the ubuntu splash screen shows up on monitor 2.  When I am running Ubuntu, monitor 2 is blank and monitors 1 and 3 are working.

Thoughts?

Thanks so much!
Trev

---

### Post by trevzilla on 2010-07-06
I ran a command in terminal to find the video cards that I was running and this is what it returned.

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

It doesn't seem as if I have drivers installed yet for my video cards.  Maybe that is the problem?  I'm at a loss...

---

### Post by tom.swartz07 on 2010-07-06
Did you try looking under the 'Monitors' Application in system menu?

Unfortunately, both of those cards aren't supported by ATI anymore (along with most of their other ones on Linux) so you really dont have any options as far as the Proprietary drivers.

My suggestion is to look under the monitors app and see what tweaks you could find there.

---

### Post by alphacrucis2 on 2010-07-06
> **trevzilla said:**
> I ran a command in terminal to find the video cards that I was running and this is what it returned.

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

It doesn't seem as if I have drivers installed yet for my video cards.  Maybe that is the problem?  I'm at a loss...

You won't be able to use the proprietary drivers. The reason being that about march last year IIRC ATI dropped support for a bunch of "legacy" cards (including yours) from all Catalyst releases since then. The catch 22 is that the older Catalyst drivers that support your setup don't work with the current x server and kernel used by Ubuntu. You may be able to get the three monitors working using the Radeon OSS driver, which Ubuntu will already be using, by tweaking the xorg.conf file. If someone with the specific knowledge doesn't pop up in this thread then search for something like 'ubuntu radeon xpress xorg.conf triple monitor'

---

### Post by trevzilla on 2010-07-06
Yes, I have looked under the 'Monitors' Application in the system menu.  Unfortunately, it has very few tweaks.  And it does not even detect my monitor 2.  It only says I have Monitor 1 and 3.  Plus, it doesn't even have a full range of resolutions.

I was using "ultramon" when I was running windows.  Is there a similar program for Ubuntu?

Thanks!

---

### Post by alphacrucis2 on 2010-07-06
> **trevzilla said:**
> Yes, I have looked under the 'Monitors' Application in the system menu.  Unfortunately, it has very few tweaks.  And it does not even detect my monitor 2.  It only says I have Monitor 1 and 3.  Plus, it doesn't even have a full range of resolutions.

I was using "ultramon" when I was running windows.  Is there a similar program for Ubuntu?

Thanks!

You best bet may be to try the forums at Phoronix. There are a bunch of Linux/ATI experts who post there (including ATI staffers). They have a forum section specializing on the OSS ATI driver.

[http://www.phoronix.com/forums/]("http://www.phoronix.com/forums/")

---

### Post by stderr on 2010-07-06
Assuming you get ATI's open source drivers running, my guess is that you'd then be looking to use Xinerama to run a 3 monitor setup. 

On Ubuntu, Compiz offers most/more/(& in some ways less) of the functionality of Ultramon. However, I was unable to run Compiz with Xinerama, and my reckoning is that you won't be able to either (they generally don't play nicely).

With NVIDIA, which has much better Linux driver support than ATI (IMHO, but also in many others' too), the three main choices for triple monitors are:

 - TwinView + X screen (you can't drag windows between the TwinView & Xscreen setups, but Compiz works - however you *need* to run Compiz just to get maximising to one monitor working)
 - Xinerama (no Compiz, but you can drag windows anywhere & everywhere, & maximising is fine)
 - 3 separate X screens (no window dragging between any of the monitors)

Neither of which is perfect, but I've eventually settled for the first option. This won't be available to you - TwinView is NVIDIA-specific.

I can't quite see you getting a setup you'll be that happy with given open source ATI drivers and whatever triple-monitor options you may have after that... I mean, I don't know of another option than Xinerama under ATI for multi-monitors, aside from separate X screens (I may be wrong), and Xinerama == no Compiz, AFAIK, and Compiz is what would provide your Ultramon-style features (assuming you actually do want such customisable functionality).

My advice: either follow alphacrucis2's advice and ask around at some more specialised forums where more people are using the open source ATi driver, or wait a bit longer here for some more advice - hopefully I've missed something blatant, or (I hate to recommend buying things, but...) newer graphics cards, especially NVIDIA, would make things easier, especially given you can pick up a card for just over £20 over here in the UK.

edit: Actually, I may have read too much into your mention of Ultramon - it's possible that Xinerama may suffice for you.

---


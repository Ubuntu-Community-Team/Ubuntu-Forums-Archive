---
title: "wireless and Ubuntu!"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by buntunub on 2007-08-08
So whats the deal with Ubuntu struggling so very hard with everyones wireless connections, at least at first? Even after you get wireless working (invariably by following some howto or guide that provides a workaround to Ubuntu's shoddy development) then your faced with WPA or WEP issues! There are other distro's that dont seem to have even half these issues, so what is going on with the underlying code here? I think about half the blame lies with gnome and its network manager, which is just crap compared to knetworkmanager, which is also crap, but does seem to work much better for most folks. As far as other networking solutions, ive tried wicd, which is an app that is being much touted as being superior to the gnome/buntu manager, but it is garbage as well. So whats a linux nub to do here? There has got to come a solution to these issues with Gutsy or forget it! I have every respect for the Buntu dev's, but one can only continue to fight with these wireless issues for so long until you find a better solution like Sabayon or PCLos (note that Fedora has even worse problems with wireless than the Buntu's do). Anyway, just my 2 cents, and if anyone knows of a more universal suggestion to fix this problem, please do tell!

---

### Post by buntunub on 2007-08-09
Bumparumpa

---

### Post by kevdog on 2007-08-09
Go find another linux distro...I can't deal with all the complaining!!!:mad:

---

### Post by petit.padavoine on 2007-08-09
You could, alternatively, pay and buy Windows. But in that sentence, there is the word "pay".

Which is not in the sentence "You could download Ubuntu". No "pay".

Am I making any sense?

Stop complaining. Be thankful. You have a great working OS and you're not paying for it.

If you want a solution to a specific problem, just search for solutions to it or post about it. Don't complain.

---

### Post by eentonig on 2007-08-09
Or buy hw that is known to work with Linux/Ubuntu.

I never had any problem to get my wireless working.

---

### Post by splintercellguy on 2007-08-09
Well, excuse me for skipping the text blob, but what trouble do you have? If you are unable to get wireless to work, can you post the output of lspci?

---

### Post by noob12 on 2007-08-09
The area is certainly maturing.  Perhaps it's been overbilled for ease of use and readiness for prime time, particularly in the area of wireless.   

Of what I've seen, none of the linux distros do as well as Windows XP  or Mac OS X in this area.    But the progress I've seen lately is encouraging, and I support the movement. 

In my limited experience, about 80-90% of the problems are at the basic driver level, the rest due to either ACPI/power management/hotplug issues or overall network management (NM or wicd).

The wireless device space may still be too fast moving for open source to keep up on drivers right now.  For Windows, at least vendors assume some of the onus of making drivers really work with the OS (while Mac OS X really only needs to deal with whatever Apple ships in its hardware).  This is why one so often has to resort to the ndiswrapper approach to work with these things.  Maybe this is actually the way to go for the medium term.

In this fast-moving area, Ubuntu 7.04 isn't up-to-date on ndiswrapper and on some of the native wireless drivers, as (I'm sure) updates lost to the need to stabilize and test.  The price and pain of this is pretty well indicated on this forum. (Building driver modules from source pulls of daily snapshots!  Oh my!)

NM and wicd are both immature when compared to wireless treatment in Windows XP.  But they're both a lot better than one could do just a couple of years ago on Linux.  My opinion is that because this paradigm isn't going to change much, developers of these tools will be able to catch up, as long as people use them and bitch constructively.

---

### Post by buntunub on 2007-08-14
Apparently the way I wrote my post must have been pretty poor if you got the impression I was complaining. No complaining here and my wireless works fine after many many hours of struggling with it. The point I was trying to make is that it just does not seem that wireless was very well addressed in fiesty because ALOT of people are really having big problems there. This should not be. Wireless in Linux is actually quite well supported in various ways. Ubuntu has done a great job of supporting dozens of things, and it is generally one of the most stable systems around. I think for Gutsy they just need to put some extra emphasis into the development of wireless support. Possibly use Wicd or something like that which appears to be better tailored to the newby and includes support for more wireless options including easy tailorability. Knetworkmanager does not seem to suffer from these types of issues as much, although it has its own set of issues (which I have heard have been eliminated in KDE4.0). So anyway, I had hoped to see some real ideas emerge from this thread and not flames.

---

### Post by phillipchandler on 2007-09-21
buntunub is talking outta is ****. WICD is a perfect piece of kit for getting wpa working. If you wanna use knetworkmanager, you have to edit scripts etc and set it up for your own wifi.

But if you dont have wifi and use a friends wifi, then WICD is great as we had problems with knetworkmanager.
I got frustrated as well spending all the time trying to set up wpa, and in the end found the right solution. So buntunub wants to do the same and try looking a bit harder / longer. Or is he complaining that knetworkmanager and wicd are just too hard for him, in which case go back to windows.

---


---
title: "Ubuntu does random things on its own1"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-11
okay so i just recently installed ubuntu on my system.. i dont run anything else except ubuntu on the system..

it just seems to me that ubuntu will randomly perform RANDOM actions on its own and then im left with a huge search and headache of how to fix it.. for instance, recently, its been switching into this weird mode where i cant click on certain things.. but i figured out that it happens because ubuntu's window menu mode automatically gets activated (ALTHOUGH THE SHORTCUT/ACCELRATOR IS SET TO BE A VERY COMPLEX KEYSTROKE COMBINATION THAT I NEVER EVER EVER EVER USE! it still goes into it on its own!!!)

anyway the reason im writting this thread is cause i have a new problem..
i was watching a video on youtube.,. didnt type or click anything and all of a sudden (ON ITS OWN!) the firefox browser decides that it wants to go what im gunna call "semi-fullscreen".. so the "start menu bar" that goes across the bottom (the one where you can click on different apps and stuff do bring them into focus, windows has this thing too), the top menu bar (the one where you can select programs and look at the time and log out from), as well as the minimize and maximize on firefox have MAGICALLY disapeared!!! so for instance if i try to double click near the top of firefox in order to make it minimize or watever, it doesnt do anything because its not there!! i cant even right click now to pull down that pop up menu in order to close maximze or minimize the window or to switch to another program i have to alt tab it... WTF?!

btw the disapearing menus at the top and botom of the screen arent completely gone, they are just being covered by firefox so if i close firefox they will still be there and will be functional.. that is unless ubuntu wants to enter that window menu mode on its own again.. also ive noticed that while im typing, sometimes there will be extra spaces inserted ON ITS OWN!.. my keyboard is not messed up either..

---

### Post by 3rdalbum on 2009-04-11
This sounds really freaky, but today when I was browsing with Konqueror it kept going full-screen when I opened a new window.

---

### Post by Zill on 2009-04-11
ayastona:

(1)  Please clarify *exactly* which version of Ubuntu you are using.

(2)  Reboot with your Ubuntu CD in the drive and run Ubuntu directly from the CD ("live CD" mode), rather than from your hdd.  Then advise if the same problems persist when using the live CD.

---

### Post by Gen2ly on 2009-04-11
Yikes!  Looks like you might be on the right track though.  Probably what ishappening is that the keyboard is sending signals to Gnome...  If this is true then it's probably a problem due to hal or possibly udev and that means you can't do much about it until they get fixed.  Do you have another keyboard around you can test?

---

### Post by a2z on 2009-04-11
I've also been experiencing disappearing task bars,trays,panels. 
First with intrepid. And also with jaunty. (both on separate h/ds)

I have dual monitors, with NVIDIA driver. Using Compiz-Fusion and God knows what else I may have in here causing conflicts. 

While reading tons of forums pertaining to panel disappearance,
I've been all around the system exploring  different possibilities to get the panels back. And being the big Linux noob that I am, can hardly remember how to get to any certain routine that worked. 
I've found at times, the only way to get them back and *both monitors enabled* was to restart the xserver with sudo command. Then rewriting the xserver backup? ( I now have 20 or so backup xconfig files[intrepid]).  I may have messed something up in the NVIDIA  panel with the save xconfig option.

After rebooting, I would sometimes have panels back. But as soon as I would activate NVIDIA driver so I can have both monitors working, they would dissapear again.
In intrepid, my latest and easiest discovery to get panels back upon boot to a panel-less desk top is alt>F1>sysTools>sysInfo. Where NVIDIA is located. Here it opens the config panel without requiring xserver restart. 
I hope this probably meaningless scattered information will help someone knowledgible to rectify this problem. And make a boot up without having to restart anything.

I have only 3 issues with jaunty so far. 1) I still have to activate my second monitor apon boot. (I think this can be automated upon boot)?
2) Yesterday it crashed hard and wiped out my cpu frequency scaler. (Asus P5N-D mob)details currently unknown to me.
3)I haven't been able to download some apps I currently have with intrepid.
I'm sure these are all minor. And will be justified soon.
Of course, I wouldn't know a "bug" if it bit me in the behind :p 
Other than that, I'm loving Ubuntu! 

Regards,
a2z

---


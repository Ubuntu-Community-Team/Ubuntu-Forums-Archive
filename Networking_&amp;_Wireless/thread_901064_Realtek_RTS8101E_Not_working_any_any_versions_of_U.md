---
title: "Realtek RTS8101E Not working any any versions of Ubuntu"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by djdafreund on 2008-08-26
Oh man has this been driving me crazy the past few days of searching and trying. I upgraded my system and apparently has the Realtek RTl8101E network adapter on board. I've searched and got not much more then 2 pages worth of anything CLOSE to usable information, and even then, a lot of THOSE we even pointing to the same forum posts of help. I've tried Ubuntu 7.10, 8.04, and 8.10, and none of them are working using this network adapter. 
    I've already downloaded 4 different drivers both from searching and from Realtek website including r8101-1.006.00r1, r8101-1.007.00.tar, r8101-1.009.00.tar, and r8168-8.008.00.tar, and using both help of install on the forums, AND the help inside the zipped file, i'm stuck with getting no where. Either in the process of the steps i get a '* Error 2' mostly. The included instructions in the 1st step says "tar vjxf r8101-8.aaa.bb.tar.bz2" which of course won't work since the filename THEY named is not that, so of course just changing that name got past the 1st step, no problem on that note, but stupid that they don't fix that important to someone not knowing better. 
   2nd step is to do "# make clean modules" which of course i run (as note if needed) as sudo, but when i do the step after "# sudo make install", that's when i get a couple lines of progress, then the last message is an error, so i can't even do the next step "# depmod -a" since i can't even get past the "# make install". 
   I also found a supposed Ubuntu patch for this driver for use to patch kernals 2.6.24 and up ("patch <r8101-1.007.00.hardy.diff.txt") which won't work as stock doesn't have the patch module installed, so it gives me a "patch module not found" message, and can't apt-get it since i don't have an internet connection yet. Kind of a catch-22 here. I need to get a patch to get a device working that IS the device i need to get the patch. ARGHGH!!! So that's where i'm at. My Vista 64bit and x64 boot installs are working fine, so i know the adapter is working just fine. I might just buy some inexpensive known network card at work tomorrow, but i shouldn't have to add more hardware JUST to get things working with Ubuntu ("It just works"-LOL, yeah right.) I'm not that great with linux, but not a newbie either. I've been using it for about 8 months here and there, and know enough of my way around to get whatever i need done, so this is the 1st time i've actually ran into a problem with using Ubuntu in all fairness. I've got some steam games installed and Wine, and a number of my windows programs that works just fine. I love the overall speed and also all the 3d desktop effects mostly.

I really need some good help here if possible. Much appreciated for any responses. I believe in good karma.

Thanks a bunch!!! :)

---

### Post by thumper13 on 2008-08-26
Strange story. My motherboard has the identical ethernet card (onboard) and it seems to work perfectly. Installation detected it right off the hop.

Perhaps the Ubuntu found the card and named it something else? I would go to System -> Administration -> Network Tools, and under Devices check to see if there is a Ethernet Interface (eth0). My wife's computer seems to bark at the card itself, but still installs. 

Another suggestion is to try running it as a Live CD, to see if you can view web pages. That would isolate the issue to being related to purely your install or Ubuntu as a whole.

I'd also check around Google and see if there is ANY walkthroughs for installing your network card. I've been around linux a few years, and manufacturer websites still confuse me... Almost any Linux distro will do (I frequent the Fedora and Debian forums), and someone there may have the issue and a resolution for you.

Sorry I can't be of more help, but I hope I helped a little.

---

### Post by Milv8 on 2008-08-26
Hi there
i have had the same problem as described above, i followed the sticky  blacklist 8167,816x, all working fine. my internal rtl 8111/8168b onboard erthnet card has been giving me problems since the newly built pc.(Seem to be running slow on the net) the problem got worse when i loaded Ubuntu Studio the card basically stopped working. 

all is fine since i blacklist 8167,816X. check the sticky and have a read.

I love Ubuntu. 

regards
Milv8

---

### Post by djdafreund on 2008-08-26
Yeah, the system incorrectly recognizes it as a 8168 i believe, which some of the posts said is one of the problems, even as far as trying to blacklist in the process of installing the correct one. I did already try using both live cd's of 8.04 and 8.10, but same issues. 
  I will try the sticky mentioned and see if that helps out though. I will also look at a network card at work today, since i get discounts and weigh out the trouble/price of new card. Thanks for the responses. If anyone else also has any comments, please don't hesitate to post them. All help is useful to me. And thanks again.

---

### Post by tsar135 on 2008-10-19
I have the same problem. Logging in as root (through the login window not the console) seems to solve the "* Error 2" problem, i get to fully install te driver but it still won't work. Tried installing the windows driver through ndiswrapper, says it's installed but still won't work, and now i'm stuck trying to install the vista drivers...

---


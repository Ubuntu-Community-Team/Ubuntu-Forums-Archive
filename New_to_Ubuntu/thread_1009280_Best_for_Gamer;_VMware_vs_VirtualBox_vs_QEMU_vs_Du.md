---
title: "Best for Gamer; VMware vs VirtualBox vs QEMU vs Dual Boot"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Ford_Prefect2nd on 2008-12-12
Ok so I have a Inspiron 6400 aka 1501, it has a Ati x1400, 2 gigs (PC 5200) ram, 1680 x 1050 display.  I am currently dual booting Windows XP 32 and Ubuntu Ibex 64  and am willing to reinstall either, though would highly prefer not to.
   The issue; I bought the laptop with gaming in mind, but not a focus, I have Guild Wars and would not mind to also play Dark Crusade, Rise of Nations and a few other older games.  Additionally I have an iPod Touch (increasingly to my chagrin, but at least its Jailbroken) and a Nokia 5200 (which I really like the Bluetooth wireless sync function).  I have started using Ubuntu very recently and am really enjoying it, however I still have to dual boot to deal with bloody iTunes and for games and some other small things that Wine just won't do (Nokia PC Sync for one).  I would prefer to not have to reboot my pc to use Windows and the HD space used by having both OS's is a bit annoying, but with the Windows Partition mounting so nicely, I can keep Ubuntu to a smaller partition, plus a 4 gig Swap.  So what is my best option, continue dual booting, try Crossover, use VMware, Virtualbox or QEMU?  I have never ran any kind of Virtual Machine and have, as I said, very little Linux experience (tried Haron, Kubuntu, Ultimate Edition and now Ibex), but I had my OMG why don't I just use Windows moment and am now somewhat comfortable with Ibex.

---

### Post by DieB on 2008-12-12
for commercial emulators check transgaming's cedega and codeweaver's crossover games.

emulation always only has the hardware present, that your host (in this case ubuntu) is "seeing", so it might not really do the trick with the ipod, but there are some further apps in the repositories for "ipod-support".

---

### Post by Locke_99GS on 2008-12-12
Unfortunately, virtualization uses virtual hardware for the guest machine, and only a few games work well through wine. The best option for gaming is to dual boot Windows. :(

---

### Post by piousp on 2008-12-12
I'm not sure, but i think that a virtual machine wont be able to use your video card, so they wont be an option.

I guess that your best bet its gonna be an API (wine, cedega, crossover) o dualboot.

---

### Post by Ford_Prefect2nd on 2008-12-12
> **DieB said:**
> for commercial emulators check transgaming's cedega and codeweaver's crossover games.

emulation always only has the hardware present, that your host (in this case ubuntu) is "seeing", so it might not really do the trick with the ipod, but there are some further apps in the repositories for "ipod-support".

Ipod support exists but it ends at iPod Touch and iPhone as Apple locked them down even more (god I hate apple, never again), and they will not even be recognized as present, or if they are, there is little you can do, all apps I have seen so far have had no iPhone or Touch support.

---

### Post by Ford_Prefect2nd on 2008-12-12
> **Locke_99GS said:**
> Unfortunately, virtualization uses virtual hardware for the guest machine, and only a few games work well through wine. The best option for gaming is to dual boot Windows. :(

I know that Crossover Gamers or whatever does do Guild Wars, but its the other older games random things that I wonder about and my Phone sync.  Nokia actually bundled some great sync software with their phones, but no Linux support.  I have not had any luck with Wubi.

---

### Post by JKBurton on 2008-12-12
I have had excellent luck with Wine this time (8.10 32-bit), but only on my Nvidia systems with the restricted drivers. My ATI laptop will run the games, but performance is unusable (< 5 frames/sec!).

VirtualBox won't run 3D games yet. VMware 6.5 claims to, but I only had limited success with their trial. The open-source version of VirtualBox doesn't do USB devices well, but there's a closed-source version at virtualbox.org that I believe may handle your Bluetooth phone.

I wish I could be more help with the games, but the current ATI driver never seems to play well with Wine. The new releases are visibly better every month or two, but if there's a way to get decent performance out of it, I've never heard of it.

---

### Post by weezerisrock on 2008-12-12
> **JKBurton said:**
> 
I wish I could be more help with the games, but the current ATI driver never seems to play well with Wine. The new releases are visibly better every month or two, but if there's a way to get decent performance out of it, I've never heard of it.

Just to add another voice.  I use ubuntu on my laptop, which has an ati x1300 mobility on it.  I have had to configure some programs config files to best take use of it, but over all I seem to run better than its windows counterpart :S

The 8.11 drivers from ati are pretty nice as far as I'm concerned.  Still not as nice as nvidia, granted, but I have had great success with them so far.

But to answer one of the original questions, doing VM's for games = not good.  And depending on what you want to play will have an impact on whether you will want to dual boot or not.  Guild Wars is well supported by Wine as far as I know, and so are many other games.  However, if you want to be able to go into a store pick something up and install and play it, you'd be better off dual booting into windows.

---

### Post by stchman on 2008-12-12
I have had pretty good luck with WINE in gaming.  If the game gives me too much problem I reboot into XP.

Windows games are better played on a Windows machine.  The exception being games that use OpenGL like any of the Quake II, III, IV based games.  Since both the Nvidia and ATI drivers that you can install in Ubuntu have a full OpenGL capability there is usually very little problems.  

DirecX on the other hand is a different thing.  DirecX is a Microsoft proprietary API so the Windows emulators have to either use virtualization, emulation, or reverse engineering for the API so it is hit or miss.

For myself I use XP for gaming and Ubuntu for everything else.

---

### Post by Ford_Prefect2nd on 2008-12-12
> **JKBurton said:**
> I have had excellent luck with Wine this time (8.10 32-bit), but only on my Nvidia systems with the restricted drivers. My ATI laptop will run the games, but performance is unusable (< 5 frames/sec!).

VirtualBox won't run 3D games yet. VMware 6.5 claims to, but I only had limited success with their trial. The open-source version of VirtualBox doesn't do USB devices well, but there's a closed-source version at virtualbox.org that I believe may handle your Bluetooth phone.

I wish I could be more help with the games, but the current ATI driver never seems to play well with Wine. The new releases are visibly better every month or two, but if there's a way to get decent performance out of it, I've never heard of it.

Wine is nice, but gaming is acutally kinda secondary to having the ability to update my cell and the iPod.  Basically rebooting is the last choice, but also a guaranteed success, so that is where I feel stuck.

---

### Post by JKBurton on 2008-12-12
> **weezerisrock said:**
> Just to add another voice.  I use ubuntu on my laptop, which has an ati x1300 mobility on it.  I have had to configure some programs config files to best take use of it, but over all I seem to run better than its windows counterpart :S

The 8.11 drivers from ati are pretty nice as far as I'm concerned.  Still not as nice as nvidia, granted, but I have had great success with them so far.


You're getting usable fps in 3d games under Wine with that card? I'd love to be able to do that on my laptop (an X1200). Can you post one of your config files for me?  Did you do anything special with the ATI 8.11 driver after installing it, or was it just working out-of-the-box?

---

### Post by Ford_Prefect2nd on 2008-12-12
> **JKBurton said:**
> You're getting usable fps in 3d games under Wine with that card? I'd love to be able to do that on my laptop (an X1200). Can you post one of your config files for me?  Did you do anything special with the ATI 8.11 driver after installing it, or was it just working out-of-the-box?

If you tell me how to do that, I would love to do so for you.  I dont even know what my config file is.  On windows I can run Dark Crusade satisfactory with enough frames, it games pretty well, the x1400 really has done a lot for me.  Ubuntu did find drivers I think during install, I had to... um activate or something my video card after I installed.  As I said Linux and I are new bed fellows.

---

### Post by Ford_Prefect2nd on 2008-12-12
Is there any way to just run the windows install thats already there on a different partition?  Like its already there, can I just run Windows in Wine by running an exe?

---

### Post by Paqman on 2008-12-12
Dual boot is by far the best bet. Windows is a much better gaming platform than Linux, as it gets all the games released natively and the graphics drivers tend to be better.

I've only managed to get one Windows game running well through Wine (City of Heroes) but even then the graphics are slightly poorer than on Windows. I tend to just reboot and play it in Windows.

IMO, if you have a valid version of a decent version of Windows, then why not use it for your games? You'll save yourself a lot of hassle.

---

### Post by Ford_Prefect2nd on 2008-12-12
> **Paqman said:**
> Dual boot is by far the best bet. Windows is a much better gaming platform than Linux, as it gets all the games released natively and the graphics drivers tend to be better.

I've only managed to get one Windows game running well through Wine (City of Heroes) but even then the graphics are slightly poorer than on Windows. I tend to just reboot and play it in Windows.

IMO, if you have a valid version of a decent version of Windows, then why not use it for your games? You'll save yourself a lot of hassle.

I would prefer to not have the Windows install at all, save myself some disk space.  Also rebooting is a bit of an annoyance and again this is not just about gaming, the syncing my phone and the iPod are also an issue and I don't want to reboot every time I want to add an episode of TWiT to my evil little iPod.  One day Rockbox will be availible as an app or something on the iPod Touch or I will install a palm OS on it and everything will be great, but until then I have to deal with my horrid decision to return my Archos 605 for a locked down POS.  Sorry for the unrelated tangent, I jumped to Linux because windows did not allow enough customization and openness, Apple is as far beyond Windows as Windows is beyond Linux, when it comes to being locked down.

---

### Post by Paqman on 2008-12-12
For simple little things like syncing phones you could use a lightweight version of Windows in a VM. Virtualbox in Seamless Mode integrates into the desktop quite nicely, and i'm assuming if you're gaming your machine will have enough smash to run a VM and desktop apps without too much trouble. I use Google Chrome in a VM for an online risk site (which doesn't like the Linux version of Flash) and it's pretty good.

---

### Post by Ford_Prefect2nd on 2008-12-12
> **Paqman said:**
> For simple little things like syncing phones you could use a lightweight version of Windows in a VM. Virtualbox in Seamless Mode integrates into the desktop quite nicely, and i'm assuming if you're gaming your machine will have enough smash to run a VM and desktop apps without too much trouble. I use Google Chrome in a VM for an online risk site (which doesn't like the Linux version of Flash) and it's pretty good.

OOOhh Chrome, thats one I really miss in Linux.  Ram wise I could be doing better, I forgot to mention the Processor, it's a 2.16 ghz core 2 dual.  It was bought with gaming in mind, but those 2 gig of slowish ram might hurt me.
   You suggested VM, you think Virtualbox is the best way to go, given what I have said.  I guess I could leave a small XP partition in place for gaming alone (those reboots are far less common then say syncing phone and iPod).

---

### Post by Ford_Prefect2nd on 2008-12-12
Virtualbox not supporting USB kinda counts it out and I can't get Bluetooth to work, so it does not work for either purpose it seems.

---

### Post by Ford_Prefect2nd on 2008-12-12
I am looking at formatting both partitions right now.  I have not found a way to exactly what I want yet.  From what I have heard here and from the Ubuntu forums, it looks like for any real gaming I will put in a small windows partition in, maybe 15-20 gigs and then leave the rest of my 120 to linux and try virtualizing.  The issue I have is getting an ipod touch and Nokia PC Sync working, I have not got either working so far by virtualizing so far.  If I was not useing an iPod touch I could just  Rockbox, but Linux will not even recognize that i have connected the Touch and I have not been able to get Bluetooth working in virtualized Windows.  I have not yet tried VM, I guess I am asking what I am best to use.  Should I virtualize and if so with what, or should I try a Wine based App to run Nokia PC sync and iTunes and if so which one?

---

### Post by Ford_Prefect2nd on 2008-12-12
> **Paqman said:**
> For simple little things like syncing phones you could use a lightweight version of Windows in a VM. Virtualbox in Seamless Mode integrates into the desktop quite nicely, and i'm assuming if you're gaming your machine will have enough smash to run a VM and desktop apps without too much trouble. I use Google Chrome in a VM for an online risk site (which doesn't like the Linux version of Flash) and it's pretty good.

What is a "risk site" and if it helps me run Chrome, could you elaborate more, I would be very interested.

---

### Post by Paqman on 2008-12-13
> **Ford_Prefect2nd said:**
> What is a "risk site" and if it helps me run Chrome, could you elaborate more, I would be very interested.

Should have capitalised that: [Risk]("http://en.wikipedia.org/wiki/Risk_(game)")

2GB of RAM is fine for running XP in a VM. It's all I have. I just give the VM about 512MB of RAM to itself, which will run XP ok. Your second core will help out for running a VM, too.

You can use a tool like [nLite]("http://www.nliteos.com/nlite.html") to create a custom version of Windows with a lot of the rubbish (IE, MSN, etc) stripped out to make it lighter. Not quite sure how kosher this is regarding the Windows license, though. I can't see why it would be a big deal assuming you have a paid-up copy of the OS in the first place.

If you don't like Virtualbox, try VMWare Server. You'll have to go through a rather long and annoying signup process, but the actual software is free of charge (although not open source)

---

### Post by billgoldberg on 2008-12-13
> **Ford_Prefect2nd said:**
> Ok so I have a Inspiron 6400 aka 1501, it has a Ati x1400, 2 gigs (PC 5200) ram, 1680 x 1050 display.  I am currently dual booting Windows XP 32 and Ubuntu Ibex 64  and am willing to reinstall either, though would highly prefer not to.
   The issue; I bought the laptop with gaming in mind, but not a focus, I have Guild Wars and would not mind to also play Dark Crusade, Rise of Nations and a few other older games.  Additionally I have an iPod Touch (increasingly to my chagrin, but at least its Jailbroken) and a Nokia 5200 (which I really like the Bluetooth wireless sync function).  I have started using Ubuntu very recently and am really enjoying it, however I still have to dual boot to deal with bloody iTunes and for games and some other small things that Wine just won't do (Nokia PC Sync for one).  I would prefer to not have to reboot my pc to use Windows and the HD space used by having both OS's is a bit annoying, but with the Windows Partition mounting so nicely, I can keep Ubuntu to a smaller partition, plus a 4 gig Swap.  So what is my best option, continue dual booting, try Crossover, use VMware, Virtualbox or QEMU?  I have never ran any kind of Virtual Machine and have, as I said, very little Linux experience (tried Haron, Kubuntu, Ultimate Edition and now Ibex), but I had my OMG why don't I just use Windows moment and am now somewhat comfortable with Ibex.

Continue dual booting.

Using a VM to game is a no-go. And Wine doesn't run that much.

---

### Post by Ford_Prefect2nd on 2008-12-13
> **Paqman said:**
> Should have capitalised that: [Risk]("http://en.wikipedia.org/wiki/Risk_(game)")

2GB of RAM is fine for running XP in a VM. It's all I have. I just give the VM about 512MB of RAM to itself, which will run XP ok. Your second core will help out for running a VM, too.

You can use a tool like [nLite]("http://www.nliteos.com/nlite.html") to create a custom version of Windows with a lot of the rubbish (IE, MSN, etc) stripped out to make it lighter. Not quite sure how kosher this is regarding the Windows license, though. I can't see why it would be a big deal assuming you have a paid-up copy of the OS in the first place.

If you don't like Virtualbox, try VMWare Server. You'll have to go through a rather long and annoying signup process, but the actual software is free of charge (although not open source)

I feel a bit foolish of the Risk thing now, when everything sounds forgien, simple things start to get overlooked.  I have a version of Windows that adds what I want and takes out what i don't so I hope MS has not decided to call it illegal, my Dell came with a License key, so I should be able to do what I want with it.  I live in Canada, companies have less rights to pull wierd $%&$ like that here.
   I actually really liked Virtualbox, very smooth, but I need USB and bluetooth and neither seemed to work, it kept telling me to turn on my bluetooth antenna when I installed the drivers.  I guess I shall give VMware a go now.  Thanks.  Now its just a matter of if I should virtualize for everything or Wine it up for some and if I do, which version of Wine.

---

### Post by Ford_Prefect2nd on 2008-12-13
> **billgoldberg said:**
> Continue dual booting.

Using a VM to game is a no-go. And Wine doesn't run that much.

Dual booting is fine for gaming, however rebooting every time I want to sync my Phone.  This is key to me, I have memory difficulties and my laptop syncing with my iPod, syncing with my phone, all syncing with Google Cal is basically the only way I get to where I need to, if there is a break in the line its worse then having none of these devices, I could pull out my iPod, look at the Cal and say no I definitely have nothing to do today, meanwhile I wrote it down on my phone.  Only using 1 device does not work either as I often forget 1 thing, but with so many options and then it also stored online, i have had great success.  However, there is no way I am going to reboot into windows every time I update something, or even remember to, at that point it would not be worth keeping Linux.

---

### Post by CatKiller on 2008-12-13
> **Ford_Prefect2nd said:**
> Now its just a matter of if I should virtualize for everything or Wine it up for some and if I do, which version of Wine.

Well, applications in a virtual environment won't work if they need accelerated graphics, since your actual hardware is abstracted away. The games that I have run in Wine work better than when I used to run them in Windows (with the exception of Starcraft, which still runs well enough to still be enjoyable). I believe that with some of them I needed to find a crack, since the copy protection only served to stop those games running in Wine. Some games didn't work at all, and I just don't play those any more.

I did get iTunes running in Wine without any hassle, but it only made me glad that I could just nuke my ~/.wine folder to get rid of it. I don't have an iPod, so I don't know if I could have fiddled with it with the horrible iTunes.

Sorry to hear you couldn't get your peripherals working in VirtualBox. I seem to recall that there was some kind of add-on package that you could install from within the VM. I don't recall what it was supposed to do. Did you try installing that, to see if it fixed your USB and Bluetooth issues?

---

### Post by Ford_Prefect2nd on 2008-12-13
> **CatKiller said:**
> Well, applications in a virtual environment won't work if they need accelerated graphics, since your actual hardware is abstracted away. The games that I have run in Wine work better than when I used to run them in Windows (with the exception of Starcraft, which still runs well enough to still be enjoyable). I believe that with some of them I needed to find a crack, since the copy protection only served to stop those games running in Wine. Some games didn't work at all, and I just don't play those any more.

I did get iTunes running in Wine without any hassle, but it only made me glad that I could just nuke my ~/.wine folder to get rid of it. I don't have an iPod, so I don't know if I could have fiddled with it with the horrible iTunes.

Sorry to hear you couldn't get your peripherals working in VirtualBox. I seem to recall that there was some kind of add-on package that you could install from within the VM. I don't recall what it was supposed to do. Did you try installing that, to see if it fixed your USB and Bluetooth issues?

I have looked, but can not find what you speak of, I think the unpaid version of Virtualbox does not support USB, there are... other options, but I prefer to do this properly, so I am looking into VMware, though I really did enjoy the ease of which I installed Windows in Virtualbox.

---

### Post by Ford_Prefect2nd on 2008-12-13
Ok, this is a recurring problem.  I have installed VMware, but have no idea how to run it, VNC and other programs seem to disappear as well.  Do I have to run them in Terminal or... if something does not appear in the... er.. "not-start menu", then I am not certain where to look for it or how to run it.  I know this is a bit off topic, but as I say its a recurring issue and I have no idea how to run VMware as long as I have it.  I am hoping for a GUI solution, mock the Windows guy all you want, but I like me my GUI

---

### Post by CatKiller on 2008-12-13
> **Ford_Prefect2nd said:**
> I have looked, but can not find what you speak of

I recall (this was a while ago) that having installed virtualbox-ose and having installed Windows to it, that I got a prompt asking me if I wanted to install some Guest Additions. Looking at Wikipedia now, it appears that these were graphics-related in some fashion.

The proprietary version is free to use, you just can't redistribute it. You can download it from the VirtualBox site.

I've never used VMWare, so I can't tell you anything about it.

---

### Post by Cresho on 2008-12-13
I run linux native games first, then I resort to wine for my other games I own from long ago which works just fine.  The ones that don't work which are not even in wineappdb, i run in windows dualboot.  But first thing is first, I run games in linux.

CUrrent list of games..i have 10x the amount but im only posting the ones I have installed

savage2
world in conflict (works 100%) in linux
quake wars enemy territory
quake 4
doom 3
Doom3 resurrection
anachronox
ut2004
neverwinter nights 1
prey (100% working) in linux
anachronox 100%)

ill stop here because I have many more commercial cames.

---

### Post by Ford_Prefect2nd on 2008-12-13
> **CatKiller said:**
> I recall (this was a while ago) that having installed virtualbox-ose and having installed Windows to it, that I got a prompt asking me if I wanted to install some Guest Additions. Looking at Wikipedia now, it appears that these were graphics-related in some fashion.

The proprietary version is free to use, you just can't redistribute it. You can download it from the VirtualBox site.

I've never used VMWare, so I can't tell you anything about it.

I swore the closed source was not free... hmm, it does not mention it, that might work, though Bluetooth is still a maybe... can't find the install for the "closed-source edition"

---

### Post by Ford_Prefect2nd on 2008-12-13
> **Cresho said:**
> I run linux native games first, then I resort to wine for my other games I own from long ago which works just fine.  The ones that don't work which are not even in wineappdb, i run in windows dualboot.  But first thing is first, I run games in linux.

CUrrent list of games..i have 10x the amount but im only posting the ones I have installed

savage2
world in conflict (works 100%) in linux
quake wars enemy territory
quake 4
doom 3
Doom3 resurrection
anachronox
ut2004
neverwinter nights 1


prey (100% working) in linux
anachronox 100%)

ill stop here because I have many more commercial cames.

Thats a good list and sounds promising, I don't game that often, but as I said its a gaming laptop and I have guests over who will play Guild Wars (/me has a desktop gaming rig) and sometimes if I am stuck out somewhere its cool to play an rts.  If it was gaming alone I think I would just switch at this point, its the dam iPod and phone.  I am willing to look at outside the box methods. My Ipod can sync with my google calendar now without being hooked up, thanks to being jailbroken, but the phone won't do it, despite a java app installed on it to sync with Google Cal.  I am considering using a different machine just for syncing, but that would mean leaving it on and /me is carbon footprint conscious.

---

### Post by CatKiller on 2008-12-13
> **Ford_Prefect2nd said:**
> can't find the install for the "closed-source edition"

It's [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), as a .deb file. You should be able to just download it and double-click it to install it using the package manager.

---

### Post by JKBurton on 2008-12-13
> **Ford_Prefect2nd said:**
> Ok, this is a recurring problem.  I have installed VMware, but have no idea how to run it, VNC and other programs seem to disappear as well.  Do I have to run them in Terminal or... if something does not appear in the... er.. "not-start menu", then I am not certain where to look for it or how to run it.  I know this is a bit off topic, but as I say its a recurring issue and I have no idea how to run VMware as long as I have it.  I am hoping for a GUI solution, mock the Windows guy all you want, but I like me my GUI

The trial for VMware Workstation 6.5 appeared on my menu under Applications/System Tools, Ford. Wasn't obvious to me, either. I had to hunt until I found it.

Linux has potentially far more power than Windows, but to take full advantage people will tell you you need to learn the command-line. Personally I think that's fine if you want to, but not necessary anymore the way it was a couple of years back. No mocking from here, pal. If GUIs weren't faster and easier for most tasks, they'd never have taken over :)

However, while the standard Ubuntu apps are by-and-large integrated with the menu system, many of the optional apps from the Universe and Multiverse repositories are not. They can all be added to the menu, but it often isn't automatic. The easiest method I know of is to initially try from the command-line until you figure out what command you're supposed to be using. Then you right-click on your Applications menu, go into the menu editor, and add an item where you type the same command. If it doesn't work when you try it, go back and edit it again, changing the type from "Application" to "Application in Terminal".

Figuring out the command can be easy or maddening. For many it's just the name of the package. You can start VMware Workstation from the command-line by just "vmware". If you can't figure one out, just ask, preferably with the exact name of the package you installed.

The bright side is, this situation is improving FAST. The improvement from Ubuntu 7.10 to 8.10 was awesome!

---

### Post by Ford_Prefect2nd on 2008-12-13
> **CatKiller said:**
> It's [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), as a .deb file. You should be able to just download it and double-click it to install it using the package manager.

Thanks, its hard going from knowing every nuance of an OS to being a newb again, thanks all so far for all currant and future help, People were not lying about the community.

---

### Post by Ford_Prefect2nd on 2008-12-13
> **JKBurton said:**
> The trial for VMware Workstation 6.5 appeared on my menu under Applications/System Tools, Ford. Wasn't obvious to me, either. I had to hunt until I found it.

Linux has potentially far more power than Windows, but to take full advantage people will tell you you need to learn the command-line. Personally I think that's fine if you want to, but not necessary anymore the way it was a couple of years back. No mocking from here, pal. If GUIs weren't faster and easier for most tasks, they'd never have taken over :)

However, while the standard Ubuntu apps are by-and-large integrated with the menu system, many of the optional apps from the Universe and Multiverse repositories are not. They can all be added to the menu, but it often isn't automatic. The easiest method I know of is to initially try from the command-line until you figure out what command you're supposed to be using. Then you right-click on your Applications menu, go into the menu editor, and add an item where you type the same command. If it doesn't work when you try it, go back and edit it again, changing the type from "Application" to "Application in Terminal".

Figuring out the command can be easy or maddening. For many it's just the name of the package. You can start VMware Workstation from the command-line by just "vmware". If you can't figure one out, just ask, preferably with the exact name of the package you installed.

The bright side is, this situation is improving FAST. The improvement from Ubuntu 7.10 to 8.10 was awesome!

I picked up on the right click on the "start" menu recently yes, though did not know about "application in terminal" nor had I considered randomly typing things in terminal.  I guess the issue here is, say in Windows, if I install something and it is not added to the start menu, I go to program files and just double click the exe, that does not seem an option in linux, I am not even sure where the programs I install go yet, I have told my mother to just do things in Windows and if it goes wrong i will fix it and am trying to follow my own advice, but its hard from feeling like you know everything to starting over... thank you for this post, its not related at all to my original query and I was worried I would get nailed for a wrong forum question.  Though I guess everything I do at this point is absolute beginners.  
  It does not help that as I write this I am also trying to install XBMC for my home theater PC, so trouble shooting two sets of problems both on a new OS is slowing me down.  Again, cheers for the help.  

PS VMware does not appear in Start/System Tools, nor can I add it, guess its randomly typing in terminal for me then.

---


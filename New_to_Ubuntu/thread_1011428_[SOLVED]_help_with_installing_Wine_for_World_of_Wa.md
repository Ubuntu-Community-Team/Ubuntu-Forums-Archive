---
title: "[SOLVED] help with installing Wine for World of Warcraft"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by jalehtor on 2008-12-14
I am very new to this. So far, I love Ubuntu. However, my kids want (NEED) their WoW fix, and I don't know how to go about doing this on Ubuntu 8.10. I gather that I will need to install Wine first, but I don't know how to do this either.

Can anyone possibly provide me with step by step instructions for installing Wine, for starters, or tell me where to go to get such instructions? I did a search, found this thread [http://ubuntuforums.org/showthread.php?t=579378&highlight=warcraft](http://ubuntuforums.org/showthread.php?t=579378&highlight=warcraft), followed the instructions, but the instructions did not work for me, but then I was taking the instructions literally...I don't know enough yet to judge the commands on my own.

---

### Post by howefield on 2008-12-14
Load up Synaptic Package Manager, search for wine and install.

This might be worth reading as well

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by sneeks on 2008-12-14
wow runs fine under wine so u should have no problem.

---

### Post by jalehtor on 2008-12-14
OK, I got Wine installed, restarted the computer just in case, put in the first WoW disc, tried to run it, and got the message "error autorunning software, cannot find the autorun program." What am I doing wrong? :confused: Also, how do I create a "convenient" directory on my desktop as they suggest on [https://help.ubuntu.com/community/WorldofWarcraft#Original%20WoW?](https://help.ubuntu.com/community/WorldofWarcraft#Original%20WoW?) I honestly haven't a clue.

---

### Post by originalfragster on 2008-12-14
Hi jalehtor,
I recently installed ubuntu 8.10 last night and found these two pages to be invaluable. Each contains instructions about installing WINE.

[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

_**Read the instructions at both links before continuing down this Post or trying to install or configure anything. The following is just some work arounds /clarifications / pro tips**_

Make sure you run "winecfg" in ubuntus terminal window, to generate the required folders before continuing.
Also install "msttcorefont" font pack using synaptic.

**CD's**
Are you using CD's or DVD's to install WoW? If using the CD version, copy all the files from the first CD onto your desktop. Then copy ONLY the tome#.mpq files from CD's 2-5 to the same directory. Right click installer.exe and run with WINE. The game should now allow you to install. (This will allow WoW to install without having to swap CD's - and getting a mounting error)

**I have WoW installed on a windows machine**
Copy the WoW program folder to your ubuntu machine. Place it into "/home/<username>/.wine/drive_c/Program Files/World of Warcraft" (you may need to press ctrl+h to reveal hidden files in the home/<username> folder)

Be sure to finish the instructions before launching, otherwise the game will crash.

Now follow the instructions in the links provided, then you are free to roam the lands of albion in ubuntu style.

Side note: To edit WINE's registry, simply type "regedit" into ubuntus terminal.
Side note 2: You can manually create a config.wtf file in "/home/<username>/.wine/drive_c/Program Files/World of Warcraft" and then add this to it:

[I]SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "1[/I]5

This will force the game to run in OpenGL, as opposed to DirectX. (Critical to playing the game!)

Sorry if the post is somewhat vague.
enjoy, and good luck,

      originalfragster

---

### Post by jalehtor on 2008-12-14
I'm in the process of copying right now, but Jesus, it looks like it's going to take DAYS to get this thing done. It's predicting something like 10-15 hours for the initial WOW alone. Is there something wrong? Will I spend all this time waiting (presumably till the day after tomorrow, since I'll be working in the daytime, and won't be around to put in the new discs) only to find out that it was all a mistake???

Should I copy directly from Blizzard's trial site?

---

### Post by originalfragster on 2008-12-14
> **jalehtor said:**
> I'm in the process of copying right now, but Jesus, it looks like it's going to take DAYS to get this thing done. It's predicting something like 10-15 hours for the initial WOW alone. Is there something wrong? Will I spend all this time waiting (presumably till the day after tomorrow, since I'll be working in the daytime, and won't be around to put in the new discs) only to find out that it was all a mistake???

Should I copy directly from Blizzard's trial site?

Depends, blizzard have a install file available on their wesite. However that is a 4gb download, and possibly not the most feasible option available.

Original WoW installer
[http://www.worldofwarcraft.com/downloads/files/pc/wowclient-downloader.exe](http://www.worldofwarcraft.com/downloads/files/pc/wowclient-downloader.exe)

WoW - Burning Crusade
[https://www.worldofwarcraft.com/account/download/bc-clientdownload.html](https://www.worldofwarcraft.com/account/download/bc-clientdownload.html)

---

### Post by jalehtor on 2008-12-14
Thanks for that information, and 4gb sounds pretty daunting. Btw, did it take so long for you when you downloaded wow? What I have right now is ridiculous; if this is normal, I'll have to wait until next weekend, and devote the entire weekend to downloading this game! This can't be right :confused: I know that my old computer, with xp, had less memory than this one, and wow downloaded quickly enough; the thing even downloaded faster on my mom's Vista, and that was a nightmarish experience. Ubuntu, so far, has been lovely for me, so I'm wondering if I'm doing something really wrong here.

---

### Post by originalfragster on 2008-12-14
> **jalehtor said:**
> Thanks for that information, and 4gb sounds pretty daunting. Btw, did it take so long for you when you downloaded wow? What I have right now is ridiculous; if this is normal, I'll have to wait until next weekend, and devote the entire weekend to downloading this game! This can't be right :confused: I know that my old computer, with xp, had less memory than this one, and wow downloaded quickly enough; the thing even downloaded faster on my mom's Vista, and that was a nightmarish experience. Ubuntu, so far, has been lovely for me, so I'm wondering if I'm doing something really wrong here.

I originally had WoW installed on a windows XP machine. I simply copied it over to my "/home/<username>/.wine/drive_c/Program Files/World of Warcraft" Then by modifying the config.wtf file and the registry, I had WoW up and running.

---

### Post by Kennedy Bushnell on 2008-12-14
If you already have it on another computer, you can just copy it over and it will be fine. Search on Google for WoW on Ubuntu and you will find plenty of articles, they all helped me even when I had no clue about Linux. The only thing you mind have a problem with is if you have an ATI graphics card, just minor issues with OpenGL on WoW.

---

### Post by Kennedy Bushnell on 2008-12-14
If you already have it on another computer, you can just copy it over and it will be fine. Search on Google for WoW on Ubuntu and you will find plenty of articles, they all helped me even when I had no clue about Linux. The only thing you mind have a problem with is if you have an ATI graphics card, just minor issues with OpenGL on WoW.

---

### Post by jalehtor on 2008-12-15
> **originalfragster said:**
> I originally had WoW installed on a windows XP machine. I simply copied it over to my "/home/<username>/.wine/drive_c/Program Files/World of Warcraft" Then by modifying the config.wtf file and the registry, I had WoW up and running.

Fragster and Kennedy, thank you very much for the suggestion. I must confess to being an absolute idiot when it comes to computers, and teaching me to deal with them is a lot like teaching someone that 2+2=4. Should I copy what I have to a disc, and copy it onto Ubuntu, or are you  talking about some other process of which I know nothing? 

Anyhow, I'm a teacher, and I have to get up in less than six hours so I should probably snooze. If it were not for my children's most unfortunate fondness for WoW which I share--I play a huntard and a rogue to my shame--I would now be enjoying a fast, virus-free experience online without worrying about WoW.

My kid wants to play a Death Knight! Lich King is one of his (and my) Christmas presents. Help!

---

### Post by originalfragster on 2008-12-15
hi jalehtor,

imo it is best to copy WoW from the windows machine to the ubuntu machine. It will save you alot of heartache. A general WoW installation is 8gb (with patches deleted) You can try copying the game onto two dvd's. (The biggest file is about 1.4gb and theres about four of these files in the Data folder - so you can burn these to separate dvd's and copy them back over in ubuntu)

You could also borrow an external hard drive or large usb thumb drive and transfer the game using that. 

Another way would be to setup file sharing between your windows and ubuntu machine. Simply goto Start->My Network Places->Setup a home or small office network in your windows machine. You can then goto network -> windows network -> [network name] and copy from there.

Once copied, then we can proceed.

I'm actually a newb to WoW myself, only a lvl 12 priest so far

---

### Post by jalehtor on 2008-12-15
> **originalfragster said:**
> hi jalehtor,

imo it is best to copy WoW from the windows machine to the ubuntu machine. It will save you alot of heartache. A general WoW installation is 8gb (with patches deleted) You can try copying the game onto two dvd's. (The biggest file is about 1.4gb and theres about four of these files in the Data folder - so you can burn these to separate dvd's and copy them back over in ubuntu)

You could also borrow an external hard drive or large usb thumb drive and transfer the game using that. 

Another way would be to setup file sharing between your windows and ubuntu machine. Simply goto Start->My Network Places->Setup a home or small office network in your windows machine. You can then goto network -> windows network -> [network name] and copy from there.

I'm actually a newb to WoW myself, only a lvl 12 priest so far

I'm a level 66 tauren hunter, and my son is a level 40 orc hunter. If we don't get this done, he'll probably explode, bless him, and I won't be far behind ):P Anyhow, I'm going through a minor stomach bug, so I'll not be at work tomorrow. That means that in between bouts of stuff I won't specify, I'll have time to figure out what to do with these files. Damn, I wish this hadn't happened on a Sunday night. Thank you for all the help. Good night!

---

### Post by jalehtor on 2008-12-15
This is lovely, but I came down with a flu bug last night...a delight, so I'm home. I retried installing it, and this time it's moving much faster, haven't the most distant clue why, so maybe I won't have to resort to my mom's laptop, but ya never know. Knock on wood. ):Thanks for all the help. ):P

---

### Post by jalehtor on 2008-12-15
OK, I downloaded the discs, then installed them. The last few screens told me to enable Java. I had, I thought, enabled Java; checked on Firefox, and Javascript is, indeed, enabled. So the thing finished installing, and I have it on my desktop, but when I click on it, nothing whatever happens. Why is this? I have yet to download Burning Crusade, and THEN Lich king :confused: 

Help?

---

### Post by originalfragster on 2008-12-16
Dont worry, WoW wont work just yet. You will need to install the expansions and then modify a new config.wtf file, edit the registry and install an addon. This is covered here:

[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

after that, WoW will work.

---

### Post by hellawaitschrist on 2008-12-16
i have gotten past the hell of getting to the install interface of the Lich King disc.  The only problem i have is when i go to install i choose english and the 'dis/agree' box shows up.  when i "read" through it to the bottom the option of choosing "agree" does not highlight.  could this be the result of WoW telling me that my system does not meet the requirements for playing WoW?????? any advice/prob fixers is much appreciated.

---

### Post by jalehtor on 2008-12-16
> **originalfragster said:**
> Dont worry, WoW wont work just yet. You will need to install the expansions and then modify a new config.wtf file, edit the registry and install an addon. This is covered here:

[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

after that, WoW will work.


I now have a somewhat working version of WoW. I installed the discs for WoW only (I wanted to make sure the thing would work) and for some mysterious reason I ended up in Terokkar, which was, I thought, only enabled for those who have BC installed as well. Now I have BC installed on my account but not on this machine, and I haven't a clue what is going on.

There are a number of problems: the sound is awful...it echoes all over the place. Went into the interface, got rid of it. The frame rate seems a tad slower, but we can live with that. The picture, though, is awful...two dimensional rather than three, if that makes any sense, and the pixels are really obvious.

So I went to the place you mentioned (THANK YOU!!!) and all went well until I got to this:

Next, we create a registry key and value.
The following instructions to modify the registry are taken directly from the Ubuntu wiki page and is licensed under CC-BY-SA.

a. Find this key HKEY_CURRENT_USER\Software\Wine\
b. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
c. Right-click on the wine folder and select [NEW] then [KEY]
d. Replace the text New Key #1 with OpenGL
e. Right-click in the right hand pane and select [NEW] then [String Value]
f. Replace New Value #1 with DisabledExtensions (Notice it’s case sensitive!)
g. Then double click anywhere on the line, a dialog box will open.
h. In the value field type GL_ARB_vertex_buffer_object

The problem is that 

1. I don't know how to create a registry key and value
2. I don't know how to find HKEY_CURRENT_USER\Software\Wine\

This is probably so simple for most users that explaining how to get there seems insulting to their (and your) intelligence. I, however, lack computer intelligence, so I need help with this likely very simple task. 

My other question is whether or not to install BC. Is the lousy picture quality a result of the fact that it's playing BC, but is doing so without having it properly installed? 

I do apologize most profoundly for these truly stupid questions.

---

### Post by originalfragster on 2008-12-16
> **jalehtor said:**
> 
1. I don't know how to create a registry key and value
2. I don't know how to find HKEY_CURRENT_USER\Software\Wine\
I do apologize most profoundly for these truly stupid questions.

The only stupid question is the one not asked.

- I was intitally stumped by the registry thing as well, but by typing "regedit" into the terminal screen (accessories -> terminal). The registry editor for wine will show up. Then just follow the instructions. (This will give you a large fps boost)

- Im not sure how to install expansions, i would imagine that you would need to simply install the expansion as per usual. 

- Have you tried typing "winecfg" into the terminal screen, going to sound and selecting the OSHA sound drivers (And de-selecting the ALDA drivers?) This has worked for me.

- I cant help with the poor image quality sorry, all I can think of is that wine is trying to run wow with directx, as opposed to the desired openGL.

Hope this helps :KS

---

### Post by starcannon on 2008-12-16
For me the easiest way to run WoW on linux is with cedega; while this does cost $15, it does make the task nearly painless.

[http://www.cedega.com](http://www.cedega.com)

GL and have fun

---

### Post by jalehtor on 2008-12-17
> **originalfragster said:**
> The only stupid question is the one not asked.

- I was intitally stumped by the registry thing as well, but by typing "regedit" into the terminal screen (accessories -> terminal). The registry editor for wine will show up. Then just follow the instructions. (This will give you a large fps boost)

- Im not sure how to install expansions, i would imagine that you would need to simply install the expansion as per usual. 

- Have you tried typing "winecfg" into the terminal screen, going to sound and selecting the OSHA sound drivers (And de-selecting the ALDA drivers?) This has worked for me.

- I cant help with the poor image quality sorry, all I can think of is that wine is trying to run wow with directx, as opposed to the desired openGL.

Hope this helps :KS

I tried it only to discover that when I do, I get a bunch of smudgy messages. When I was at that same place yesterday, that was not happening. I'm starting to think that this is God and all the saints telling my family and me that it is time to break the WoW addiction. 

Damn. WHY is Wine all muddled up????

Btw, tried it again, and got a message that
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack


Which means I have to disturb this peaceful community yet again to figure out what that means. I feel like a complete pest and apologize in advance.

---

### Post by originalfragster on 2008-12-17
> 
Btw, tried it again, and got a message that
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack

[http://ubuntuforums.org/showthread.php?t=607558](http://ubuntuforums.org/showthread.php?t=607558)
It seems to be a compatibility issue with your sound hardware.
 
User "cogadh" recommends this:
> That "fixme" message is due to the fact that your sound card does not do hardware sound mixing and does not have a master volume control. It is not a showstopper bug, many people have that error and it shouldn't cause wine to crash. The only real way to get rid of it is to configure software sound mixing in ALSA and create a virtual master volume control device, or replace your sound card with one that can actually do hardware mixing.

The Jack "fixme" just means that you don't have the Jack library installed. It's not really required anyway unless you intend to use the Jack sound driver, but most people will want to use ALSA or OSS.

Just a note, "fixme" messages are just developer notes about items that have not been implemented or fully completed in Wine yet. They don't mean anything to a normal user, unless the particular missing feature they refer to is required by the application you are trying to run.

As for your crash/lockup, the first thing you should try is a complete uninstall and purge of Wine, then re-install it:

**sudo apt-get remove --purge wine**

sounds like your having a great time with ubuntu, wish my installation was just as eventful :)

---

### Post by jalehtor on 2008-12-18
> **originalfragster said:**
> [http://ubuntuforums.org/showthread.php?t=607558](http://ubuntuforums.org/showthread.php?t=607558)
It seems to be a compatibility issue with your sound hardware.
 
User "cogadh" recommends this:


sounds like your having a great time with ubuntu, wish my installation was just as eventful :)

Yeah, this has been a blast...not really. If it were not for WoW, I would probably not even notice these problems as minus the WoW issues, it's outperformed anything else I've had. What's humbling is that I know the problems are minor, and that someone with some skill could fix the mess in less than five minutes, while I struggle on and on and on.

It's fun! :lolflag:

---

### Post by originalfragster on 2008-12-19
So have you had any luckn so far?

---

### Post by jalehtor on 2008-12-19
> **originalfragster said:**
> So have you had any luckn so far?

Well, I think I figured out the wine configuration problem. Now that I can configure (sort of, long story) I can try and fix WoW. 

I hate to pester, but do you happen to have any suggestions with the configuration? I'm still on WoW. Since that took so long to load, I didn't want to spend a huge amount of time loading BC and Lich King. It's always possible that I'll have to reload every single thing in any case. 

My problems with WoW at the moment are: choppy movement, echoing, choppy, echoing sound, and bad visuals...almost like a three-dimensional picture drawn by an adult has turned into a two-dimensional picture redrawn by a child--very pixellated. Don't know if this makes any sense at all!

Oy. Hope you're leveling up while we're suffering here with a non-functional system ):P

---

### Post by donkyhotay on 2008-12-19
> **jalehtor said:**
> Yeah, this has been a blast...not really. If it were not for WoW, I would probably not even notice these problems as minus the WoW issues, it's outperformed anything else I've had. What's humbling is that I know the problems are minor, and that someone with some skill could fix the mess in less than five minutes, while I struggle on and on and on.

It's fun! :lolflag:

Yeah, it can be frustrating when your learning how to do all this stuff. Just remember though that for each problem you learn how to fix now is another step in learning how to not just use your computer but master it.

---

### Post by jalehtor on 2008-12-19
> **originalfragster said:**
> So have you had any luckn so far?

I totally disabled the sound on the game...no sound on the Vista anyway, so we can live with it. I also messed around with the video on the game, and now it looks much, much better. The game is still jerky, though, and sometimes it gives me motion sickness to look at it. Would you happen to know what's causing it?

---

### Post by jalehtor on 2008-12-19
> **donkyhotay said:**
> Yeah, it can be frustrating when your learning how to do all this stuff. Just remember though that for each problem you learn how to fix now is another step in learning how to not just use your computer but master it.

Microsoft is responsible for this. Had Vista worked, I wouldn't be here with Ubuntu. You're right; I'm getting the hang of it, but very, very, very, very slowly. I'm a medieval geek, not a computer geek!

Thanks for the encouragement :grin:

---

### Post by jerome1232 on 2008-12-19
> **jalehtor said:**
> I totally disabled the sound on the game...no sound on the Vista anyway, so we can live with it. I also messed around with the video on the game, and now it looks much, much better. The game is still jerky, though, and sometimes it gives me motion sickness to look at it. Would you happen to know what's causing it?

Have you tried disabling desktop effects? I know on my machine if compiz is on I get like 3 fps when it's off I'm at 50 fps.

---

### Post by jalehtor on 2008-12-19
> **jerome1232 said:**
> Have you tried disabling desktop effects? I know on my machine if compiz is on I get like 3 fps when it's off I'm at 50 fps.

I disabled the effects, and it's still jerky. However, the picture is very nice, everything works, no lag time in battles etc. Would you happen to know what the jerkiness is? Other than my own jerkiness in pestering innocent folk to get a game to work, that is?

---

### Post by jalehtor on 2008-12-20
OK, I don't know what happened. I played around with WoW interface, slept on it, then my son went on and started a Death Knight. I asked him if the jerkiness bothered him, and he said, what jerkiness? I looked at the game, and it's beautiful!!! 

What happened? Anyhow,I'm so very happy to mark this thread as solved, though I fear that it won't help anyone else who's dealing with the same problem. 

Thanks for putting up with a completely bizarre series of questions. ):P

---

### Post by originalfragster on 2008-12-23
hmm, thats weird. Glad to hear its worked out for you.

---


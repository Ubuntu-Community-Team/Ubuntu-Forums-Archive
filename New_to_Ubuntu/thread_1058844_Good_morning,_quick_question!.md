---
title: "Good morning, quick question!"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Mr_Shadetree on 2009-02-03
I have already burned my cd and began the installation process,i am passed the launguage point of choosing english, and then it went to install so i clicked on the install now,  now i am at a blck screen with a X in the middle of the screen, i have been on this x for 30 minutes just wondergin hwo long to complete this process? what kind of tiem line should i be looking to spend to complete this process? any help would be a plus at this point! Just not sure whats going on and why this is so slow of a process.

---

### Post by howefield on 2009-02-03
Is it Ubuntu you are installing ? 

15 - 20 minutes should install it on most computers, maybe a little longer on a slow machine but not much.

Did you see the progress bar at all as it installed ?

---

### Post by krzysz00 on 2009-02-03
If there's a screen with either a gray or black background with just an X on it, there may be a problem. Tell us what monitor and video card you have.

---

### Post by LeAstrale on 2009-02-03
I'm sorry to see that you have those problems. But lets try to fix it! It appears that your X server isn't loading probably. My first try would be chaning the driver to VESA instead of whatever it might have set itself to.

Please let me know if you need assistance for doing so.

/LeAstrale

---

### Post by binbash on 2009-02-03
Did you complete the install and then you saw a black etc screen OR in the middle of the installation?If second, then try with alternate CD

---

### Post by Mr_Shadetree on 2009-02-03
> **howefield said:**
> Is it Ubuntu you are installing ? 

15 - 20 minutes should install it on most computers, maybe a little longer on a slow machine but not much.

Did you see the progress bar at all as it installed ?

yes i did see the progress bar at the beginning but havent seen it in 40 minutes or so

---

### Post by Mr_Shadetree on 2009-02-03
> **krzysz00 said:**
> If there's a screen with either a gray or black background with just an X on it, there may be a problem. Tell us what monitor and video card you have.

i am using a samtron 77v monitor and i have an 'ati n424 image card, and yes i am looking at a black screen with a X right in the middle of the screen! this monitor was/is fully functional prior to starting this process of installing ubuntu, and the video card was capable of playing onlin games without a problem!

---

### Post by Mr_Shadetree on 2009-02-03
> **LeAstrale said:**
> I'm sorry to see that you have those problems. But lets try to fix it! It appears that your X server isn't loading probably. My first try would be chaning the driver to VESA instead of whatever it might have set itself to.

Please let me know if you need assistance for doing so.

/LeAstrale

i need all kinds of assistance at this point cause somethign dont seem right!

---

### Post by Mr_Shadetree on 2009-02-03
> **binbash said:**
> Did you complete the install and then you saw a black etc screen OR in the middle of the installation?If second, then try with alternate CD

im sorry but i dont have an alternate cd? do i need to get one? if so is it free and availabel for download? will this cure my problem? 
i have completed step number 2 accourdring to the unbuntupocket guide pdf file.. i have been following the pdf fiel to the t' i am on page 16 of the pdf file and completed step number 2 awaiting step number #3?? but nothing but a black screen with an x in the middle of the screen?

---

### Post by LeAstrale on 2009-02-03
What you need to do is press ctrl+alt+F1. That should bring you to a commandline interface where you can login. Go ahead and login, which should give you the normal commandline prompt. Type this:
```
sudo nano /etc/X11/xorg.conf
```

In that file you should find a place that lists your brand of graphics card and below that a line like this:

```
Driver		"the current driver in use"
```

Replace that with:
```
Driver     "vesa"
```

Then save and quit. press ctrl+alt+F7 which should bring you to the screen with the X in the middle and then try pushing ctrl+alt+backspace for restarting the x server.

/LeAstrale

---

### Post by Mr_Shadetree on 2009-02-03
> **LeAstrale said:**
> What you need to do is press ctrl+alt+F1. That should bring you to a commandline interface where you can login. Go ahead and login, which should give you the normal commandline prompt. Type this:
```
sudo nano /etc/X11/xorg.conf
```

In that file you should find a place that lists your brand of graphics card and below that a line like this:

```
Driver		"the current driver in use"
```

Replace that with:
```
Driver     "vesa"
```

Then save and quit. press ctrl+alt+F7 which should bring you to the screen with the X in the middle and then try pushing ctrl+alt+backspace for restarting the x server.

/LeAstrale

control alt f-1 isnt working? and log on? how can i log on when i am not to that point in the installation to be loggin on when i havent created the user accoutn yet? I am on page 16 of the pdf file, and step number 2 is completed, awaiting the instructions for step number #3

---

### Post by LeAstrale on 2009-02-03
ctrl+alt+F1 should give you access to tty1 (a commandline interface) From here you can log in with the user credentials created during the installation. Then you should be able to follow my former directions :) You might have to press enter 1 time to get the login prompt up on tty1.

/LeAstrale

---

### Post by Mr_Shadetree on 2009-02-03
> **LeAstrale said:**
> ctrl+alt+F1 should give you access to tty1 (a commandline interface) From here you can log in with the user credentials created during the installation. Then you should be able to follow my former directions :) You might have to press enter 1 time to get the login prompt up on tty1.

/LeAstrale

contrl, alt, f-1 isnt working, isnt changing anythign on my screen..and i have not been prompted to setup user credentials yet! i just tried to remove the disk thnking i could start all over again, and it wot open the door to eject the disk.. the prompt light just flashed 2 times? but will not eject the disk

---

### Post by Elfy on 2009-02-03
Did you check the download md5sum before you burned the cd or the integrity of the burn on the menu you get when the disc boots?

Also how much RAM do you have, I found that when it was 'close' to minimum then it could take a while to get through stages. If you don't have a lot of RAM then you could make a swap partition and then reboot - the livecd would recognise it and use it.

---

### Post by phr0ze on 2009-02-03
OK. No one asked. Did you answer the 7 install questions yet? Before it installs it asks what time zone, what language, what user name, what password, what partition etc.

If you didn't do that, then you are just having problems booting the CD. The alternate CD may help. Its free and available from the same ubuntu.com download page.

The other choice is when the CD first boots there are some choices at the bottom of the screen for video modes. Try those too.

---

### Post by Mr_Shadetree on 2009-02-03
> **forestpixie said:**
> Did you check the download md5sum before you burned the cd or the integrity of the burn on the menu you get when the disc boots?

Also how much RAM do you have, I found that when it was 'close' to minimum then it could take a while to get through stages. If you don't have a lot of RAM then you could make a swap partition and then reboot - the livecd would recognise it and use it.

when i burned the cd, i got the proccess fully fixated message at the end of the burn, indicating that the burn was successful, i have 448 ram in this machine, at this point i have now powered down and restarted then removed the install cd, and thats what point i am at right now! i am going to reattempt the install again, assuming maybe i missed somehtign during the install since it appears i have notfollowed instructions and missed the part where i was suppose to of created user credentials!

---

### Post by Mr_Shadetree on 2009-02-03
> **phr0ze said:**
> OK. No one asked. Did you answer the 7 install questions yet? Before it installs it asks what time zone, what language, what user name, what password, what partition etc.

If you didn't do that, then you are just having problems booting the CD. The alternate CD may help. Its free and available from the same ubuntu.com download page.

The other choice is when the CD first boots there are some choices at the bottom of the screen for video modes. Try those too.

no sir i have not reached that point of the install yet where i am asked the questions you are speaking of!

---

### Post by Mr_Shadetree on 2009-02-03
i have now reinstalled the disk again, and i have selcted the language, then at main menu where i am asked to install or check integrity iam checking integrity now keep you posted..

---

### Post by Mr_Shadetree on 2009-02-03
> **Mr_Shadetree said:**
> i have now reinstalled the disk again, and i have selcted the language, then at main menu where i am asked to install or check integrity iam checking integrity now keep you posted..

just finished integrity check and no errors found on the disk!

---

### Post by Mr_Shadetree on 2009-02-03
> **Mr_Shadetree said:**
> just finished integrity check and no errors found on the disk!

i am now testing memory keep you posted!

---

### Post by Mr_Shadetree on 2009-02-03
> **Mr_Shadetree said:**
> i am now testing memory keep you posted!

50% currently pass all of tests thus far!

---

### Post by Mr_Shadetree on 2009-02-03
> **Mr_Shadetree said:**
> 50% currently pass all of tests thus far!

100% pass complete no errors..... on the memory test... next step?

---

### Post by HavocXphere on 2009-02-03
Right at the start keep hitting F4 until it gives you an option to use Safe Graphics. Its somewhere round about the time where you select the language. Had a similar problem...minus the X.

---

### Post by Mr_Shadetree on 2009-02-03
> **HavocXphere said:**
> Right at the start keep hitting F4 until it gives you an option to use Safe Graphics. Its somewhere round about the time where you select the language. Had a similar problem...minus the X.

not questioning you just questioning instructions, why am i doing this? you didnt give any follow up instructions?

---

### Post by Mr_Shadetree on 2009-02-03
ok no respoonce so going to attept to reinstall again. 1048 am install began again! immediatly  x in the center of a black screen.

---

### Post by Mr_Shadetree on 2009-02-03
> **Mr_Shadetree said:**
> ok no respoonce so going to attept to reinstall again. 1048 am install began again! immediatly  x in the center of a black screen.

can i assume somethign is still not right sinc ei dint get asked the 7 questions spoken of earlier?

---

### Post by Elfy on 2009-02-03
Hi - lets just slow down a bit here - 
> 
I am on page 16 of the pdf file, and step number 2 is completed, awaiting the instructions for step number #3 where is this located -= so we can see where you think you've got to in the process

> not questioning you just questioning instructions, why am i doing this? you didnt give any follow up instructions?Did you try this? You need to try to use the safe graphics mode - it's on eof the options - possibly F6 - all these options are at the bottom of the boot screen when the livecd starts.

---

### Post by HavocXphere on 2009-02-03
> **Mr_Shadetree said:**
> not questioning you just questioning instructions, why am i doing this? you didnt give any follow up instructions?
When kubuntu starts, it tries to find a driver to works for your graphics setup. If the one it picks doesn't work then you're stuck without working graphics. By selecting F4, it reverts to the Vesa drivers, which are old-school, but fairly bulletproof. Once you are done installing, then you can grab up-to-date proper graphics for your gfx card.

I'm not saying that is your problem...but its easy to find out.

---

### Post by snowpine on 2009-02-03
Are you sure you have enough ram? 

Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution

---

### Post by Mr_Shadetree on 2009-02-03
> **forestpixie said:**
> Hi - lets just slow down a bit here - 
 where is this located -= so we can see where you think you've got to in the process

Did you try this? You need to try to use the safe graphics mode - it's on eof the options - possibly F6 - all these options are at the bottom of the boot screen when the livecd starts.

i have been getting all my instructions from the unbuntu pocket guide manual, sorry not able to locate the link right this second, but the pocket guide is offered through this website, thats where all this started from this website... i am on page 16 about a third of the way down on the page where it lists th einstructions:
1. Insert the Ubuntu CD and reboot your computer. At the BIOS
startup screen, look for the keypress option that brings up the
boot device menu. Exactly what this is varies from computer to
computer. On many computers you’ll need to hit the Esc key, or
F12. Select the CD/DVD-ROM drive from the menu when it
appears. If there’s no option for bringing up the boot device
menu, enter BIOS setup by hitting the relevant key (usually
Delete). Then configure the CD/DVD-ROM drive as the first
boot device. Again, how this is done varies from PC to PC.
2. When the computer boots from the CD, the Ubuntu CD-ROM
boot menu will appear. Using the up/down cursor keys, select
your preferred language from the list and hit Enter. Then
highlight the Install Ubuntu option on the main menu using the
cursor keys and hit Enter.
3. Eventually the Ubuntu installation program window will appear,
as shown in Figure 1-1. Work your way through the choices, such
as entering your location and language choices, clicking the
FORWARD button to move on each time. 
OK SORRY DUE TO ME INCREASING THE MAGNIFICATION IT SHOWS AS BEING ON PAGE 16 BUT WHEN IN REGULAR NON MAGNIFIED LISTING IT IS ON PAGE 10 NOT PAGE 16 SORRY, I HAD TO MAGNIFY THE PAGE TO READ THE TEXT

---

### Post by Mr_Shadetree on 2009-02-03
[QUOTE Did you try this? You need to try to use the safe graphics mode - it's on eof the options - possibly F6 - all these options are at the bottom of the boot screen when the lived starts.[/QUOTE]

NO I didnt try this as i didnt have follow up instructions, all that was suggested to do was click on f-4 repeatedly? not reboot after making the nessarary adjustments while under f-4! i will try to reboot now with the adjustments made to the f-4 option

---

### Post by Mr_Shadetree on 2009-02-03
> **snowpine said:**
> Are you sure you have enough ram? 

Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution

 Re: Good morning, quick question!
Quote:
Originally Posted by Mr_Shadetree View Post
50% currently pass all of tests thus far!
100% pass complete no errors..... on the memory test.

---

### Post by Elfy on 2009-02-03
448MB RAM - earlier in the thread which is why I ignored it - should certainly be enough.

To use the safe graphics - when you boot with the cd you get a languauge choice - after that you are presented with the boot menu - at the bottom are various option reached with F keys - one of them is safe graphics I think - maybe F6 - but you might need to F4 for options.

---

### Post by Mr_Shadetree on 2009-02-03
after doign the f-4 function 'safe graphics mode' then attempting to reinstall again(7th time) 35 minutes of installing (or so i guess it is actually installing) still nothing no 7 questions as previously mentioned! I have done the check disk for defects no defects, i have doen the meemroy check and assed that test successfully, i have a good copy of the dick to be burnign why aint this thing installing? this is crazy 24 hrs trying to install this and still nothing! the only hope that this thing might work is i am actually seeing the initial installation bar scrolling across the screen for the first few minutes then i get the black screen with 'x' in the middle of the screen!

---

### Post by Mr_Shadetree on 2009-02-03
as soon as i boot from cd, i get the option to choose my launguage, then i get a screen with the kubuntu logo, and 5 options:1. trykubuntu without any changes to your pc 
2. install kubuntu
3. check cd fr defects
4. test memory
5. boot from first hard disk

then i am presnted with the f-1, f-2, f-3, f-4, f-5, f-6 options where i went in f-4 and changed the option to 'safe graphics mode, and another 20 minutes again and still nothign abou tno 7 more questions to answer??? it just goes to the black screen witht e 'x' in the middle of the screen? has no one ever had aproblem liek this reported before? i have done a search in this sit, and i am not finding anythign on this nature of a install problem? 

this is already the third copy of this install I have burned, and every copy was burned and fixated properly, using the infrarecorder as suggested by the kubuntu website.

What am i missing here? This makes no sence to me!!!

---

### Post by Elfy on 2009-02-03
I would look to getting the alternate as suggested earlier by binbash.

Yes others have had similar problems - it is most probably a combination of video and RAM - if for instance you have shared video memory then it's possible that there's not enough memory for the livecd to run.

Another way to do it is to use a live partition editor such as gparted to create a swap partition such as [partedmagic]("http://partedmagic.com/") if it is a RAM issue.

Download, burn as iso and boot with it, use it to resize and create swap partition.

One more thing you say you checked the burn but did you check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")? Hashes are [here]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by Mr_Shadetree on 2009-02-03
ok folks i have reburned a new copy of the Kubuntu alternate, and it is installing right now, i have already answered all 7 questions, i have created user accoutn name, and doen the geographical location, and time stamp information..... the install current position is :installing the base system, at installing extra packages...

---

### Post by raydeen on 2009-02-03
Not sure if this link covers things you've already tried:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I'm wondering if there's a problem with booting with ACPI on? You may need to modify your initial boot with either acpi=off or noacpi. There may be something funky with your BIOS or power management that's preventing the OS from loading. 

The other thing to try is to burn the alternative CD

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

This does a terminal only install which you can then add your desktop of choice to afterwards. In your case I think you would type

```

sudo apt-get install kubuntu-desktop

```

after you've finished installing. This will do some more downloading but after you reboot you'll get the Kubuntu desktop. I had to do this on an old Apple G4 that just didn't have the guts to run the live CD. Took a little extra time but it worked find.

---

### Post by Mr_Shadetree on 2009-02-03
ok folks, i am jammed again? I am at a screen that says: [select and install software] then below that it shows a percentage line with 1% filled in, then below that it says [configure language-pack-en-base] got any ideas?
 no longer jammed, it finally proceeded, forward up to 6% of installing software

---

### Post by Mr_Shadetree on 2009-02-03
since i am installing using the alternate iso/ what am i going to be missing from my computer that i will have to pickup later? I do understand i am missing somethings but after many multiple searches i have yet to of found a diction as to what i will be missing that i will need to install after i get online! 

Folks i am sorry to be a pain in the butt, i know that sometimes its better to just go to bed, and forget about it.... but that's hard to do when i am on a mission so after  34 hrs straight i do tend to get a little aggravated, and i apologize for my aggravation if taken out on any of you folks, as i do greatly appreciate every ones help that has contributed... to assisting me with the installation of Kubuntu, on this doner, pc i am donating to my neighbor!

---

### Post by Mr_Shadetree on 2009-02-03
currently at 59% latest update!

---

### Post by Elfy on 2009-02-03
Not sure that you'll actually need to install anything once it's installed.

It should just boot into the system for you once it's finished and you've rebooted without the cd.

There is a whole lot of information here specifically about the alternate install
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) some of it is about using the livecd so pick the right bits.

---

### Post by raydeen on 2009-02-03
You really won't be missing anything except a GUI (desktop). The OS will drop you to a terminal prompt. See my previous post for installing a desktop after everything is installed. for KDE

```

sudo apt-get install kubuntu-desktop

```

For Gnome

```

sudo apt-get install ubuntu-desktop

```

There are a number of desktop environments you can install and switch between when you log in. It's still Ubuntu under the hood, it's just putting a different body and paint job on top of it. :) Depending on how your machine performs you could try 

```

sudo apt-get install xubuntu-desktop

```

This is a very lightweight desktop using Fluxbox. If your machine seems sluggish under Gnome or KDE it should run much faster with Xubuntu.

Install as many as you have HD space for and experiment. You'll just choose which one you want to use by choosing the Session at login.

---

### Post by LeAstrale on 2009-02-04
Please ignore raydeen, there are obvious errors in his post. Installing from an alternate installer disc gives you the same as the desktop disc except that the installation is done without a GUI. The alternate install however requires alot less ram due to the fact that it doesn't run the Operating system live from the CD while you're installing.

Please don't do multiple posts after one another, keep it simple and edit your early post if new info has arrived and your post is the last one.

/LeAstrale

---

### Post by sstusick on 2009-02-04
> **raydeen said:**
> ```

sudo apt-get install xubuntu-desktop

```

This is a very lightweight desktop using Fluxbox. If your machine seems sluggish under Gnome or KDE it should run much faster with Xubuntu.
I wasn't aware that Xubuntu contained Fluxbox. I always thought it was XFCE. I guess you learn something new everyday.

---

### Post by Elfy on 2009-02-04
> **sstusick said:**
> I wasn't aware that Xubuntu contained Fluxbox. I always thought it was XFCE. I guess you learn something new everyday.

You're right - you'd need to install fluxbox.

---

### Post by nothingspecial on 2009-02-04
I`ve seen this exact problem. The simple fact is you don`t have enough memory. My sugesstion would be to install xubuntu until you add more memory.

If you wish to try Ubuntu afterwards use [[COLOR="Magenta"]these[/COLOR]]("http://www.psychocats.net/ubuntu/puregnome") instructions to remove the xubuntu desktop environment. Then ```
sudo apt-get install ubuntu-desktop 
``` to replace it with Ubuntu.

---

### Post by raydeen on 2009-02-04
Sorry if my posts had inaccurate info. I recalled that the alternate CD didn't come with a GUI. It's been a few years since I used the alt CD. If it was bad info, then please do ignore. I must admit I'm not the brightest bulb right now. Broke my ankle last week and the oxycodone pain killers sort of makes my brains mush.

And Xubuntu is XFCE. I'm thinking of Fluxbuntu. I really shouldn't be posting I guess.

---

### Post by Mr_Shadetree on 2009-02-04
> **nothingspecial said:**
> I`ve seen this exact problem. The simple fact is you don`t have enough memory. My sugesstion would be to install xubuntu until you add more memory.

If you wish to try Ubuntu afterwards use [[COLOR="Magenta"]these[/COLOR]]("http://www.psychocats.net/ubuntu/puregnome") instructions to remove the xubuntu desktop environment. Then ```
sudo apt-get install ubuntu-desktop 
``` to replace it with Ubuntu.

Yes sir i do have enough memory you must have missed the message on page 3 stating that I have installed 1-gig of ram, and on page 4 i was able to get Kubuntu to fully install the alternate  and is fully functional now! 

Now i am in the position of getting all the other addons done first being wireless internet to begin.... from thei ri will be able to see and do alot more I am naked without internet connnection at the momment!

---

### Post by Mr_Shadetree on 2009-02-04
[QUOTE=LeAstrale;Please don't do multiple posts after one another, keep it simple and edit your early post if new info has arrived and your post is the last one.

/LeAstrale[/QUOTE]

sorry for mutlple posts I am not here looking for poster of the week award... so my apologies! I am here looking to resolve my issues, The multiple posts were mostly to keep everyone upto date as to whats going on and why, So my apologies!!

Newest of issues now i am now trying to install the my cd into cdrom to install wireless connections for linksys 2.4 ghz 802.11g, now i have installed the cd a 1000 times and all it does iis insert the disk but thier is nothing commanding it to run? what i have i not learned during the last four days that i am not able to command this o/s to read a cd in the cdrom?

---

### Post by raydeen on 2009-02-04
You probably have a CD that was designed to work with Windows and as such won't do anything when you stick it into the drive. You may see an icon on your desktop that you'll be able to click on and browse but you won't be able to 'run' any programs off of it by default. Below is a link that should get you started in finding out first what wireless device you have and possibly how to get it working.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If you can run the very first command, it may give others here some info that will get you on your way more speedily.

---

### Post by LeAstrale on 2009-02-05
Please create a new thread for a seperate problem and mark this one solved :)
That will help you get attention from the right people. Meaning that the people who haev helped you here might not know anything about wireless network adapters.

/LeAstrale

---

### Post by Mr_Shadetree on 2009-02-05
> **LeAstrale said:**
> Please create a new thread for a seperate problem and mark this one solved :)
That will help you get attention from the right people. Meaning that the people who haev helped you here might not know anything about wireless network adapters.

/LeAstrale

WOW well thank you! I had no idea how these things work as i dont visit Forums regular! Again not here for post or thread counts.... O dotn care about that junk, just here to get a o/s working...

[SIZE="5"]Problem solved! Kubuntu O/S Installed![/SIZE]

---


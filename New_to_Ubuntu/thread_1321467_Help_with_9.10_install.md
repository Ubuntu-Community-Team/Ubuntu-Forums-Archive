---
title: "Help with 9.10 install"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by andygait on 2009-11-10
Hello all. 
I've tried to use 9.10 via the wubi and the live CD but whenever I try my mouse and keyboard will not work. My keyboard will work through the bios screen and the intro screen to allow me to pick the live CD option but after that nothing. 
I have tried my Microsoft wireless and a PS2 keyboard and also a wireless, USB and a PS2 mouse. Nothing works. 
 
I'm a bit of thicko when it comes to Linux (I've used Puppy on an old crappy laptop, and not with any great success), so any help with this would be great. 
 
My PC is running Windows 7 RC (64 bit), 2 GB RAM and a 2.6GHz intell Core Duo processor
 
Many thanks
Andy

---

### Post by geoffree on 2009-11-10
People seem to have problems with the wubi installer.  Have you tried using an alternate? Not knowing what options you had, I can't recommend one, but how about the standard one?  Hope this helps.  Keep trying.  On the other hand, have you checked out SuSE 11.1? Very stable and pretty.

Geoffree

---

### Post by yanceypd on 2009-11-10
Make sure you defrag the Win7 before an install.  Install from live cd.  When you get to the partioning section of install move the slider to set partition size in a side by side setup or select use whole disk if you have a spare drive.  That seems to work smoothest.

---

### Post by andygait on 2009-11-10
Thank you both for the replies. 
 
I have installed a second hard drive and have tried to install to that.  The disc loads and I get to the page 1 of 6 to start the install but I can't fill in any info as the keyboard and mouse will not work. 
 
Where am I going wrong?

---

### Post by QIII on 2009-11-10
First guess (and purely a guess!):  Did you check the md5sum and also select the "Check disk for errors" option from the LiveCD?

---

### Post by andygait on 2009-11-10
Thanks.
 
Yes, I checked the disc for errors, but what's the md5sum?
 
Do you think it would make any difference if I tried 9.4 instead?

---

### Post by andygait on 2009-11-11
Right, I've now tried to install 9.4 and it still won't work. This time it doesn't even load. I put the disc in and it starts but then just sits there doing nothing for hours. 
My PC is an Acer Aspire M1640.

---

### Post by hansdown on 2009-11-11
Hi andygait.

My box is identical to yours, and 9.04 runs very well.

The few times that this problem happened to my computer, the problem was a bad install disk.

The disk needs to be burned at the slowest speed possible.

Just to recap:
              Burn disk at slowest possible speed.
              Defrag the windows at least once. Twice is better.

Welcome to the forum andygait.

---

### Post by drsubhadip on 2009-11-11
well i ve also same kind of problem with 9.04 but now it is running 9.10...with wubi..in the win dhus 7...
so i guess it is working for me..
 one thing more that the sound in my system is great with the ubuntu than windows ..my box is alteclansing 4121

---

### Post by andygait on 2009-11-11
> **hansdown said:**
> Hi andygait.
 
My box is identical to yours, and 9.04 runs very well.
 
The few times that this problem happened to my computer, the problem was a bad install disk.
 
The disk needs to be burned at the slowest speed possible.
 
Just to recap:
Burn disk at slowest possible speed.
Defrag the windows at least once. Twice is better.
 
Welcome to the forum andygait.
 
Thanks for the reply. 
 
OK, I've burned a new disc at 4x, slowest I could get. I've run a defrag but still no joy. 
 
Do I need to alter anything in the BIOS to get this to run?

---

### Post by hansdown on 2009-11-11
The only thing needed, is to insert the disk, close it out, and restart the computer.

When the acer screen starts, hold F12 to get to the boot menu.

Change the boot to CD/DVD.

Hit enter.

---

### Post by andygait on 2009-11-12
Done that many, many times. It will not work. 
 
It gets to the welcome screen 1of 6 and then that's it. It won't let me move the mouse or use the keyboard to pick any options.

---

### Post by hansdown on 2009-11-12
That is strange.

Ive started googling for more info, but it has to wait until after work.

So far, I'm looking here, but haven't gotten very far.

[http://www.google.ca/search?q=ubuntu+9.04+install+freezes+keyboard+and+mouse&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ubuntu+9.04+install+freezes+keyboard+and+mouse&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I did see something suggesting to use a wired keyboard and mouse to get through the install.

One other thing; When the installer starts, there are options to;

"try ubuntu with no changes to your computer", and "install ubuntu".

Both lead to the same goal, so try the one you haven't used.

I know it's frustrating, but someone will be able to help.

---

### Post by theozzlives on 2009-11-12
Even though Karmic seems a bit flaky at this time, Jaunty is pretty stable. A Jaunty install should work without problems. Are you using CD-RW by any chance?

---

### Post by andygait on 2009-11-12
> **hansdown said:**
> That is strange.
 
Ive started googling for more info, but it has to wait until after work.
 
So far, I'm looking here, but haven't gotten very far.
 
[http://www.google.ca/search?q=ubuntu+9.04+install+freezes+keyboard+and+mouse&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ubuntu+9.04+install+freezes+keyboard+and+mouse&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
 
I did see something suggesting to use a wired keyboard and mouse to get through the install.
 
One other thing; When the installer starts, there are options to;
 
"try ubuntu with no changes to your computer", and "install ubuntu".
 
Both lead to the same goal, so try the one you haven't used.
 
I know it's frustrating, but someone will be able to help.
 
 
I've tried "try ubuntu with no changes to your computer, and install ubuntu" but no joy. It gets to the desktop screen but then it's the same issue with not being able to use the keyboard or mouse. 
 
 
> **theozzlives said:**
> Even though Karmic seems a bit flaky at this time, Jaunty is pretty stable. A Jaunty install should work without problems. Are you using CD-RW by any chance?
 
Tried this too. Same thing happens. 
 
And it's a CD-R disc.

---

### Post by andygait on 2009-11-12
Thought I'd try a different distro, gnewsense. same thing again. ](*,) ](*,) ](*,)
 
Getting very fed up now and thinking about not bothering. 
 
Thanks to all who have tried to help.

---

### Post by whitey_1 on 2009-11-12
> **andygait said:**
> Thought I'd try a different distro, gnewsense. same thing again. ](*,) ](*,) ](*,)
 
Getting very fed up now and thinking about not bothering. 
 
Thanks to all who have tried to help.

Look on the bright side, you got further than i have, and ive been trying for nearly 4 days!!

But the members of this forum are very helpful.

Keep going, i hear it is a very good product!

---

### Post by ranch hand on 2009-11-12
I think that to make this easier you need to check the md5 sum;

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Lets find out if your image is good.  This is different than if your disc is good.

---

### Post by andygait on 2009-11-12
> **ranch hand said:**
> I think that to make this easier you need to check the md5 sum;
 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
Lets find out if your image is good. This is different than if your disc is good.
 
 
Done that with both the 9.4 and the 9.10 that I tried to install. Both are OK.

---

### Post by ranch hand on 2009-11-12
Ah, good.  Now we know that is not the problem.

Are wired keyboard and mouse possible?

I am wired.

I always use R-W and have no trouble with it.  I do not remember any problems of this nature in 9.10 testing.  We had a few that would not boot.  But if they booted, they worked.

---

### Post by SteveHillier on 2009-11-12
> **yanceypd said:**
> Make sure you defrag the Win7 before an install.  

I think Win7 like Vista automatically defrags as it goes along (or at least once a day when you boot up which is a pain in the proverbial) but good advice just to make sure.

---

### Post by SteveHillier on 2009-11-12
> **andygait said:**
> I have installed a second hard drive and have tried to install to that.  The disc loads and I get to the page 1 of 6 to start the install but I can't fill in any info as the keyboard and mouse will not work. 
 
Where am I going wrong?

This may be a very stupid question of maybe not. Are you using PS/2 mouse and keyboard?  Are you using USB mouse and keyboard?  Are you using KVM switch or anything like that?
I hear, but have not tested, that Linux is twitchy using KVM.

Sorry had not read fully.  An aspire is laptop right?  So my comments above are academic only but I will leave them for the next person who searches the forum.  I do remember in the past having a laptop behave like this but cannot remember what I did to get out of it or which release I was installing.

---

### Post by RJ12 on 2009-11-12
Look in the BIOS is there a option with USB Legacy Support? is it on if so turn it off. if its off try turning it on.

---

### Post by hansdown on 2009-11-12
> **RJ12 said:**
> Look in the BIOS is there a option with USB Legacy Support? is it on if so turn it off. if its off try turning it on.

No option in bios.

andygait, if you like, I can post screenshots of my bios settings.

1: power management setup.

2: pci/pnp configuration.

Sorry for the quality.

---

### Post by andygait on 2009-11-13
> **ranch hand said:**
> Ah, good. Now we know that is not the problem.
 
Are wired keyboard and mouse possible?
 
I am wired.
 
I always use R-W and have no trouble with it. I do not remember any problems of this nature in 9.10 testing. We had a few that would not boot. But if they booted, they worked.
 
 
At the moment the keyboard is PS2 and the mouse is USB. I was hoping to use my wireless keyboard/mouse after install. 
 
 
> **SteveHillier said:**
> This may be a very stupid question of maybe not. Are you using PS/2 mouse and keyboard? Are you using USB mouse and keyboard? Are you using KVM switch or anything like that?
I hear, but have not tested, that Linux is twitchy using KVM.
 
Sorry had not read fully. An aspire is laptop right? So my comments above are academic only but I will leave them for the next person who searches the forum. I do remember in the past having a laptop behave like this but cannot remember what I did to get out of it or which release I was installing.
 
I have no idea what a KVM switch is, so I can't answer that one. 
 
The PC is a desktop. Acer Aspire M1640
 
> **hansdown said:**
> No option in bios.
 
andygait, if you like, I can post screenshots of my bios settings.
 
1: power management setup.
 
2: pci/pnp configuration.
 
Sorry for the quality.
 
Thanks. I'll check that against mine later on today. 
 
 
many thanks to all for your help.

---

### Post by SteveHillier on 2009-11-13
> **andygait said:**
> I have no idea what a KVM switch is, so I can't answer that one. 

Keyboard, Video, Mouse switch.  Allows you to use a number of computers using the same keyboard, mouse and monitor.
I have come across a few machines that will accept input from wireless Keyb/mouse but a number do not.  I always try to use PS/2 connectors if they are available.
I do see a point rapidly approaching when PS/2 connectors won't exist - until then...

---

### Post by andygait on 2009-11-14
> **hansdown said:**
> No option in bios.
 
andygait, if you like, I can post screenshots of my bios settings.
 
1: power management setup.
 
2: pci/pnp configuration.
 
Sorry for the quality.
 
 
Ok, done this now. All is the same as yours except for in PCI/PNP config. I have Palette Snooping **disabled**.
 
Could this be the problem? And if I change it what will this do to Windows, as I want to duel boot?

---

### Post by hansdown on 2009-11-14
This explains it better than I can.

[http://www.computerhope.com/issues/ch000935.htm](http://www.computerhope.com/issues/ch000935.htm)

Although we have the same computer, you may have audio or video cards added, that don't require pallet snooping.(I'm using the onboard video and  audio that came with mine).

The best advice given in this thread, was the MD5 SUM check.

Some other things I've see from googling are, audio and video cards causing this problem. 

I'm glad you're still giving it a go andygait. It should be a lot easier.

I'll post a screenshot of my 1: product info.
                             2:standard cmos features.
                             3:advanced bios features.
                             4:advanced chipset features.

---

### Post by andygait on 2009-11-14
> **hansdown said:**
> This explains it better than I can.
 
[http://www.computerhope.com/issues/ch000935.htm](http://www.computerhope.com/issues/ch000935.htm)
 
Although we have the same computer, you may have audio or video cards added, that don't require pallet snooping**.(I'm using the onboard video and audio that came with mine).**
 
The best advice given in this thread, was the MD5 SUM check.
 
Some other things I've see from googling are, audio and video cards causing this problem. 
 
I'm glad you're still giving it a go andygait. It should be a lot easier.
 
I'll post a screenshot of my 1: product info.
2:standard cmos features.
3:advanced bios features.
4:advanced chipset features.
 
 
I'm using the same cards that came with it. The only hardware I've changed is adding another hard drive, but I had this problem before doing that.

---

### Post by hansdown on 2009-11-14
Do the other screenshots compare with your setup?

I hesitate to suggest enabling pallet snoop.It may be worth a try.You can set it back if it doesn't help.

---

### Post by SteveHillier on 2009-11-15
hansdown & andygait.
Are you both running the same BIOS version?

---

### Post by hansdown on 2009-11-15
Hi SteveHillier.

That is what I'm wondering.

This is mine.

---

### Post by andygait on 2009-11-17
Here's a pic of the screen. (sorry if it's big. Done in a rush) [IMG]http://i746.photobucket.com/albums/xx109/Andys-pics/Photo-0021.jpg[/IMG]

---

### Post by hansdown on 2009-11-17
The difference that sticks out, is the system bios id.

---

### Post by andygait on 2009-11-17
Which means what? 
 
Sorry if I'm being thick. :D

---

### Post by hansdown on 2009-11-17
I don't think there is any difference.

---

### Post by hansdown on 2009-11-17
Any and all advice would be appreciated.

---

### Post by ranch hand on 2009-11-17
Have you tried the Alternate Install CD?

A lot of people with some problem or other seem to do well with that.

---

### Post by telovin on 2009-11-18
hi Andy,
try the options whenu get to loadthe live cd, u'll see ubuntu try live cd witthout any change.
on that screen on the right hand corner, do u see f6?go to that and try change acpioff or in the boot options try usplash instead of splash..I had a problem getting a box saying saying input not support and when i tried these, i was able to load from  live cd without any problems..

---

### Post by arnab_das on 2009-11-18
see if this helps:

[http://thoughtsndreams.wordpress.com/2009/11/17/install-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/17/install-ubuntu/)

---

### Post by SteveHillier on 2009-11-18
> **hansdown said:**
> I don't think there is any difference.

Raincheck on this.

Hansdown - your main board ID is MCP73
Andygait - your main board ID is MCP73VE

I don't know the subtleties of the difference.  Is it chipset?  Is it some other device?

The point andygait is that there is something coming in between your hardware and the application that installs Ubuntu.

If you have done the obvious like running from PS/2 devices which have to be present on restart then the something that is getting in between is the BIOS.  If there are chipset differences etc then there COULD be a difference in the BIOS the makes a difference.

Running USB mouse & Keyboard on a motherboard with PS/2 connectors normally (but not always) requires a system level higher than BIOS (ie an OS) in order to detect and run the device.  Ditto with wireless Keyboard / Mouse.

If your mother board does not have PS/2 connectors for either mouse or keyboard (and a number now don't) then the BIOS will contain the relevant code to detect and use the USB versions of these devices.

I hope I have used enough caveats to prevent the hoards from chasing after me.

---

### Post by hansdown on 2009-11-18
Yes  SteveHillier.

There is a major difference between these two. Thanks for that.

When I search MCP73, it spits out basic facts like the screenshot below.

When I search MCP73VE, the results are a bit...crazier.

[http://www.google.ca/search?q=MCP73VE&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=MCP73VE&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I also second ranch hand on the alternate CD.

---

### Post by andygait on 2009-11-20
[SIZE=2]Thank you one and all for your help. It has been very much appreciated. Hansdown, I know you have put a lot of effort into this. Thank you again. [/SIZE]
[SIZE=2]I will try the f6 suggestion and if that doesn’t work I’ll download the [COLOR=black][FONT=Verdana]Alternate Install CD. [/FONT][/COLOR][/SIZE]
 
[COLOR=black][FONT=Verdana][SIZE=2]Many thanks again. [/SIZE][/FONT][/COLOR]

---

### Post by hansdown on 2009-11-20
You're welcome andygait.

SteveHillier has some very good advice here, more than I gave.

There have been times, when the alternate install disk was the only one that worked for some versions on my PC.

Hope all goes well.

---

### Post by andygait on 2009-11-21
(sigh) and so it goes on...
 
Right, I used f6 and changed acpioff and loaded without change to the pc. All went well and everything loaded. I then used the desktop icon to install... it worked! I could use everything and was a happy bunny. I then restarted the pc and I'm back to square one again. It starts, gets so far in the everything stops, keyboard and mouse (both ps2) do nothing. I can't get passed the login screen. 
 
 
I am so hacked off with this now. ](*,)

---

### Post by andygait on 2009-11-21
After yet another frustrating and fruitless afternoon, I think the Ubuntu experiment is at an end. I just can't be bothered anymore. 
 
Many thanks again to all who helped. 
 
Andy. :(

---

### Post by hansdown on 2009-11-21
andygait, given the level of frustration from this, it would be good to cool off a while. It drives me buggy to not be able to help.

New info comes onto the net all the time, so I'll keep looking.

Take care.

---

### Post by andygait on 2009-11-21
I have an old HP in the garage, I may dig that out and see what happens...
 
But maybe not for a few weeks. :)
 
Thank you again.

---

### Post by SteveHillier on 2009-11-22
Andygait, listen well to Hansdown.
There have been many occcasions where I just wanted to kick the rotten stuff where the sun down ever shine but have a break from it and come back later on.
If you can get through it you will be well rewarded.

---

### Post by andygait on 2010-01-11
Just to update the situation, my old PC died, so I now have a new self build PC running 9.10 on a duel boot with windows7 (my daughter need windows for Itunes and some of her school work).
I have also revived an old laptop which is running very well with Hardy. 

No more frustration and I'm a happy bunny once more. :D

---

### Post by hansdown on 2010-01-11
Glad you got things going andygait. Good job.

---

### Post by andygait on 2010-01-12
Thanks. :D

I'm still learning and trying new things, but there's just something about Ubuntu/Linux that I really like. It just seems right. 
On the old laptop I played around with quite a few distros before sticking with Hardy (it just seemed the most stable and as it's a LTR, why not? Although I do like Puppy and it does run a bit quicker than Hardy).

Karmic is running fine and dandy on my desktop and I was lucky to get a free (and legal) version of windows 7, so that keeps the wife and daughter happy. With a bit of education I hope to ween them off of windows and then use Ubuntu for 99% of the families use of the PC. 

Thanks again to all who helped,
Andy.

---

### Post by theozzlives on 2010-01-15
> **andygait said:**
> Thanks. :D

I'm still learning and trying new things, but there's just something about Ubuntu/Linux that I really like. It just seems right. 
On the old laptop I played around with quite a few distros before sticking with Hardy (it just seemed the most stable and as it's a LTR, why not? Although I do like Puppy and it does run a bit quicker than Hardy).

Karmic is running fine and dandy on my desktop and I was lucky to get a free (and legal) version of windows 7, so that keeps the wife and daughter happy. With a bit of education I hope to ween them off of windows and then use Ubuntu for 99% of the families use of the PC. 

Thanks again to all who helped,
Andy.

I think everyone's getting a free version of Windows. It's Microsoft's way of saying, "oops sorry about Vista". I got mine from a confrence I went to.

In April, we'll have another LTS (Lucid Lynx), if you prefer LTS then get that one.

---

### Post by andygait on 2010-01-15
> **theozzlives said:**
> I think everyone's getting a free version of Windows. It's Microsoft's way of saying, "oops sorry about Vista". I got mine from a confrence I went to.
[B]
In April, we'll have another LTS (Lucid Lynx), if you prefer LTS then get that one[/B].

Yeah, I've just read on the wiki that it's supported until 2013, so that's cool.

---

### Post by no2498 on 2010-01-16
lol @ you 2
i just went through this on a dell 6400 2 weeks ago
i had to turn off the hard drive
pull the dvd/rw put the jumper to not master or slave the other 1 forget its name
put the disk in all went well put the jumper back to master
now its time to fix the bugs
webcam works grate in cheese but not wxcam no settings to fix the pic
an flash does not see it do to the loss of v4l1

---


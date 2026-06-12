---
title: "Will Ubuntu run on an old Presario 925ea?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by inikay on 2009-06-15
Hi!

I have an old Compaq presario 925 ea laptop, which I only use for:

- Internet (Firefox)
- MSN Messenger
- Office applications

I connect to my home wireless network with a Linksys Wireless-G notebook adapter.

I'm tired of Xindow XP running SLOW on this. Sometimes it takes 2 minutes (!!) to start firefox...

I thought about installing a light Linux distro which could guarantee the above three functions for this computer.

Anybody has any experience with ubuntu on this type of laptop? Would it run faster than Windows XP?

Thanks,

Inikay.

Specs:
Mobile AMD Athlon XP 2000+ (1,66Ghz)
512 MB RAM
30Gb Hard Disk
Radeon IGP 320M Graphic Card

---

### Post by halitech on 2009-06-15
Ubuntu should run fine on that system. Only possible issue I see is the video card which may require some work but should work. I would suggest trying the live cd before installing.

---

### Post by Mark Phelps on 2009-06-15
> **inikay said:**
> 
- Internet (Firefox)
- MSN Messenger
- Office applications


While Ubuntu should be able to run just fine on your machine, realize that if what you're asking is to run MS Windows apps (through Wine or some other emulation/virtualization feature), then the answer is most probably no -- as in, no, the machine won't run those faster than Windows XP.

Any emulation or virtualization software/layer is going to cost something in terms of performance.

If you're willing to use strictly Linux tools to do the messenger and office work, you should get pretty good performance, but if you're planning on continuing to use MS Windows tools, you're most likely going to be sadly disappointed.

---

### Post by rogueleader12345 on 2009-06-15
There's hardly a computer that Ubuntu can't run on, but you'd have to substitute Pidgin for MSN and OpenOffice for MSOffice. If you're willing to do that, then you should be good!

---

### Post by tomszyszko on 2009-06-15
Ubuntu should run fine, but if you are looking for speed, you should try puppy linux

[http://www.puppylinux.org/]("http://www.puppylinux.org/")

It is light-weight and has everything pre-installed for what you need. Ubuntu is great but gnome slows it down quite a bit. Puppy is faster than Xubuntu also.

Gd luck trying linux!

---

### Post by inikay on 2009-06-15
Thanks for the answers.

Yes, sure, I want to use strictly Linux apps, not MS ones. I'm tired of that :-)

Issue is, I want it really light and fast (well, as fast as this old machine can get :-)

I have been thinking about Linux for ages, but never decided myself to give it a try, so I am a bit worried about driver issues, etc. I've been using computers for more than 20 years, have programed a lot in Turbo Pascal (ages ago, :-) but have no experience on other programming.

I guess I will try the puppy linux tomszyszko suggested, and also an ubuntu version, and see what's the best for me.

Any suggestions on a suitable ubuntu version and where can I get a live CD downloaded from?

Thanks again,

Inikay.

---

### Post by halitech on 2009-06-15
Puppy (as suggested) and DSL are 2 lightweight live cd distros that are designed to run from the cd and have the option to install however I don't recommend them simply due to the fact they use old kernels and outdated apps. Prior to 8.10 I would have suggested Xubuntu but with the bloat they have added to make it easier to use, its not much lighter then regular ubuntu anymore.

If you want speed and stability, I would recommend doing a netinstall of Debian (the basis of Ubuntu) and build it from the ground up. Instructions are here if you are interested

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by prvteprts on 2009-06-15
I was able to install Ubuntu on an even lower-end machine:

Intel Pentium 4 M 1.6
256MB RAM (shared video memory)
Intel Integrated Graphics
30GB HD

So I think it would run on yours better. I have to admit, it's still pretty slow, but at least it starts up way faster (boot and startup programs). I dual boot it with XP and if I boot into XP it takes more than 5 minutes for all the startup programs to load. As they say, XP gets slower and slower with time.

Oh yeah, for better performance use the ext4 filesystem.

---

### Post by egalvan on 2009-06-15
> **halitech said:**
> ...Puppy & DLS... however I don't recommend them simply due to the fact they use old kernels and outdated apps.


Seriously, how "old" and "outdated" is the software compared to, say,
Hardy 8.04.2 LTS?

Often, the "older" kernels are considered more stable.

There are many heavy-duty server farms still running 2.4.x kernels
(yes, this is extreme) do to it's rock-solid stability.

And some apps are in the same boat... a version or two back are considered more stable.


I can't speak for DSL, because I stopped using it over a year ago, when I switched to Puppy.

Puppy is lightning-fast, doesn't need much RAM (256M is good),
and the latest 4.2.x series is rather good at hardware detection.
With 512M RAM, you are in great shape.

Still, building up a minimal Debian, as suggested, is also a fine idea.
A lot of work, but it will give you a lean system, fast and stable.

Puppy will just be easier to get running.

(and it's ludicrously fast on a Quad-Core Phenom with 8GB RAM. :)
or even a 3.2GHz Dual-Core P-IV with 4GB RAM)
or an IBM Thinkpad T40 laptop, 1.6Mhz Pentium M with 1GB )

---

### Post by egalvan on 2009-06-15
> **prvteprts said:**
> I was able to install Ubuntu on an even lower-end machine:

Intel Pentium 4 M 1.6
**256MB RAM (shared video memory)**
Intel Integrated Graphics
30GB HD

So I think it would run on yours better. I have to admit, it's still pretty slow, but at least it starts up way faster (boot and startup programs). I dual boot it with XP and if I boot into XP it takes more than 5 minutes for all the startup programs to load. As they say, XP gets slower and slower with time.

Oh yeah, for better performance use the ext4 filesystem.

If at ALL possible, install more RAM... the difference is tremendous.
(Mom&Pop-style computer shops and computer clubs are two good places to find the older-style RAM you need...
a pair of 256M DDR SODIMM'S can be had for a song,
a pair of 512M DDR SODOMM'S usually requires a dead president or two,
and a pair of 1GB DDR SODIMM'S is usually not worth the expense. :) 
"Your Mileage May Vary Wildly" ).

I got a pair of 256M's free
("I 'need' 1GB RAM for Vista, here's a pair of worthless 256M"


Another useful upgrade is a CPU with a larger cache.

I went from a 1.8 with 512K cache, to a 1.4 with 2Meg cache ($10 'cause it was "only 1.4GHz, what a dog")
It feels "snappier" with the larger cache...

The biggest expense was the hard drive...
PATA Deskstar, 100GB, 7200RPM.
I needed the space, and decided to pay for extra speed.

All-in-all,  a nice lappie...

---

### Post by halitech on 2009-06-15
> **egalvan said:**
> Seriously, how "old" and "outdated" is the software compared to, say,
Hardy 8.04.2 LTS?

Often, the "older" kernels are considered more stable.

There are many heavy-duty server farms still running 2.4.x kernels
(yes, this is extreme) do to it's rock-solid stability.

And some apps are in the same boat... a version or two back are considered more stable.

I honestly have to say its been awhile since I looked at puppy just due to the fact that I've been using debian on pretty much everything lately but looking at the home page for it, they have just released a new version which looks like it might be better and I am downloading it to take a look.

server farms are generally set up and forgotten about until there is a hardware failure and stability would be more important then the latest features like a desktop user would be looking for.

> I can't speak for DSL, because I stopped using it over a year ago, when I switched to Puppy.

Puppy is lightning-fast, doesn't need much RAM (256M is good),
and the latest 4.2.x series is rather good at hardware detection.
With 512M RAM, you are in great shape.

my main gripe with dsl and puppy was trying to get software to install and stay installed after installing to the hard drive. DSL was supposedly a standard debian install (based on the woody distro) after install with an old kernel which gave me troubles seeing the ISA sound card on my laptop. Debian found it with no issues.

> Still, building up a minimal Debian, as suggested, is also a fine idea.
A lot of work, but it will give you a lean system, fast and stable.
I had to recently reinstall due to a hard drive failure and following the link I gave had me up and running with most things working properly in under 25 minutes and its not hard to copy and paste code into the terminal :)

> Puppy will just be easier to get running.

(and it's ludicrously fast on a Quad-Core Phenom with 8GB RAM. :)
or even a 3.2GHz Dual-Core P-IV with 4GB RAM)
or an IBM Thinkpad T40 laptop, 1.6Mhz Pentium M with 1GB )

I'll take a look and see how it runs on my Toshiba Satellite 1800 just for comparison to the current Debian install.

---

### Post by egalvan on 2009-06-15
> **halitech said:**
> ...its been awhile since I looked at puppy 
...but looking at the home page for it, they have just released a new version which looks like it might be better and I am downloading it to take a look.

I hope you will be pleasantly surprised.

The other thing to remember is that Puppy is not trying to be a
"do-it-all" distro... it's meant to be a small distro with the basic functions of Internet, documents and IM.
f you need or want more, then perhaps Puppy is not for you.
Although Puplets exist that contain different outlooks...

> server farms are generally set up and forgotten about until there is a hardware failure and stability would be more important then the latest features like a desktop user would be looking for.

Well, the OP stated he is looking for 

[I]- Internet (Firefox)
- MSN Messenger
- Office applications
[/I]

combine this with older hardware, and stability might be more up his alley than "latest features".
I hope he isn't trying to run Compiz!!??

> 
my main gripe with dsl and puppy was trying to get software to install and stay installed after installing to the hard drive. DSL was supposedly a standard debian install (based on the woody distro) after install with an old kernel which gave me troubles seeing the ISA sound card on my laptop. Debian found it with no issues.


As I stated, I quit using DSL because it was such a pain to set up and use. I never found DSL easy to install, or set up, or use.
Puppy was (and still is) just boot and run...


> I had to recently reinstall... I had me up and running with most things working properly in under 25 minutes and its not hard to copy and paste code into the terminal :)

yeah, it's not that hard for users like you and me, with some experience under our belts... ;)
but the OP gives me the impression he is a new-comer to Linux.
Ease of use will help him enter our world with a good outlook.
Then again...maybe he compiles kernels for breakfast... :)

> 
I'll take a look and see how it runs on my Toshiba Satellite 1800 just for comparison to the current Debian install.

I keep the latest Puppy on an old 256Meg thumb-drive, 
and another copy on a compact CD-RW, just to show folks how small it can be, yet still boot to a workable system.

And as for tiny,
have you tried TinyCore Linux?

---

### Post by halitech on 2009-06-15
> **egalvan said:**
> I hope you will be pleasantly surprised.

The other thing to remember is that Puppy is not trying to be a
"do-it-all" distro... it's meant to be a small distro with the basic functions of Internet, documents and IM.
f you need or want more, then perhaps Puppy is not for you.
Although Puplets exist that contain different outlooks...

I've got it booted up and I'm looking around at it. Had a hard time getting my wireless set up through the setup icon on the desktop but worked fine through pwireless network scanner. the chat icon is misleading in that it opens xchat, not an IM program like pidgin (not installed anywhere that I can find unless you count the meebo webchat). I was impressed with the fact that I popped an audio cd in and it gave me sound right off. The new look of conky is also nice however I still don't like the layout of the icons or the fact that my touchpad won't work with double tapping.

> Well, the OP stated he is looking for 

[I]- Internet (Firefox)
- MSN Messenger
- Office applications
[/I]

combine this with older hardware, and stability might be more up his alley than "latest features".
I hope he isn't trying to run Compiz!!??

I see they have updated to a more recent kernel (2.5.26.26) so issues I was having with hardware have hopefully been resolved. If open office installs and run fine then he should be good to go if he can handle using meebo (or installs pidgin himself). I would hope he's not using compiz as well. My main system has an x1200 video card and I still don't use compiz but I'm not an eye candy type of guy.

> As I stated, I quit using DSL because it was such a pain to set up and use. I never found DSL easy to install, or set up, or use.
Puppy was (and still is) just boot and run...

agreed, puppy does look like it has come along ways since I used it last (still won't be using it on my main system) but I'll keep a copy around for old systems I'm always running across that need to be saved from windows 9x/ME


> yeah, it's not that hard for users like you and me, with some experience under our belts... ;)
but the OP gives me the impression he is a new-comer to Linux.
Ease of use will help him enter our world with a good outlook.
Then again...maybe he compiles kernels for breakfast... :)

never know, it could be Linus or Richard stallman coming for a look at us "regular" users ;)

> I keep the latest Puppy on an old 256Meg thumb-drive, 
and another copy on a compact CD-RW, just to show folks how small it can be, yet still boot to a workable system.

And as for tiny,
have you tried TinyCore Linux?

haven't tried tiny yet as I've been able to get Debian on everything I've tried with either XFCE or LXDE but I just might one of these days.

---

### Post by 2ninerniner2 on 2009-06-15
Bonjour,

I have just recently converted to Linux on a similar system and with spectacular (for me, anyway) results :)

The hardware:
- early 2001 vintage COMPAQ Evo N600c laptop, 1.066GHz P3, 512 RAM, 80 GB HD, shared video memory

The software:
- did a clean install (i.e. wiped out XP Pro, after backup of desired files) using the Kubuntu Live CD and then installed the Gnome desktop environment, as it performs a lot faster on this system and I also prefer the layout.

What I have also been able to do, and this truly amazes me! 
- installed VirtualBox and then XP Pro within that
- installed The Uniform Server (a WAMP package) within XP Pro
- installed Joomla withiin The Uniform Server
... and it runs FASTER than the same setup ever did natively! 

I did this more to see if it could be done, and how to do it, than to use it on a regular basis; plus I also need to run the Artisteer Template generator which I could not get to run in WINE.

However, my favourite graohics package, Macromedia Fireworks 5, runs faster in WINE than it ever did natively! :)

I have now, for all intents and purposes, a "new" computer! Oh, and one more thing ... on this system under Win XP, I could barely get Google Earth to load ... now, I plug in my joystick (which it immediately recognized) and can smoothly use the Google Earth fligh simulator! :)

Cheers!
Lyle

---

### Post by ayenack on 2009-06-15
Not sure if this has been mentioned (haven't read all the posts.) But if your XP install is taking 2 mins to start Firefox on that system then there's something wrong maybe a runaway process or a virus. Your system should run XP fine. 

As for Ubuntu on it, I can't see any problems other than the possible wireless card.

Check this link out to see if it's listed as supported.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

As for a lite weight version of Ubuntu take a look at this.

[http://files.filefront.com/ubuntuicewmremixiso/;13864261;/fileinfo.html](http://files.filefront.com/ubuntuicewmremixiso/;13864261;/fileinfo.html)

---

### Post by egalvan on 2009-06-15
> **halitech said:**
> I've got it booted up and I'm looking around at it. **Had a hard time getting my wireless set up** through the setup icon on the desktop but worked fine through pwireless network scanner. the chat icon is misleading in that it opens xchat, not an IM program like pidgin (not installed anywhere that I can find unless you count the meebo webchat). I was impressed with the fact that I popped an audio cd in and it gave me sound right off. The new look of conky is also nice however I still don't like the layout of the icons or the fact that **my touchpad won't work with double tapping**.

I don't use wireless, but the three lappies I installed Puppy 4.x on ended up with working wifi out of the box.
As for the touchpad issues, the Puppy forum has some good information, you might take a look-see.


> 
I see they have **updated to a more recent kernel (2.5.26.26**) so issues I was having with hardware have hopefully been resolved. If **open office **installs and run fine then he should be good to go if he can handle using meebo (or installs pidgin himself). I would hope he's not using compiz as well. My main system has an x1200 video card and I still don't use compiz but **I'm not an eye candy type of guy**.

Yeah, the latest Puppy's tend to be a bit more up-to-date.
And there is a new Puppy variation coming along.

There is a Puplet that is set up for OpenOffice,
but I wonder if AbiWord is enough for the OP.

As for 'eye-candy', I prefer the beach for that.
South Padre Island is a 20-minute drive. :)

> 
agreed, puppy does look like it has come along ways since I used it last (still won't be using it on my main system) but I'll keep a copy around for old systems I'm always running across that need to be saved from windows 9x/**ME**

ME? ugh and triple ugh.

98se was a very good OS, especially with the changes that 98Lite could make, and changing 98-based Explore for 95-based Explorer.
But I can't trust it on the 'net, so Puppy for me!

> never know, it could be Linus or Richard Stallman coming for a look at us "regular" users ;)

I've be honored to shake their hand.
Or even be in the same room with them.
I consider them, along with Doc Searls and "Mad Dog" Hall to be far superior coders than Gates.

> 
haven't tried **tiny** yet

a ten megabyte download, and you haven't tried it yet?
Watcha' waiten' fer :)


>  as I've been able to get Debian on everything I've tried with either XFCE or** LXDE** but I just might one of these days.

so how is LXDE? I'm searching for a good LiveCD to test it with.
Any recommendations?

---

### Post by halitech on 2009-06-16
> **egalvan said:**
> I don't use wireless, but the three lappies I installed Puppy 4.x on ended up with working wifi out of the box.
As for the touchpad issues, the Puppy forum has some good information, you might take a look-see.

I finally got it going but the settings manager didn't work for some reason, just seems odd they would have it there if it doesn't work (or maybe it just didn't like my rt61 chipset). Not too worried about it for now since I won't be using it full time.


> Yeah, the latest Puppy's tend to be a bit more up-to-date.
And there is a new Puppy variation coming along.

There is a Puplet that is set up for OpenOffice,
but I wonder if AbiWord is enough for the OP.

well it seems like it certainly has come a long way since the last time I used it so hopefully it will get better. And yeah, Abiword and gnumeric are what I use the most instead of OpenOffice but I do install it on my main system as I get my boss sending me Corel docs which only OpenOffice seems to open properly.

> As for 'eye-candy', I prefer the beach for that.
South Padre Island is a 20-minute drive. :)

I agree, or pretty much anywhere downtown seeing as this is a university town ;)

> ME? ugh and triple ugh.

98se was a very good OS, especially with the changes that 98Lite could make, and changing 98-based Explore for 95-based Explorer.
But I can't trust it on the 'net, so Puppy for me!

98se and windows 2000 are the best of the versions they've released so far but with all the extras a person needs to keep safe online, it bumps the resources up so much that running w2k on anyting under a 1gig system is hard anymore.

> I've be honored to shake their hand.
Or even be in the same room with them.
I consider them, along with Doc Searls and "Mad Dog" Hall to be far superior coders than Gates.

I agree and I would love to meet any of the coders that give us such great, free software.

> a ten megabyte download, and you haven't tried it yet?
Watcha' waiten' fer :)

guess I'm lazy ~L~


> so how is LXDE? I'm searching for a good LiveCD to test it with.
Any recommendations?

I find it good, nice and light and loads up about 10-15 seconds faster then XFCE does on the same hardware. Debian has a live cd with it

[http://cdimage.debian.org/cdimage/release/current-live/i386/iso-cd/](http://cdimage.debian.org/cdimage/release/current-live/i386/iso-cd/)

I haven't run the live cd so not sure how it is but the installed version runs nicely on a P300 with 96 meg of ram as long as you don't try to do too much at once.

---

### Post by inikay on 2009-06-17
Guys,

I tried to run the latest Puppy release live CD. Everything went fine, up to the graphics card test. Ir worked all right, but when I clicked "back", it hanged up (there was a message telling it could be a possibility in certain computers).

I had to shut down, and upon restarting, it always hangs on the step "Setting up the layered filesystem...".

After displaying "Done" for this step, it displays the following message:

"Performing a 'switch_root' to the layered filesystem...Kernel panic - not syncing: Attempted to kill init!"

I can't seem to get through this...

Any ideas?

Thanks,

Inikay.

---

### Post by Roadbloc on 2009-06-17
i had a presario 1600us (dunno whether its anything like yours) and it ran like a dream, unlike xp which just ground to a halt after a week or so of usage.

---

### Post by inikay on 2009-06-17
OK. It's up and running, and got everything working except for my Wireless PCMCIA Linksys Card.

I will now try to sort this out through the appropriate forum (PuppyLinux).

It sure runs fast. Managed to connect to the internet via LAN but am a bit disappointed by the looks of some sites. Some info does not appear completely. This might be solved with the new version available. I will see that.

Thanks for the help. I will let you guys know how did this come out.

Inikay.

---


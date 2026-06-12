---
title: "Stopping Ubuntu from booting ANYTHING GUI"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Syndacate on 2011-05-13
**Version:  Ubuntu 11.04**

The "additional drivers" (ie. Jokey) is failing miserably to install simple Nvidia drivers for my GTX285.  I heard somewhere that this was a known issue, if it is, not sure why it's not fixed, it used to work flawlessly for like the last year and a half...but regardless.

It's typically plenty easy to install using the script from Nvidia's site...but I can't shut down Ubuntu's GUI -any part of it.

If I type what I'd expect to type:
/etc/init.d/gdm stop

It gives me some crap about it not being an init.d script anymore (not like it could have been linked or anything to the new system) and I should use:

system gdm stop

Or something to that effect.  Only problem is, when I do that, it gives me a message along the lines of "unknown action: stop."

I just want to stop GDM/X11 so I can install the Nvidia driver 'manually.'

Starting in recovery mode starts the novaeu driver - I want no graphics drivers running - I want text only mode.  Is there any way to make it happen?

Sorry if the post sounds snippy, I'm just aggravated as hell.  I literally spent 20 minutes trying to kill the GUI and I CAN'T, and on top of that, everywhere on google is just like "use the restricted drivers manager" -arrrrrg.

EDIT:
If people need "exact" error messages from the "service" functionality, I can tell you them, but I'm sure if you know about the services functionality, you probably know what they are and the paraphrasing is accurate enough.

TIA

---

### Post by lykwydchykyn on 2011-05-13
I think the command you need is 
```

service gdm stop

```

Not running gdm on my Natty systems, so I don't know if the behavior has changed, but that should work.

If it doesn't, try just "service gdm" and it should give you a list of arguments you can use.

You can also hit shift at boot to invoke the grub menu, then select the "recovery mode" option which will get you to "single user mode" (text console as root with no services running).

---

### Post by jtarin on 2011-05-13
You don't have listed your version of Ubuntu.
Ctrl + Alt + F1-6 will get you another virtual terminal. Ctrl + Alt + F7 will return you. Switch to a virtual terminal then stop GDM with your command. Install your diver, start GDM then siwtch to Ctrl + Alt + F7.(don't forget sudo)

---

### Post by Syndacate on 2011-05-13
> **lykwydchykyn said:**
> I think the command you need is 
```

service gdm stop

```Not running gdm on my Natty systems, so I don't know if the behavior has changed, but that should work.

If it doesn't, try just "service gdm" and it should give you a list of arguments you can use.

You can also hit shift at boot to invoke the grub menu, then select the "recovery mode" option which will get you to "single user mode" (text console as root with no services running).

That's what I was telling you doesn't work ("service gdm stop").  If I type "service gdm" it just tells me:
"USAGE:  /etc/init.d/gdm COMMAND"

This "up start service" thing was just jammed in there and doesn't work worth of ****.  If I type "service gdm help" it says something along the lines of: "/etc/init.d/gdm rather than use the init scripts, use service(8), help is not supported for upstart services" - helpful.

So yeah, that doesn't work.

As for recovery mode, that doesn't work either, it still is running a GUI, just uses the noveau drivers, it does NOT drop you into text-only mode as expected.

> **jtarin said:**
> You don't have listed your version of Ubuntu.
Ctrl + Alt + F1-6 will get you another virtual terminal. Ctrl + Alt + F7 will return you. Switch to a virtual terminal then stop GDM with your command. Install your diver, start GDM then siwtch to Ctrl + Alt + F7.

....That's what I was trying...it doesn't work.  The problem is stopping the GDM has been moved from /etc/init.d/ to this "startup services" thing - and by "moved" I mean "rigged/jammed/forced kicking and screaming"

My version is 11.04 - aka. the only version of Ubuntu where these scripts don't work as expected.

---

### Post by jtarin on 2011-05-13
In my post I mentioned to remember sudo.....did you in the command.
```
sudo service gdm stop
sudo service gdm start 
```

---

### Post by Syndacate on 2011-05-14
> **jtarin said:**
> In my post I mentioned to remember sudo.....did you in the command.
```
sudo service gdm stop
sudo service gdm start 
```

I did not use sudo, I was logged in as root.

---

### Post by ClientAlive on 2011-05-14
You probably already looked at this but these guys are also talking about how difficult it is to stop that service so I guess you aren't alone. I just thought that if they figure out the way to do it (and they actually post it) it could help.

[http://www.overclock.net/linux-unix/1009065-failing-11-04-nvidia-2.html](http://www.overclock.net/linux-unix/1009065-failing-11-04-nvidia-2.html)

Sorry if its something you already saw or is not useful. Just thought I'd offer.

:)

---

### Post by Syndacate on 2011-05-14
> **ClientAlive said:**
> You probably already looked at this but these guys are also talking about how difficult it is to stop that service so I guess you aren't alone. I just thought that if they figure out the way to do it (and they actually post it) it could help.

[http://www.overclock.net/linux-unix/1009065-failing-11-04-nvidia-2.html](http://www.overclock.net/linux-unix/1009065-failing-11-04-nvidia-2.html)

Sorry if its something you already saw or is not useful. Just thought I'd offer.

:)

I didn't see their site, actually.

I'll have to peruse it later when I have more time.  I can't deal with this issue now, as much as it's pissing me off, I have work to do :(.

So I got the service stopped - but it didn't fix...anything.

It turns out disabling the service via root
ie.
```
# service gdm stop
```Doesn't work, but doing it with sudo ie.
```
$ sudo service gdm stop
```Does work.  Theoretically they should be the same, but they weren't (for whatever reason).  Though given how jammed in this 'service' script appears to me that shouldn't be surprising.

That didn't stop anything, though - it stopped the GDM, sure, but in previous versions you were able to then stop X and install the Nvidia drivers, it is not the case here, the nouveau driver is still running, making the installation of the Nvidia driver impossible.

What really annoys me is I know it MUST be possible because Jocky knows how to do it.  I almost feel like tearing into the Jocky source to see how it's disabling the nouveau driver, since it needs to in order to insert the Nvidia module.

Arrrrrrrrrg.  So annoying :(.

Why is it so hard in 11.04???

PS:  I also tried blacklisting the nouveau driver in the modprobe blacklist but it still started just peachy..

EDIT:
So I guess I'm still trying to figure out how to shut down the X server

---

### Post by ClientAlive on 2011-05-14
> **Syndacate said:**
> I almost feel like tearing into the Jocky source to see how it's disabling the nouveau driver, since it needs to in order to insert the Nvidia module.

Now that sounds like a good idea. Except you said you were having problems with Jockey doing its thing - didn't you? Perhaps Jockey is having problems with 11.04. If that were the case then whatever is in the Jockey source would only tell you the same things that aren't working for Jockey on 11.04.

Honestly . . . I ran 11.04 from alpha 3 to release. In the end, I had so many problems with it I went to 10.04. The last time I used 11.04 I had tried to change the names of my username, groupname and home directory. After successfully changing the username and groupname I wanted to change the home directory name. Using the chmod led to an absoute catastrophe on my system. I, and a friend, spent two full days trying to resolve the issue. I almost lost all my personal data and what I had to go through to get it out was just insane! Now I blame myself for this really. I'm very new to Linux and likely did something wrong that caused it. Nevertheless, I can not ignore all the feedback from my friend in the course of trying to restore that home directory. Ever corner we turned with the system led to him making comments like "there's something terribly wrong," and "this shouldn't work like that," or "that thing should be here," etc.

Good luck w/ 11.04. I think you'll need it.

---

### Post by ClientAlive on 2011-05-14
For what it's worth (except you sound like a much more advanced user than I am) here is the results of some digging around on my machine that I did just to see what things are like in there. As I said before though, I'm running 10.04. Just that it shows how I went about getting some info on how this stuff might be working on my system.

```

uname@host:~$ cd /etc/init.d; la | grep gdm
gdm
uname@host:/etc/init.d$ file gdm
gdm: symbolic link to `/lib/init/upstart-job'
uname@host:/etc/init.d$ cd /lib/init; la
fstab     rw                     upstart-job                vars.sh
readlink  splash-functions-base  usplash-fsck-functions.sh
uname@host:/lib/init$ file upstart-job
upstart-job: POSIX shell script text executable
uname@host:/lib/init$ 

```



What may be an option - yet dirty - is to find the file the system uses at startup where it get the information to run the gui stuff; comment out those parts in the file; restart (you'd probably get a shitload of errors and maybe can't even log in unless you do a ctrl+F1 and log in throught the vertual terminal); do your manual installation; go back and un-comment those lines you had changed; reboot.

Bad, Bad ideas. Please don't listen to me. I think crazy things sometimes - especially if I get pissed off at my computer - lol.

:)

---

### Post by jtarin on 2011-05-14
> **Syndacate said:**
> I did not use sudo, I was logged in as root.
Logged in as root will only affect roots account .....on some aspects of your system.

---

### Post by jtarin on 2011-05-14
To load/unload modules/drivers use the command "modprobe".......it was around long before jockey.You can find the usage by using your terminal and typing "man modprobe"

---

### Post by Syndacate on 2011-05-15
> **ClientAlive said:**
> Now that sounds like a good idea. Except you said you were having problems with Jockey doing its thing - didn't you? Perhaps Jockey is having problems with 11.04. If that were the case then whatever is in the Jockey source would only tell you the same things that aren't working for Jockey on 11.04.

Well it's having problems as in after I hit activate it's green 'n all, but if I open it back up after a restart it says "This driver is installed but is currently not being used."

> **ClientAlive said:**
>  Honestly . . . I ran 11.04 from alpha 3 to release. In the end, I had so many problems with it I went to 10.04. The last time I used 11.04 I had tried to change the names of my username, groupname and home directory. After successfully changing the username and groupname I wanted to change the home directory name. Using the chmod led to an absoute catastrophe on my system. I, and a friend, spent two full days trying to resolve the issue. I almost lost all my personal data and what I had to go through to get it out was just insane! Now I blame myself for this really. I'm very new to Linux and likely did something wrong that caused it. Nevertheless, I can not ignore all the feedback from my friend in the course of trying to restore that home directory. Ever corner we turned with the system led to him making comments like "there's something terribly wrong," and "this shouldn't work like that," or "that thing should be here," etc.

Good luck w/ 11.04. I think you'll need it.

From the front end side, I'm like 11.04 a lot, it's a very fluid system.  From the back end side, I'm not sure.  This is the first I've had to dabble with it...because the drivers won't work...and it's not looking good so far... :(  I'd like to *NOT* roll back in Ubuntu distro but I may have to if they decide they want to change the whole system around every release...I don't have time for all that, I use Ubuntu Linux because everything is done for you and you don't have to know anything or think about anything at any time.

> **ClientAlive said:**
> For what it's worth (except you sound like a much more advanced user than I am) here is the results of some digging around on my machine that I did just to see what things are like in there. As I said before though, I'm running 10.04. Just that it shows how I went about getting some info on how this stuff might be working on my system.

```

uname@host:~$ cd /etc/init.d; la | grep gdm
gdm
uname@host:/etc/init.d$ file gdm
gdm: symbolic link to `/lib/init/upstart-job'
uname@host:/etc/init.d$ cd /lib/init; la
fstab     rw                     upstart-job                vars.sh
readlink  splash-functions-base  usplash-fsck-functions.sh
uname@host:/lib/init$ file upstart-job
upstart-job: POSIX shell script text executable
uname@host:/lib/init$ 

```

What may be an option - yet dirty - is to find the file the system uses at startup where it get the information to run the gui stuff; comment out those parts in the file; restart (you'd probably get a shitload of errors and maybe can't even log in unless you do a ctrl+F1 and log in throught the vertual terminal); do your manual installation; go back and un-comment those lines you had changed; reboot.

Bad, Bad ideas. Please don't listen to me. I think crazy things sometimes - especially if I get pissed off at my computer - lol.

:)

That's pretty round-about and hackish, yes, but it might come down to that.  Although the C or Python Jocky is written in beats trying to decipher shell script code :-P.  I'll keep that answer in mind, though, thanks.

As for my Linux experience.  I've been around Linux awhile, but never really dove deep into it, so some may say I am, I say not at all.  The think that pisses me off about Ubuntu is it's a double sided coin.  On one end, ALMOST EVERYTHING works PERFECTLY out of the box.  On the flipside...god ******* help your *** if something doesn't work because pulling answers out of the community is like doing a standing triple backflip - it just doesn't work.  The problem is the same as Windows.  Ubuntu does such a good job at making things work for MOST of the people, MOST of the time, that when you need help getting something done, most answers you get are like "uhhh....."  You don't run into these problems on Arch Linux or Gentoo because people inevitably know the system better.  On the downside, you don't get as great of an end-user experience on those systems...but you know the system inside and out...and if you don't, the person next to you does.  If it wasn't for the fact that I *always* like my system to *just work* with *just about everything* I'd be leaps and bounds away from Ubuntu.  Problem is that it works so damn well comparatively.

> **jtarin said:**
> Logged in as root will only affect roots account .....on some aspects of your system.

I see.  I thought sudo's main purpose was to execute a command as root?  That is, root power without logging in as root?  9 times out of 10 (I would say every time, but apparently not) executing as root has the same effect as prefixing the command with sudo.

> **jtarin said:**
> To load/unload modules/drivers use the command "modprobe".......it was around long before jockey.You can find the usage by using your terminal and typing "man modprobe"

Yeah, I generally don't like messing with Kernel modules - but I'll give it a shot.  I should be able to just boot up in limited graphics mode so the Nouveau driver starts (*I have no idea what is running now as Jocky says the restricted Nvidia driver is 'green' - but it also says it's not currently using it*), then use modprobe to unload the noveau module?

---

### Post by Syndacate on 2011-05-15
> **jtarin said:**
> To load/unload modules/drivers use the command "modprobe".......it was around long before jockey.You can find the usage by using your terminal and typing "man modprobe"

modprobe -l doesn't work, right?  (At least for what I want) - That displays a list of all modules it finds, not of what's currently inserted/installed.  Is this correct?

To mitigate, I used lsmod.

I typed 'lsmod' and one of the modules is named 'nvidia' - so I opened up the nvidia X server configuration and all the configurations are there including a driver number.

So what do I trust?

- lsmod says there's a module named 'nvidia' installed
- Nvidia control panel says it has a driver number (270.41.06)

- Jocky says "Nvidia accelerated grahpics driver (current version) [Recommended] as Green - BUT
- Jocky says at the bottom:  "This driver is activated but is not currently in use"

I don't know who the hell to trust...  Any ideas?

Also, if I add/remove a module from the kernel while running, do I have to reboot?  I'm guessing if I have to reboot I have to rebuild the initialization image?  Def. confused as hell as to whether it's installed or not.

I'd have to go with "NO" despite the evidence of the Nvidia control panel.  OpenGL renders like balls - the program 'glxgears' runs like somebody jammed a wrench in there.  I'm thinking the module is inserted, but not being used...arg, I'm lost :(

---

### Post by ClientAlive on 2011-05-15
I'm online reading about your graphics card (I think).

In your first post you said it is an GTX 285 right?

This one?  [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4376032&CatId=2306&SRCCODE=WEBGOOKWL&cm_mmc_o=mH4CjC7BBTkwCjCs81CjCE](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4376032&CatId=2306&SRCCODE=WEBGOOKWL&cm_mmc_o=mH4CjC7BBTkwCjCs81CjCE)

A new card?

Then In your last post (post #14) you say the driver is 270.41.06.

I see an article here:  [http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml](http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml)

that talks about that driver but the GTX 285 is not among the list of cards it talks about.

Then there is another article here:  [http://news.softpedia.com/news/Download-NVIDIA-GeForce-181-21-Drivers-for-GTX-285-and-GTX-295-Support-101517.shtml](http://news.softpedia.com/news/Download-NVIDIA-GeForce-181-21-Drivers-for-GTX-285-and-GTX-295-Support-101517.shtml)

and it is talking about the GTX 285 but the driver it's talking about is the 181.20 WHQL not the 270.41.06.

Now, perhaps you know what the deal is with that, I don't. I don't have an nVida card I have a broadcom card (oh dread, the broadcom 43xx).

So I'm looking around to see what I can find, but I wonder about this. Also - maybe there is a bug report? Sometimes someone posts a solution they found in the bug report. I've had this happen with a different issue. I did what was said in the solution and it worked.

I'll let you know if I find anything that may be useful.

---

### Post by ClientAlive on 2011-05-15
I assume you've checked additional drivers?

would

```
lspci -v
```

actually list information if the card weren't working? idk.

Are you running 64 bit? Seems like I see that come up in some of my searches.

---

### Post by jtarin on 2011-05-15
To determine your graphics chip/card
```
lspci
```
Then Google to see which module it uses
To see which modules are loaded
```
lsmod
```
To add/remove modules
```
modprobe.
```

All commands have manpages accessible through your terminal.
More detailed examples can be found by Google.

---

### Post by jtarin on 2011-05-15
To determine your graphics chip/card
```
lspci
```
Then Google to see which module it uses
To see which modules are loaded
```
lsmod
```
To add/remove modules
```
modprobe.
```

All commands have manpages accessible through your terminal.
More detailed examples can be found by Google.

BTW:I come from Slackware to Ubuntu and don't let the GUI's get in my way. They are nice at times but the commandline and knowledge of your /etc directory will go a long way.

---

### Post by ClientAlive on 2011-05-15
> **jtarin said:**
> To determine your graphics chip/card
```
lspci
```
Then Google to see which module it uses
To see which modules are loaded
```
lsmod
```
To add/remove modules
```
modprobe.
```

All commands have manpages accessible through your terminal.
More detailed examples can be found by Google.

BTW:I come from Slackware to Ubuntu and don't let the GUI's get in my way. They are nice at times but the commandline and knowledge of your /etc directory will go a long way.

jtarin:

I found this article that talks about a sort of different way of installing nvida drivers than what I had been seeing. The article is for Ubuntu 10.10 but I think some things don't change between versions.

What do you think about this? Are they doing something different in that article then?

---

### Post by jtarin on 2011-05-15
> jtarin:

I found this article that talks about a sort of different way of installing nvida drivers than what I had been seeing. Link???

---

### Post by ClientAlive on 2011-05-15
> **jtarin said:**
> Link???

Oops! Sorry.

Here ya go:  [http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat)

btw - looks like reader comments at the end might be worth taking a peek at too.

Looks like whatever was going on - the guys figured it out about a third of the way into the reader comments.

> 
Too sleepy but I have the answer, I think. I ha similar issues. Add me up on msn. [email]udaypatel5858@hotmail.com[/email] 

Make sure you mention &#8216;ubuntu guide&#8217; when sending me the email invitation.



btw - how much do we know about this guys system that it might help us to help him? Does he have onboard graphics as well? Is he running 32 or 64 bit? Would these make a diff?

---

### Post by Syndacate on 2011-07-17
Wow, it's been awhile since I've posted here.  I got caught up with a bunch of stuff in life and haven't had time to deal with this for awhile.

Now that I'm back trying to get Ubuntu to do anything except fail, I returned to this thread.

Yes, my graphics card is supported - it was supported just perfectly fine under 10.10, the proprietary drivers worked PERFECTLY.  It's been nothing but a headache in 11.04.  If you just google:
"natty nvidia drivers installed not currently active" you get BOATLOADS of results.  The problem is very simple, the proprietary drivers via Jokey don't work.  Now lots say thats Jokeys fault, if you look around (anywhere), you'll see it's a reported bug about Jockey...which is fine.

I don't know how this is going on for 3 months and there's still no patch to fix it in Jockey, but fine, whatever, it's not getting fixed, but at least let me install the proprietary drivers manually FFS.  I can't, though.  I can't because Ubuntu ****** with the init scripts and I can't get them to work right.

This SHOULD work:
```
/etc/init.d/gdm stop
```

But it doesn't.

Then I can do:
```
sudo ./nvidia....blah blah blah
```

But it won't shut down GDM, nor the X server, nothing shuts down, there's no terminal recovery only no GUI anymore....All I want to do is install the the thing using the Nvidia scripts...if they can't fix Jockey then at least let me do it semi-manually?

I love Ubuntu, I love Unity, but holy **** this problem is annoying.  And if you google it, there's posts EVERYWHERE about it, but apparently no fix?  Seriously?

I'm sorry if I sound like a total ******* in this post (I am), but I've put way too much time into something that should just work...and if you're wondering how I can say "it should just work" - it's because it "just worked" in the last 3 distros of Ubuntu.

---

### Post by Zill on 2011-07-17
> **Syndacate said:**
> ...but I've put way too much time into something that should just work...and if you're wondering how I can say "it should just work" - it's because it "just worked" in the last 3 distros of Ubuntu.
If you had a stable system that worked for you then why upgrade?  If you *need* a stable production system then I suggest the [LTS]("https://wiki.ubuntu.com/LTS") releases would be more appropriate:
> Instead of doing an automatic full package import from Debian unstable, we will do it from Debian testing. The benefit we gain from not introducing new bugs and/or regressions outweighs the new features and/or fixes we often get from unstable.

---

### Post by lykwydchykyn on 2011-07-17
> **Syndacate said:**
> 
This SHOULD work:
```
/etc/init.d/gdm stop
```

But it doesn't.

Then I can do:
```
sudo ./nvidia....blah blah blah
```


I thought we established several pages back that 
```

sudo service gdm stop

```
(using sudo, not root)
is the command to use, and that it worked for you.  Is this not working for you?

---

### Post by Syndacate on 2011-07-18
> **Zill said:**
> If you had a stable system that worked for you then why upgrade?  If you *need* a stable production system then I suggest the [LTS]("https://wiki.ubuntu.com/LTS") releases would be more appropriate:

While I need this to be a stable system, I have other production systems that are set up to do development necessary for work.  So my apologies if I over-emphasized the necessity of this system.  This is more my "*general purpose and non-life critical programming projects system*."  Ideally I'd be in Ubuntu 24x7 on this system except for when I play a game (once a week? lol).  Maybe you can say I'm a programming hobbiest since I'm not really affiliated with any project in my free time? (sure?)

My main (critical) dev occurs at work (8-5 or so) - where my system is setup just right, but it's in a Windows environment.  My apologies for the confusion.

> **lykwydchykyn said:**
> I thought we established several pages back that 
```

sudo service gdm stop

```
(using sudo, not root)
is the command to use, and that it worked for you.  Is this not working for you?

My mistake, that was me rushing while typing the last post, I did do sudo service gdm stop/start and sometimes it works...sometimes it says "*instance not found*."

I'm not entirely sure what to do.  I dropped to a root shell, the nvidia installer dropped the noveau disable script into my /etc/modprobe.d/ directory, and that appears to work to shut noveau down...and then the installer appears to build and insert the module...but it fails...or maybe it's succeeding but sucking?

It seems like when it's installed everything works..but my graphics are horrible.  I get my native graphics resolution, but glxgears turns slow as hell, despite a claimed 8500 FPS, and Flash runs like complete crap, barely able to play videos, completely unable if I fullscreen them.  My desktop seems fine, though.  This behavior reminds me EXACTLY of the noveau driver...  If I uninstall the module and use Jockey to install, I get the EXACT same effects, and it says "*This driver (Nvidia proprietary) is installed, but is currently not in use.*"

I have had the "*installed but not in use*" problem ever since I installed Natty - fresh install.

I have a feeling when the Nvidia build script (from their site) builds, it is failing the same way Jockey is..  The only issue I get during the Nvidia installation is that the pre-installation script failed.  I checked the nvidia installer logs and I CANNOT find any useful information.  It just tells me what's enabled and disabled, it doesn't tell me any problems other than what the installer tells me...so I'm assuming there are none?  (Poor assumption).

Don't know - don't know where to start, this is an annoying problem.  I feel there was more issues than the service scripts not working...and I don't know what to do or how to proceed.

Any advice is much appreciated.

If you just google "nvidia driver installed not currently in use" you'll get a boat-load of results pointing to the same problem, which appears to be a problem with Jockey...but who the hell knows, I can't find a good answer anywhere :(.

Sorry for the long post, and again, thanks.

---

### Post by Zill on 2011-07-18
Syndacate:  Could your problem be related to Bug [#771788]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788")?  It may be worth trying the solution given in post [#104]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788/comments/104") by Emilio.  Please note that additional relevant info is given in post #105 so you may like to read all associated comments before proceeding. ;-)

---

### Post by Syndacate on 2011-07-19
> **Zill said:**
> Syndacate:  Could your problem be related to Bug [#771788]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788")?  It may be worth trying the solution given in post [#104]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788/comments/104") by Emilio.  Please note that additional relevant info is given in post #105 so you may like to read all associated comments before proceeding. ;-)

While it's possible, I don't think it is.

That is the known bug I was speaking of which is easily google'able.  Though I don't think that's my issue.  I think I'm running off of the noveau driver, but I cannot tell.

In previous versions with of Ubuntu, I gauged whether the nvidia driver was running by simply running 'glxgears' - that might be a hack way of telling..sure...but I have a GTX280 so it's not exactly a slouch (I can't recall if it's a 280 or 285).  On previous installs of Ubuntu, when running glxgears, they run perfectly smooth and happy once the Nvidia drivers are installed.  On this one?  Not even remotely.  They update about once every 5 seconds, though for some reason they still report a FR of 8500 or so.  The way they act feels a lot like what I'd expect to get from the noveau drivers.

So I guess in the end the question becomes, how do you know which drivers are currently being used by X?

It's not just glxgears which fails miserably, desktop UI is fine, but when I go to like youtube, or any other "harder" animation level thing it's just choking like all hell.  Stereotypical noveau driver issues :-\.

The bug above talks about Jockey not reporting it, which is what I said a few posts back (multiple times) - I'm ok with that, though, if Jockey doesn't report it, whatever, I just want to install it from the binary on their site, then...which apparently I have...but the results don't appear as if I have...and the script the nvidia installer tries to run at startup fails...this leads me to believe that the nvidia driver install (out of Nvidia's script, NOT Jockey) is failing silently...which is another reported bug...

I'm kind of lost as to which steps to take, but I will look at post 105 and related posts when I get back today - I'm judging that I don't think it is based on the title.

I guess the problem I'm having now has shifted more towards "the drivers say they installed...but I don't think they're being used" rather than anything to do with Jockey.

---

### Post by lykwydchykyn on 2011-07-19
Try 
```

grep -i loadmodule /var/log/Xorg.0.log

```

one of the lines should look something like this:
```

[    20.893] (II) LoadModule: "nvidia"

```

---

### Post by Syndacate on 2011-07-31
> **lykwydchykyn said:**
> Try 
```

grep -i loadmodule /var/log/Xorg.0.log

```

one of the lines should look something like this:
```

[    20.893] (II) LoadModule: "nvidia"

```

```
$ grep -i loadmodule /var/log/Xorg.0.log
[    32.023] (II) LoadModule: "extmod"
[    32.023] (II) LoadModule: "dbe"
[    32.023] (II) LoadModule: "glx"
[    33.516] (II) LoadModule: "record"
[    33.517] (II) LoadModule: "dri"
[    33.517] (II) LoadModule: "dri2"
[    33.517] (II) LoadModule: "nvidia"
[    33.677] (II) LoadModule: "fb"
[    33.678] (II) LoadModule: "wfb"
[    33.678] (II) LoadModule: "ramdac"
[    35.324] (II) LoadModule: "dri2"
[    35.405] (II) LoadModule: "evdev"
```

**New synopsis at bottom if you don't feel like reading**

:-\

I don't know what to do.  According to that the nvidia module is loaded and *should* be running fine...it just feels like the noveau driver.

Don't know, maybe I'm delusional.  Maybe OpenGL didn't build right, I don't know.  What is GLX?  It says the module is installed...I've been using GLXGears for the last 5 years to make sure I'm not using the regular driver...never once has it failed to determine the truth.  Every single time, it's choppy as hell with the provided driver, and it's smooth as silk with the Nvidia drivers.

I typically download the Nvidia drivers via Jockey, but since that seems to have a major flaw that nobody is bothering to fix (what is going on with that, btw?? - it's like, this massive problem in 11.04 since its release that nobody's fixed) - I installed from their make script, thinggy.

I guess I'm just losing my head.

I downloaded an old computer graphics project...it's not much, but I bumped the resolution up to 1000x1000 and lowered the refresh rate to 10ms.  It's not like, super heavy duty processing, but it's 2 walls, a floor, a table, some GLUT objects on the table with some luminescent properties, 2 lights with different properties, and a camera position controlled by the keyboard, and another one animated to circle above the scene.  It's nothing hardcore, but I would think it's on par with the 200x200 glxgears view...but my program runs smooth as silk.  That's just OpenGL and GLUT.

But the other thing is Flash.  Now IMO, Gnash just can't cut it.  Being a heavy youtuber, I rely on Adobe's flash, but when it glitches like it is, it makes me not want to use it.

Wow, in the midst of whining about Flash not working right, which is what I've seen as a common problem using Adobe's Flash with an OSS gfx driver, I double checked to make sure it wasn't gnash - it was.  I have to say - "wow" to the gnash guys, it's come a LONG way since I've seen it last...though still, at the present, I would rather use Adobe's flash plugin...which I have, but the weird thing is, after disabling gnash, even though the adobe plugin is installed, it doesn't work in FF.

Weird.

This went from a "*my driver isn't working worth of *****" question to "*glx gears isn't working and I can't figure out how to turn on flash.*"

I feel like an idiot.  I give up, I guess the driver IS installed, but the two sources I relied on (which were poor, I'll admit) BOTH happened to give me false positives.

<-- Fails I guess...blah.

Guess I gotta figure out how to turn on the Flash player.

**Synopsis:**
Though I do have to say, I couldn't install Nvidia's driver for the longest time because the Novaeu driver was active...I'm thinking in somewhere in the midst of you guys helping me - running commands, trying different things, getting useless error messages from the Nvidia installer, and having no luck what-so-ever, I guess I finally did get it disabled via the Noveau disable file, and I guess the Nvidia driver did install (but with some errors I guess?)...and I guess all my tell-tale signs I used remained the same.  Weird.

---

### Post by Zill on 2011-07-31
Syndacate:  Maybe [Bug #755148]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/755148") is relevant?

---

### Post by Syndacate on 2011-08-01
> **Zill said:**
> Syndacate:  Maybe [Bug #755148]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/755148") is relevant?

I don't think so.

Two reasons:
1)  That frame rate is dropping, he said he couldn't get it past 1k - mine's at 8500 in glxgears, it's just slow as hell anyway.
2)  I'm pretty sure I'm using compiz

Though if you read the above...I think the problem is fixed..  I think just relying on glxgears and flash as I was was a combination of two factors that I was using to determine whether it was on the built-in driver or not failing.

I'd still like to know why glxgears is slow as **** despite its supposed 8500 frame rate, but I think everything else is good, most of the flash issues can be attributed to gnash, which I didn't realize was enabled.

I'd like to say my windows are a bit glitchy when I drag them fast...but that may just be a placebo of me over-analyzing them now.

I'm not sure what the problems are anymore, or if I even have any besides glxgears not working...?

Perhaps the newer version of xorg or OGL's GLX interface is performing poorly?

---

### Post by whitethorn on 2011-08-01
Glxgears isn't a good way to test graphics

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

What kind of graphics card do you have? Have you tried gnome classic without effects, you can choose it after inputting your name and before you password at login. How does it perform compared to unity. Unity runs horribly on my netbook, but gnome classic is ok, and openbox is fast.

I'm not sure what version of adobe you have installed, but the beta version has video acceleration enabled and it has problems with it, check the file (if it's there), and disable it. 

```

sudo nano /etc/adobe/mms.cfg           # and set to 1 to 0, 
EnableLinuxHWVideoDecode=1             

```

---

### Post by Syndacate on 2011-08-10
> **whitethorn said:**
> Glxgears isn't a good way to test graphics

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

I'm not trying to use it as a benchmark, either.  I simply stated that it runs like dog-****, when typically with the nvidia drivers installed, it's completely smooth.  I simply put the FPS there because at how shitty it's running, .5 FPS would be a more accurate rating.

> **whitethorn said:**
> What kind of graphics card do you have?

A GTX-280 overclocked from the factory...I doubt it's going to have issues rendering the DE.

> **whitethorn said:**
> Have you tried gnome classic without effects, you can choose it after inputting your name and before you password at login. How does it perform compared to unity. Unity runs horribly on my netbook, but gnome classic is ok, and openbox is fast.

I haven't tried Gnome classic, no, but honestly, without sounding pompous, if my GTX-280 OC'ed can't run unity smoothly, then they messed up....bad...I'm not running a netbook here.

> **whitethorn said:**
> I'm not sure what version of adobe you have installed, but the beta version has video acceleration enabled and it has problems with it, check the file (if it's there), and disable it. 

```

sudo nano /etc/adobe/mms.cfg           # and set to 1 to 0, 
EnableLinuxHWVideoDecode=1             

```

Doesn't exist.  Should I add it?

I'm considering going Gnome 3 (not for this reason), but I hear you can't go back, really, so I'm not sure if it'll be much of a problem, anymore.  Though I def. feel the UI ran smoother in 10.10...though it may just be Unity vs Gnome.  Either way, GLX running like crap is annoying me, because I don't know the reason.

---


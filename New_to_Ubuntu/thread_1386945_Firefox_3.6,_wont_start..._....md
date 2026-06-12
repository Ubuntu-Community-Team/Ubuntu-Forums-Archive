---
title: "Firefox 3.6, wont start... ..."
date: 2010-01-21
forum: New to Ubuntu
---

### Post by techno-mole on 2010-01-21
hello.

I have just upgraded firefox to 3.6 (namoroka) and found that it wont start, and running it in a terminal gives this error - ```
(firefox-bin:10639): GLib-WARNING **: g_set_prgname() called multiple times

```

I have found a fix for it, but you have to do it every time you want to run it, delete the .mozilla folder in your home directory (press ctrl + h to see it as its hidden) but be warned doing this will delete your bookmarks etc, so maybe it would be better to rename it, that way when it gets sorted out you should be able to copy the .mozilla contents into the new one that gets created when you run firefox.

of course you could also just not update for a while :-)

cheers

---

### Post by andreasdelpaso on 2010-01-22
Help,i'm a new ubuntu user and i just upgraded from firefox 3.5.7 to 3.6 namoroka.
It started up once,then crashed and wont start again.
Can anyone help me?
Thanks in advance.

---

### Post by kansasnoob on 2010-01-22
Ubuntuzilla updated me to FF 3.6 today with no problems:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by andreasdelpaso on 2010-01-22
> **kansasnoob said:**
> Ubuntuzilla updated me to FF 3.6 today with no problems:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Thank you for the reply but once i write in terminal :
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

i get :
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found

---

### Post by andreasdelpaso on 2010-01-22
Out of desperation i used update manager,got some updates that i probably unistalled from synaptic (like firefox 3.5 i think) and Namoroka is up and running,in fact it restored my previous session.
Sorry for the false alarm...

---

### Post by kansasnoob on 2010-01-22
First of all do not remove the official Ubuntu Firefox package(s)!

Next determine if this is 32 bit or 64 bit by running:

```
uname -m
```

64 bit users would see x86_64, 32 bit users would see i686. 

[B]For 32 bit in 9.04 and later only run:
[/B]
```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null 
```

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

```
sudo apt-get update
```

```
sudo apt-get install firefox-mozilla-build
```

**For 32 bit in 8.10 and earlier only run**

```
echo -e "\ndeb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null 
```

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

```
sudo apt-get update
```

```
sudo apt-get install firefox-mozilla-build
```

**All 64 bit users only look here:**

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)

**Note:** read here about Localizations:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Localizations](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Localizations)

---

### Post by mkvnmtr on 2010-01-22
I updated to 3.6.1 pre from Ubuntuzilla this morning. I had to restart the browser three times but now it is up and running fine. It seems to be using much less memory and cpu. We will have to use it a while but I think it will be much better.

---

### Post by techno-mole on 2010-01-22
well firefox 3.6 is working for me, sort of.

I cant launch it using any icons, either from gnomes applications menu or icons on awn, same goes when I tried it with cairo dock or any other icon.

it will however run using terminal (not ideal) and heres where it gets odd, I have a keyboard that has various short cut keys on it, eg  - a key for the up and down volume and start and pause etc etc if I use the short cut key for the browser it works ? so at the moment im just using the key until I can figure out why it wont launch from an icon

cheers

---

### Post by JSeymour on 2010-01-22
I've about had it with  FF brain-deadness.   Their latest update (3.5.7, I think it is) has been wreaking havoc on the 'doze desktops here at work.  You see: Unlike most other places (apparently): We don't let our end-users commonly run with Admin rights.  Well, it seems the FF updater is too st00pid to realize that, attempts an update, anyway, which it cannot complete, and trashes things to the point where an Admin has to login to the system, uninstall Firefox, and re-install from scratch.

So, as time allows (HA!) at work: I plan to look into Opera and Chrome for my 'doze users.  I'll be doing the same for my wife and I at home.  (I use Ubuntu, exclusively, on my desktop.)

If I can dump FF, it'll be history.

I wish somebody would take the Gecko rendering engine, which is, by all accounts, pretty decent, and build a browser around it that wasn't a bloated, unstable, exploit-riddled POS, really I do.

Jim

---

### Post by muteXe on 2010-01-22
Least you get to chose your browser. At my work we have to use IE :/

---

### Post by mkvnmtr on 2010-01-22
The latest Seamonkey build from Mozilla is a good browser that does not seem to have the problems that Firefox has.It also has Ad block and No-Script.

---

### Post by nanotube on 2010-01-22
> **mkvnmtr said:**
> I updated to 3.6.1 pre from Ubuntuzilla this morning. I had to restart the browser three times but now it is up and running fine. It seems to be using much less memory and cpu. We will have to use it a while but I think it will be much better.

if you got 3.6.1 pre, then it is not from the ubunutzilla repository - the repository only follows official mozilla releases, and latest firefox release is 3.6. you're probably getting your 3.6.1pre from the ubuntu-mozilla-daily repository?

---

### Post by ktucker on 2010-01-23
For me Firefox 3.6.1pre only starts with a new profile via 'firefox -P' (or if I first delete the contents of an existing profile directory, losing all its settings ... later discovered I only had to delete file 'compatibility.ini').

---

### Post by JSeymour on 2010-01-24
> **muteXe said:**
> Least you get to chose your browser. At my work we have to use IE :/Not really.  Firefox is basically mandated.  For now.  As you're probably aware: It's neigh impossible to actually *remove* IE, but we do remove it from the desktop and do not pre-configure it, thus strongly discouraging its use.  But when time provides (HA!), I'm going to research an alternative.

Jim

---

### Post by Bethain on 2010-01-26
For an unknown reason, Firefox 3.6 crashes on startup if you have Stylish or Greasemonkey installed and enabled. When disabled, it behaves completely normal.

---

### Post by skymera on 2010-01-26
I found creating a new profile fixed this for me.

```
 firefox -P 
```

---

### Post by ashgoodman on 2010-01-26
Same problem. Creating a new profile solves the problem, though the error message:

(firefox-bin:3876): GLib-WARNING **: g_set_prgname() called multiple times

still comes up.

But at least it starts.

Never mind that I all my bookmarks, saved passwords, extensions etc are in the other profile....

And yes I know I can copy them over but until I know what the blazes is happening and why things are broken I don't have the time to go through the trial and error of copying one thing over, ns testing, copying another and testing....

Bottom line Firefox is broken I don't know if its an ubuntu problem or a firefox one, but as firefox is the default browser in ubuntu that makes it an ubuntu problem.

Here is the full output from terminal when starting my default profile: 

user@mycomputer:~$ firefox

(firefox:4665): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4665): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4665): GLib-WARNING **: g_set_prgname() called multiple times
Segmentation fault
user@mycomputer:~$

After which firefox does not start.


Here is output when I start a new profile:
user@mycomputer:~$ firefox

(firefox:4742): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4742): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4742): GLib-WARNING **: g_set_prgname() called multiple times

user@mycomputer:~$

The new profile now crashes as well though not everytime.

I await an official fix as it is beginning to look as if my only option is to do a complete reinstall if I wish to have a usable computer.

I am a hardcore linux fan, but right now i am about as pissed off as I can get. I use these computers to MAKE A LIVING and a browser is a core feature!

---

### Post by nanotube on 2010-01-27
which version of firefox are you using? how did you install? and post output of 'firefox --version'

---

### Post by ashgoodman on 2010-01-27
INstalled through synaptic

:~$ firefox --version
Mozilla Firefox 3.5.7, Copyright (c) 1998 - 2009 mozilla.org


Just did a remove  and reinstall between which I removed my old profiles and still getting the following errors:

$ firefox -no-remote -P

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

As the old profiles are not there anymore this means it can't be an extension though i supose it could be one of the plugins? All I have installed for plugins are the standard java rte, totem and flash players

It does start however, but I seriously doubt its stable with 4 identical errors coming up while it starts.

Xulrunner is 1.9.1

I am a webdesigner and to suddenly be unable to use and test on a core browser... I am shaking my head speechless as I write this. Its inexcusable. A bug like this should have been detected and fixed BEFORE being pushed out.

I have been with ubuntu (happily) since I first switched to linux. After today I am seriously looking into other linux variants.

Inexcusable

As if that wasn't bad enough this forum suddenly wants to make things difficult: it doesn't remember my password (using opera for now) so for example I have had to post this 3 times as the first 2 times the forum said I didn't have sufficient permissions....  so not only am I fighting critical bugs, but I have to fight to post about them.

In one day I have been changed from a hardcore ubuntu fanboy to a pissed off seriously looking at another linux or (dare I say it) windoze again (lots of problems in windows, but browsers not working has never been one of them at least for me). God I sgudder even to say it, I haven't used windows in over 3 years. But I gotta work and if linux wont let me what choice do I have.

My stomach is turning even thinking about it.

edit: when I reload sources in synaptic I get this message:

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages)

Could this have anything to do with it?

This isnt the first time I have gotten messages like this, last time it left me unable to update for weeks.

Maybe I'll look at suse

---

### Post by nanotube on 2010-01-27
> **ashgoodman said:**
> INstalled through synaptic

:~$ firefox --version
Mozilla Firefox 3.5.7, Copyright (c) 1998 - 2009 mozilla.org


Just did a remove  and reinstall between which I removed my old profiles and still getting the following errors:

$ firefox -no-remote -P

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:6884): GLib-WARNING **: g_set_prgname() called multiple times


as very prominently displayed, these are /warnings/, not errors. they can be safely ignored. 

i notice also you're starting with '-no-remote'... if you're running multiple instances of firefox, note that you have to be careful not to use the same profile for multiple instances, that can cause problems.

> 
As the old profiles are not there anymore this means it can't be an extension though i supose it could be one of the plugins? All I have installed for plugins are the standard java rte, totem and flash players

It does start however, but I seriously doubt its stable with 4 identical errors coming up while it starts.



if it does start and work when you remove the profile, that means it's working, so the actual problems were caused by something borked in the profile. (the warnings do /not/ mean it doesn't work).

so just create a fresh profile, and copy over your bookmarks and stuff.

> 
<snip out angst> :)

edit: when I reload sources in synaptic I get this message:

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages)


duplicate sources are basically harmless (note again, this is a warning, not an error). however, it should be pretty clear as to the cause and the solution (i.e., go through your sources.list, and remove the duplicate medibuntu entries).

> 
Maybe I'll look at suse

never hurts to try new things :)

EDIT: also note that this thread is about firefox 3.6 - since you say you're using 3.5.7 from the ubuntu repos, maybe you should have started a new thread...

---

### Post by ashgoodman on 2010-01-27
Thanks for the feedback nanotube.

The thing is I am not running multiple instances of firefox. I even rebooted the computer to be sure.

That error message (and since I am not running multiple instances - at least not intentionally - that's what i'll call it) comes up the first time I run firefox after a fresh boot.

It comes up whether I run no-remote or not.

And aside from the segmentation fault the message was the same before and after deleting my profile.

Since I rely on firefox for several things from browsing to email to password storage to ftp. I can hardly have it throwing errors or warnings or showing any signs of instability.

Its the center of my workflow.

I know it should not be throwing these messages and as long as it is I will not be able to rely on it comfortably.

"if it does start and work when you remove the profile, that means it's working, so the actual problems were caused by something borked in the profile. (the warnings do /not/ mean it doesn't work)."  I didnt say it meant it wasn't working. I said it would start but wasnt stable. and in fact further testing has backed this up. Simply opening the addons dialogue causes it to crash in one instanace, browsing a google search results page another and so on. This is a newly created profile with no addons installed.


And can anyone explain why this forum requires me to login 3 times before I have sufficient permissions to post. And then another 3 times before I can save my post. Seriously this is not a joke. For some reason this is what is happening (using latest version of opera)

---

### Post by Kupfer on 2010-01-27
I have the same problem with FireFox 3.6:

(firefox-bin:3223): GLib-WARNING **: g_set_prgname() called multiple times

And I get the same error message with Swiftfox 3.6 too. They wont start.

This must be an Ubuntu-specific problem, because on my Fedora 12 FireFox 3.6 is running without any problems.

It is a little bit frustrating, since I naturally want a working FireFox on my system, but there are many good alternatives. Until this gets (hopefully) sorted out, I am using Chromium. 
I am running the FireFox-based GNU IceCat (version 3.5.7 of course) as a FF replacement. You can get it here: 

[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
[http://ftp.gnu.org/gnu/gnuzilla/3.5.7/](http://ftp.gnu.org/gnu/gnuzilla/3.5.7/)

Oh, and I have no problem logging in/posting on/editing posts in the forum. (I'm writing this with IceCat 3.5.7)

We are certainly not alone with the FF 3.6 problem - I've seen comments reporting this on webupd8.org too.

---

### Post by ashgoodman on 2010-01-27
Hi Kupfer

Looks like icecat is having the same trouble: 

:~$ icecat

(icecat-bin:3390): GLib-WARNING **: g_set_prgname() called multiple times

---

### Post by Kupfer on 2010-01-27
> **ashgoodman said:**
> Hi Kupfer

Looks like icecat is having the same trouble: 

:~$ icecat

(icecat-bin:3390): GLib-WARNING **: g_set_prgname() called multiple times

Did you try the 3.5.7 version? Because only older versions of FireFox or FF-based browsers like IceCat or SwiftFox are working for me.

I have now downgraded my FireFox 3.6 to the prevoius 3.5.7 version in synaptic. 
3.5.7 is working fine for me, only 3.6 doesn't want to start.

I hope someone with more Ubuntu experience figures out some solution - I'm just a regular user. 

I looked into  'GLib-WARNING **: g_set_prgname() called multiple times' problems on the internet and mostly they were solved with downgrading  libglib2.0-0. I tried taht but it isn't working in this case.

I don't need to have FF 3.6 right away, so I will be using 3.5.7 temporarily. But I do hope someone with more experience figures this out.

---

### Post by ashgoodman on 2010-01-27
I am using 3.5.7 in firefox. Not 3.6

Tanks for your help anyway, but I think I'll have to find another solution

---

### Post by Post Monkeh on 2010-02-05
i use swiftfox and this problem started a week or so ago for me when using swiftfox.

i thought that since my firefox was 3.5.3, and my swiftfox was 3.6, that it would be a good idea to upgrade my firefox to version 6 as well.  it wasn't, now firefox won't start either.

what i CAN do is alternate between the two. if i load swiftfox and close it, i can't open it again, but i can open firefox. once i colse firefox, i can't open it again, but i can open swiftfox, but while this isn't exactly the end of the world since they are essentially the same program it is still a bit of a poor bug.

i read about the fact that deleting the compatibily.ini would fix this, so i made a little script to launch instead of just automatically running swiftfox.

```
#!/bin/bash
cp /home/will/.mozilla/firefox/dtqfi85t.default/compatibility.ini /home/will/.mozilla/firefox/dtqfi85t.default/compatibilitybak.ini
rm /home/will/.mozilla/firefox/dtqfi85t.default/compatibility.ini
swiftfox
```

obviously everyone's profile folder (and home folder of course) will have different names than mine, but it at least means i can always  load the program.

---

### Post by Fernando Hernandez on 2010-02-12
Well at least it seems I'm not the only one with this problem.

I just did a system update, and it upgraded my FireFox to Namoroka 3.6.  I was able to launch it once, was dissatisfied with 2 useful add-ons not being compatible, went to download 'good enough' replacements for them, and did the standard 'restart to take effect'.  Restart didn't happen, got the same terminal output as everyone else...

(firefox-bin:1919): GLib-WARNING **: g_set_prgname() called multiple times

Uninstalled, did sudo apt-get autoremove a few times, rebooted my computer, reinstalled, nothing is working.  Tried to install 3.5 again.  No difference.  I can get Namoroka to launch with an alternate profile, but I'd rather just clean my system of this garbage and get my 3.5 back.  Is there any way I can do that?  I don't know how to remove 3.6, and as I said, reinstalling 3.5 still gave me the same error when trying to launch.  Still kind of a n00b here, so if there's a way to remove 3.6 and start with 3.5 again (even if I've got to lose all my settings, while I'd prefer not to; I backed up with FEBE about a month ago so it could be worse), help would be greatly appreciated.  Google Chrome is a nice and fast backup browser, but I'd really rather not have to use it full-time - I want my FF, and I want my add-ons.

---

### Post by jegxx on 2010-02-26
Ok for everyone trying to fix this problem this is what fixed it for me.

The first thing i did was go to my profile folder at .mozilla in my home folder. (you have to go to View and check the Show Hidden Files box)I then found the profile i wanted to start and deleted the compatibility.ini file in that profile.then open terminal and type "firefox -safe-mode" then disable all extentions and start firefox.Go to tools-addons and click the extentions tab and enable each extention and restart till you find the one that is causing it to crash.For me it was Prism that was causing it but the remove was grayed out and I had to go to synaptic to remove it or use the terminal.

---

### Post by Arkitekt on 2010-02-26
I was having the same problem, turns out it is two different issues.

After some trial and error, I have discovered that the reason 3.6 won't start up is due to greasemonkey. The reason it is causing a problem with 3.6 is because greasemonkey seems to not auto-update when a new version comes out, most of us have pre-3.6 versions. I myself had a version from January of 2009. Looks like in 0.8.3 greasemonkey added a 3.6 compatibility flag. Updating manually from the add-ons website to 0.8.20100211.5 fixed this issue for me. 

I fixed my GLib warnings by downgrading libglib2.0-0 and libglib2.0-data to 2.22.1-0ubuntu1, the newest one from karmic-updates (2.22.3-0ubuntu1) seems to be unstable. For those wondering how to do this, in synaptic highlight the package and under the package menu on the toolbar select force version (CTRL-E).

Hope this solves this for everyone.

---


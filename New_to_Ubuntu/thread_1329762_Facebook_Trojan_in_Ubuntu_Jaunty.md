---
title: "Facebook Trojan in Ubuntu Jaunty"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by alireza_shd on 2009-11-17
please help!!!
I use firefox and Tor to access facebook. 
my Ubuntu is up to date
but it seems I have a facebook Trojan
every time I log in to facebook all of my friends receive a wall post from me that lead them to a pass fishing site. 
how should I deal whit this Trojan?

---

### Post by Garyhans on 2009-11-17
Doubtful. My Friend.

---

### Post by Mrandersonjr on 2009-11-17
Open a terminal and:
Sudo apt-get install bleachbit

Then install it then run:
sudo bleachbit and check everything except for places in the firefox section and click delete.

---

### Post by Sealbhach on 2009-11-17
Install the Opera browser and see if the same thing happens when you use that.

.

---

### Post by The Funkbomb on 2009-11-17
Two things are more probable...

You used an easy to guess password or you fell for the same password phishing site that is spamming your friends.

---

### Post by dillandriskell on 2009-11-17
funkbomb may be right, you may not even be infected.

Just try changing your password first and see if you're still getting hacked after that.

---

### Post by alireza_shd on 2009-11-17
> **Sealbhach said:**
> Install the Opera browser and see if the same thing happens when you use that.

.
facebook is not accessible in my region so I must use a program such Tor. I cant make Tor work with opera. 

> **The Funkbomb said:**
> Two things are more probable...

You used an easy to guess password or you fell for the same password phishing site that is spamming your friends.

I have changed my pass twice!!!
the time of wall post is exactly as the time I log in to facebook

---

### Post by The Funkbomb on 2009-11-17
Did you try rkhunter and chkrootkit?

---

### Post by orethrius on 2009-11-17
Wait, why are you on Ubuntu?  Not to be snarky or anything, but did someone recommend it as a free alternative to Windows?  Correct me if I'm wrong, but this sounds suspiciously like a rogue Facebook app, where it's as bad an idea to blame Ubuntu for the breach as it would be to blame Windows.

Of course, as a technician, I have to wonder here, since Facebook apps authenticate through the central Facebook server and *maybe* some client-side JavaScript.  There's literally no way for them to jack an Ubuntu system without root access, since a. Linux flat-out doesn't properly recognize Win32 programs (without Wine, and that's a different kettle of fish entirely) and b. typical installation methods require root access.

On to the part where I try to diagnose the problem: have you installed any Facebook apps recently?  There are a few that seem pretty cool on the surface, but due to a lack of timely verification measures, get away with spamming and similar undesirable behavior.

[quote="The Funkbomb"]Did you try rkhunter and chkrootkit?[/quote]

Correct me if I'm wrong here, but wouldn't getting a rootkit in the first place typically imply that the user runs with root privs on a regular basis?  Even then, wouldn't the rootkit take actions "as appropriate" rather than "only upon logging into Facebook"?  Of course, I suppose a rootkit could be designed to behave this way, but given the laziness of the average cracker, which is more likely? :)

---

### Post by NickJones on 2009-11-17
And if your password is changed it doesn't mean your password cant be found, it's probably the same password you use for your email, and even this.

---

### Post by The Funkbomb on 2009-11-17
> **orethrius said:**
> Correct me if I'm wrong here, but wouldn't getting a rootkit in the first place typically imply that the user runs with root privs on a regular basis?  Even then, wouldn't the rootkit take actions "as appropriate" rather than "only upon logging into Facebook"?  Of course, I suppose a rootkit could be designed to behave this way, but given the laziness of the average cracker, which is more likely? :)

Take a look around at how many people ask how to disable that annoying password dialog they have to go through.

---

### Post by snkiz on 2009-11-17
Agreed its doubtful your Ubuntu is infected. However it is possible that Firefox has been  compromised. A bad extension, javascript, macros all are os independent for the most part. I'd suggest you create a new Firefox profile and see what happens. Use the command Firefox -p

---

### Post by orethrius on 2009-11-17
> **The Funkbomb said:**
> Take a look around at how many people ask how to disable that annoying password dialog they have to go through.

Oh believe me, I understand worst practices, but even not assuming best practices, shouldn't he hit a solid brick wall with a rogue Facebook app even if he's logged in as root (through no less than JavaScript controls and assumptions of Win32's presence)?

---

### Post by teward on 2009-11-17
*sigh*  are you SURE it's a Trojan?  Most of the trojans exist on Windows if they're on Facebook.

---

### Post by orethrius on 2009-11-17
> **TrekCaptainUSA said:**
> *sigh*  are you SURE it's a Trojan?  Most of the trojans exist on Windows if they're on Facebook.

I think that's where I'm going with my questions.  The resolution procedures for a rogue Facebook app aren't the same as the resolution procedures for an actual factual trojan. ;)

---

### Post by snkiz on 2009-11-17
These days so many infections depend on social engineering. If the OP is one of those people that complain about gksu no OS will save him/her. Still say try with a fresh profile, get the simple answers you have control over first. Then go after facebook or rootkits or whatever.

---

### Post by Garyhans on 2009-11-17
> **orethrius said:**
> Wait, why are you on Ubuntu?  Not to be snarky or anything, but did someone recommend it as a free alternative to Windows?  Correct me if I'm wrong, but this sounds suspiciously like a rogue Facebook app, where it's as bad an idea to blame Ubuntu for the breach as it would be to blame Windows.

Of course, as a technician, I have to wonder here, since Facebook apps authenticate through the central Facebook server and *maybe* some client-side JavaScript.  There's literally no way for them to jack an Ubuntu system without root access, since a. Linux flat-out doesn't properly recognize Win32 programs (without Wine, and that's a different kettle of fish entirely) and b. typical installation methods require root access.

On to the part where I try to diagnose the problem: have you installed any Facebook apps recently?  There are a few that seem pretty cool on the surface, but due to a lack of timely verification measures, get away with spamming and similar undesirable behavior.



Correct me if I'm wrong here, but wouldn't getting a rootkit in the first place typically imply that the user runs with root privs on a regular basis?  Even then, wouldn't the rootkit take actions "as appropriate" rather than "only upon logging into Facebook"?  Of course, I suppose a rootkit could be designed to behave this way, but given the laziness of the average cracker, which is more likely? :)
10-4 to that.

---

### Post by oldsoundguy on 2009-11-17
If you got this and filled it out .. you gave away your information yourself:
[http://voices.washingtonpost.com/securityfix/2009/11/spike_in_social_media_malware.html](http://voices.washingtonpost.com/securityfix/2009/11/spike_in_social_media_malware.html)

---

### Post by alireza_shd on 2009-11-17
rootkit gives two warnings on
 /usr/sbin/unhide 
 /usr/sbin/unhide-linux26

three days ago firefox stoped working properly ( when I used to try to open firefox some parts like favourites and history wouldn't load correctly) and I started using "sudo firefox" instead. sudenlly today it start to work as befor. 
this may be the origin on problem.

> **snkiz said:**
> Agreed its doubtful your Ubuntu is infected. However it is possible that Firefox has been  compromised. A bad extension, javascript, macros all are os independent for the most part. I'd suggest you create a new Firefox profile and see what happens. Use the command Firefox -p

the command "firefox -p" works perfect 
now how should I repair my firefox?


I really thanks you for answering to such a user like me.

---

### Post by juancarlospaco on 2009-11-17
> **alireza_shd said:**
>  fishing site. 


*Fish problems...?*  :popcorn:

---

### Post by NickJones on 2009-11-17
> **alireza_shd said:**
> 
the command "firefox -p" works perfect 
now how should I reaper my firefox?

I presume you meant repair, not reaper, AKA death,
-p just starts it with no addons, In Firefox, go to tools, Addons, and Un-Install any Extensions and Plugins you don't recognise, maybe give us a list and we can tell you the good ones and the bad ones.

---

### Post by snkiz on 2009-11-17
export your bookmarks from your old profile then delete it. When you open you new profile import you bookmarks. All of this can be done from within Firefox. There is other stuff you can import but seeing as we've established that your old profile is bad you don't really want to do that.

---

### Post by alireza_shd on 2009-11-17
add-ons: Adblock Plus, FoxyProxy Standard, ScarpBook, Tab scope, WebMynd
extensions: DownThemAll!, Torbutton, Ubuntu Firefox Modifications, User Agent Switcher
plugins: Default Plugin, Demo Print Plugin for unix/linux, DivX Web Player, QuickTime Plug-in 7.2.0, Shockwave Flash, VLC Multimedia Plugin, windows Media Player Plugin

---

### Post by snkiz on 2009-11-17
no the "p" option start Firefox's profile manager where you can create a fresh profile with no addons, history, javascripts, etc. The OP's problem most likely isn't an addon as they need confirmation to install from anywhere but Firefox's site. (but it could be.) Its most likely javascript.

---

### Post by doas777 on 2009-11-17
bottom line, if you seriously suspect, or can confirm infection, rebuild your os, and look carefully at any executables from your previous build that you plan to restore.

---

### Post by mdshann on 2009-11-17
> **alireza_shd said:**
> rootkit gives two warnings on
 /usr/sbin/unhide 
 /usr/sbin/unhide-linux26

three days ago firefox stoped working properly ( when I used to try to open firefox some parts like favourites and history wouldn't load correctly) and I started using "sudo firefox" instead. sudenlly today it start to work as befor. 
this may be the origin on problem.



the command "firefox -p" works perfect 
now how should I repair my firefox?


I really thanks you for answering to such a user like me.

Wow dude... sudo firefox? You ran firefox as root? That's the cause right there. Although you may have had the malware before when your favs and history weren't loading, running 'sudo firefox' likely allowed the malware that was in your original profile access to write to firefox files that nothing but root should have access to. Instead of just changing profiles I would go into synaptic and remove firefox via the purge method. I would then reinstall firefox.

This actually brings up any interesting idea... it seems that viruses that are targeted to  infect an application such as firefox instead of targeting the O/S are still able to gain a foothold! Kinda scary!!!

---

### Post by 3rdalbum on 2009-11-17
> **mdshann said:**
> This actually brings up any interesting idea... it seems that viruses that are targeted to  infect an application such as firefox instead of targeting the O/S are still able to gain a foothold! Kinda scary!!!

All the damage was limited to the user's Firefox profile. It doesn't seem that any other files in the home directory were touched. Firefox provides methods for plugins and the like to work with the Firefox profile the same way, regardless of operating system. It's not really a foothold - it's more like a little pinky-fingernail-hold.

Secondly, you misunderstood the poster - his problems vanished when he ran Firefox as root. It's still not a smart thing to do, for a number of reasons. In fact, I'd be surprised if the normal user profile still works now that it's become partly root-owned.

Thirdly, I'm wondering if it's possible that the problem exists at the exit node. I know, the Tor exit node should be randomized, but you never know.

---

### Post by doas777 on 2009-11-18
> **3rdalbum said:**
> 

Secondly, you misunderstood the poster - his problems vanished when he ran Firefox as root. It's still not a smart thing to do, for a number of reasons. In fact, I'd be surprised if the normal user profile still works now that it's become partly root-owned.

I find it more likely that the malware was fighting system constraints, and locking FF. then when it is run as admin, the malware can do whatever it was designed to, and thus does not hang FF. Not exactly a solution. more widening the crack in the damn.

---

### Post by mdshann on 2009-11-18
> **3rdalbum said:**
> All the damage was limited to the user's Firefox profile. It doesn't seem that any other files in the home directory were touched. Firefox provides methods for plugins and the like to work with the Firefox profile the same way, regardless of operating system. It's not really a foothold - it's more like a little pinky-fingernail-hold.

Secondly, you misunderstood the poster - his problems vanished when he ran Firefox as root. It's still not a smart thing to do, for a number of reasons. In fact, I'd be surprised if the normal user profile still works now that it's become partly root-owned.

Thirdly, I'm wondering if it's possible that the problem exists at the exit node. I know, the Tor exit node should be randomized, but you never know.

Actually I didn't misunderstand him. The problem with his favorites and history went away when he ran as root, but the issue with facebook did not. He was running it as root to fix the favorites and history problem, not the facebook issue. The facebook issue was still there when running as root. Running in 'safe mode' ie 'firefox -p' fixed the issue. So he needs to delete his profile and make a new one. Easiest way to do that and ensure that nothing outside the profile is compromised is to remove the package via the purge method and reinstall it.

---

### Post by snkiz on 2009-11-18
I believe you misunderstand a couple things. First the "-p" option for Firefox is for the profile manager, safe mode is this "-safe-mode" witch is used to run your current profile without extensions.
Second purging the Firefox package will not remove any files from your home folder, witch is where your Firefox profile is stored in /home/<username>/.mozilla/<firefoxversion>/<profilename>

knowledge is power, but half the knowledge is dangerous.

---

### Post by mdshann on 2009-11-19
So then what does purge do? Just curious, I don't want to be dangerous and all...

---

### Post by doas777 on 2009-11-19
purge rarely removes anything from the home dir, so if you purge it with apt-get, be sure to delete ~/.mozilla before reinstalling.

I feel I have to reiterate, if you seriously suspect a comprimise, then backup your content, and rebuild from scratch.

---

### Post by bwzz on 2009-11-19
I faced this before, I would suggest changing your password, and DO NOT save it in FF or ticking on "remember me/keep me logged in" box.

---

### Post by MaxVK on 2010-04-25
Sorry to resurrect an older thread, but I thought some may find it and also find this information useful/interesting:

> Warning:
Please DO NOT use sudo firefox. If you really need to run Firefox with administrative rights for whatever reasons, then use gksudo firefox instead. When you use gksudo it’s starts Firefox with administrative rights, but uses the root Firefox profiles, while sudo uses the user profiles, thus messing with the permission and preventing regular users from loading their profiles correctly. More info at [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Found on >[This Page]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1")< while researching a similar problem.

---


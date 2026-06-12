---
title: "Are installation scripts like Ubuntu Tweak dangerous?"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by juil on 2010-09-28
I read on the site below that installation scripts are dangerous:
[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Never-use-installation-scripts-like](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Never-use-installation-scripts-like)

I installed Ubuntu-Tweak about a month ago and haven't used it yet. Just yesterday, I tried installing Gnome-DO, then later realized that it is not available for Lucid. 

When I checked Ubuntu-Tweak after reading the info on the website, I found that Gnome-Do was available and ready to install...
One thing I disagreed though was that using Sources List Generator is dangerous. I'm saying this because it would be dangerous to people who don't know what they are doing. But after using the generator to make the list, you could check the repository address to make sure your not downloading from some insecure third party repository no?

---

### Post by linux-hack on 2010-09-28
if you downloaded the ubuntu tweek from ubuntu repos it means is secure to install it. if not check the md5sum of you package from the original webpage. And it not dangerous to install it. It is thought to do things you don't understand what they are meant for. And if you do dangerous stuff on your pc it is your responsibility and don't blame it on the software.

---

### Post by NikoC on 2010-09-28
I have been using Ubuntu Tweak for a couple of weeks now and haven't had a problem so far with my Ubuntu (10.04) installation. I installed tweak from the Ubuntu repos.

---

### Post by Paqman on 2010-09-28
> **juil said:**
> I read on the site below that installation scripts are dangerous

They can be, depending on how well they're written.

In general, helper apps like Ubuntu Tweak have had a very poor track history. Not so long ago everybody was using Automatix to do the same things, and that was a truly horrendous piece of software.

The problem is that by installing extra repos and such, users end up straying outside trusted sources of software, usually without knowing. If a script decides to add some 3rd party repo, how do you know it's safe? Does the script even tell you that it does this? How stable is the software in the repo it adds?

I'm not saying Ubuntu Tweak suffers from any of the same problems that things like Automatix did, as i've never used it and don't know how it works under the hood. This is just a general caveat about the risks of using "helpful" scripts to install packages. Treating them all with a healthy degree of suspicion is prudent, and best practice would be indeed to avoid using them.

(And having given out this sage advice, I might just go back over my own Perfectminimal script and make sure it's a lot more up front about any 3rd party sources it uses...)

---

### Post by Elfy on 2010-09-28
Automatix morphed into Ultamatix ... I'd not go there.

Computer janitor does what it says - it's up to the one using it to make sure that it's not going to remove something that you want to keep. 

Never bothered much with ubuntu tweak. I've used a source list generator though - that was fine.

---

### Post by Soul-Sing on 2010-09-28
> i'm not saying ubuntu tweak suffers from any of the same problems that things like automatix did, as i've never used it and don't know how it works under the hood. This is just a general caveat about the risks of using "helpful" scripts to install packages. Treating them all with a healthy degree of suspicion is prudent, and best practice would be indeed to avoid using them.

+1

---

### Post by beew on 2010-09-28
I read that too. There are some people who think that even going out of the street is dangerous because you may get run over by cars so they huddle in fear at home.That is the impression I have of this guy, don't install anything, just stick with whatever Canonical gives you even if softwares may be very outdated  and buggy, do minimal things, live a minimal live and have minimal risk and you will be "safe", it is kind of like the "abstinence" school of safe sex.  

I don't take these kind of people and their advice seriously, I would rather mess up my system than to use my computer like that, at worst I will do a clean install, you probably have to do that every 6 months anyway if you want to upgrade your softwares in the 'official' way since OS upgrades apparently fail a lot based on troubles reported on these forums.

---

### Post by Paqman on 2010-09-28
> **beew said:**
> OS upgrades apparently fail a lot based on troubles reported on these forums.

A bit off-topic, but they did used to be pretty unreliable. Not so any more. Unless you've got a very oddball system you should have no trouble upgrading. People just parrot the old advice of avoiding upgrades without actually trying it for themselves.

---

### Post by beew on 2010-09-28
Ubuntu tweak is very helpful. By all means use it. I agree that we should be skeptical, especially towards those who tell you every third party app is dangerous, either because they are very fearful individuals or because they know how to do these tasks by command lines and you don't so they can feel superior about it. Mess around and learn, worst is you need to clean install, big deal, I wish we can just clean install when things screw up in life. :)

Pagman

> The problem is that by installing extra repos and such, users end up  straying outside trusted sources of software, usually without knowing.  If a script decides to add some 3rd party repo, how do you know it's  safe? Does the script even tell you that it does this? How stable is the  software in the repo it adds?Three cheers for "straying" outside trusted sources. I install a bunch of PPAs to keep my softwares up to date and fresh. 

If I stick to "trusted" repo some of my softwares wouldn't even run because of bugs and the rest would be very outdated or dysfunctional,--the document viewer from Maverick is much better than the old version in Lucid, petty those who don't stray away from trusted source and have to put up with that for three years. Linux means freedom to customize and configure and getting the software features I want or need is a large part of that. If I want to be a sheepo with my software needs dictated by the OS I would get a Mac.

For those who use a lot of PPAs Ubuntu Tweak's ppa  purge feature is particularly helpful. There is a risk that some packages installed from PPAs may result in conflicts and ppa purge lets you downgrade them safely.  It is very helpful if you are not a command line jock who can whip up a script for that on the spot. 

(Come to think about it, maybe that's why some people warn you against UT; it allows the novice  to take risk unpunished. It's like religious people  lie about condoms  being full of holes because condoms allows you to have sex and get away with it)

---

### Post by Paqman on 2010-09-28
> **beew said:**
> 
Three cheers for "straying" outside trusted sources. I install a bunch of PPAs to keep my softwares up to date and fresh. 


There's absolutely nothing wrong with adding PPAs, but there's a big difference between deliberately adding a source you've located yourself and having it silently added for you (possibly without even being aware of it). Helper scripts often do the latter. I admit that i've been guilty of writing scripts like this myself, and will definitely try and be a lot more transparent in the future.

---

### Post by beew on 2010-09-28
> **Paqman said:**
> There's absolutely nothing wrong with adding PPAs, but there's a big difference between deliberately adding a source you've located yourself and having it silently added for you (possibly without even being aware of it). Helper scripts often do the latter. I admit that i've been guilty of writing scripts like this myself, and will definitely try and be a lot more transparent in the future.

I am not sure that UT does that. It has an add ppa feature but  it only presents a list for users to choose from, nothing is hidden. I don't use it though. I would prefer to go to launchpad and add them myself because I would like to find out a bit more about the ppa before I add them,--like what packages are in the repo, when was the last update and so on.

---

### Post by juil on 2010-09-28
I appreciate all your comments!
I've grown to love the method of installing apps from synaptic as it shows which dependencies it will be installing, and it's more secure. I also like seeing the repository added to my sources.list as well. Doing all this gives assurance that your doing it properly. 

But using UT gives me the feeling that I'm just telling someone to install a program on my computer without knowing how he's doing it. At the same time, I get tempted to do it, because it's just so quick. Most of the apps seem trust-able, but when it comes to themes like shiki-colours, I cant help the feeling of when I used to own windows and would install themes by executing some .exe file I downloaded. Would you guys recommend adding themes yourself or do you think it's still ok to use UT to do it?

---

### Post by Paqman on 2010-09-28
> **juil said:**
> Would you guys recommend adding themes yourself or do you think it's still ok to use UT to do it?

Shiki-colors is in the repos, so that's the best way to get it. Otherwise i'd say using something like Ubuntu Tweak isn't any more risky than downloading something off Gnome-look.org and adding it yourself.

---

### Post by beew on 2010-09-28
> **Paqman said:**
> A bit off-topic, but they did used to be pretty unreliable. Not so any more. Unless you've got a very oddball system you should have no trouble upgrading. People just parrot the old advice of avoiding upgrades without actually trying it for themselves.


Well I don't know what you mean by an odd ball system. Many people have proprietary drivers installed and that is enough to cause some problems. For example, I lost graphic when I rebooted after upgrading to Maverick from Lucid.  All I saw was a terminal without any instruction of what to do next. I think the update removed the Nvidia driver without installing any substitute. Now I had thought of that possibility before so I had some tutorials saved in my other computer for the occasion. But I was too lazy to look them up so I just did a clean installation of Maverick instead. Luckily that was a trial installation on an old PC, I was just trying to see how update works so no loss. But imagine some newbie trying to follow the advice  of  only upgrading softwares through upgrading the whole OS every 6 months because it is more "secure" then only to find himself facing a terminal on reboot with no clue what might have happened.

---

### Post by beew on 2010-09-28
> **juil said:**
> I appreciate all your comments!
I've grown to love the method of installing apps from synaptic as it shows which dependencies it will be installing, and it's more secure. I also like seeing the repository added to my sources.list as well. Doing all this gives assurance that your doing it properly. 

But using UT gives me the feeling that I'm just telling someone to install a program on my computer without knowing how he's doing it. At the same time, I get tempted to do it, because it's just so quick. Most of the apps seem trust-able, but when it comes to themes like shiki-colours, I cant help the feeling of when I used to own windows and would install themes by executing some .exe file I downloaded. Would you guys recommend adding themes yourself or do you think it's still ok to use UT to do it?

If you download and install  a .deb file the dependencies will be taken care of as well (the program manager will go online to fetch the dependencies). It will be integrated into the software manager just like other programs you install from the repos or ppas. The only thing is that they don't get automatically upgraded (so they are under the section "local or obsolete" in Synaptic) But then if you stick to the official repos things don't get updated anyway, it is not very common that you will need security update  for some small utilitie and  they don't get bug fixes,-- there are some unusable programs in the repo  because of bugs and some are so outdated that the developers basically tell you don't even bother to install from the official repos. So you may as well down load the .deb files and update them  manually instead of using a probably already outdated version in the official repo waiting for 6 months to three years just to get less outdated. For most end user softwares I try to get them from PPAs as far as possible. 

The only things that are not incorporated into the software manager would be commercial softwares.

---


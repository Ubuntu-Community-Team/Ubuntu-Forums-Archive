---
title: "software versions"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by beew on 2010-09-03
Hi,

I am currently running Ubuntu 10.04 and I have just created a live usb for Ubuntu 10.10. I notice that many programs have newer versions in the the 10.10 repositories. I am wonder what happen to 10.04? Will the softwares be updated accordingly or am I stuck with old versions for a while even though the 10.10 versions have been updated?

---

### Post by mikewhatever on 2010-09-03
No. The programs will keep their versions, except for a few exceptions. That's the way Ubuntu and most of other distros work.

---

### Post by inameiname on 2010-09-03
Typically each version of Ubuntu freezes versions in their repository after a little while, so unfortunately, yes, you will have to find a PPA or other repo to install the software to newer versions. This doesnt' include Ubuntu specific packages of course, but things like Gnome, Linux kernel (Lucid won't pass 2.6.32), Firefox (usually, though it did get a few updates due to Lucid being a LTS release), and etc. 

Anyway, if you want to install the latest versions of stuff, try PPAs. I use quite a few that bring about all sorts of improvements and updates my way. Check out Ubuntu-Tweak for an easy way to install several more trustworthy ones if you'd like. 

Sadly, you can't just add the repositories from 10.10 and upgrade your 10.04 release with them as there are dependencies issues and all sorts of other things that arise that'd mess you computer up if you don't know what you are doing.

---

### Post by beew on 2010-09-03
inameiname,

Thanks. I too use a lot of ppas and have downloaded and install quite a few .deb files.  I find a lot of the softwares in  the repo are terribly outdated and bugs don't get fixed. When people talk about the convenience of the repos they don't usually mention that. I always knew that updates are kind of slow in the repo, but I didn't know that they actually freeze them. From now on I will install all softwares by ppas if I can find them.

So what is the meaning of LTS? Does Ubuntu expect users to be e stuck with outdated and buggy softwares for three years just because it is more "stable" and "secure"?? This sounds really stupid, like turning your house into a prison so the bad guys cannot come in.

---

### Post by 3rdalbum on 2010-09-03
> **beew said:**
> inameiname,

Thanks. I too use a lot of ppas and have downloaded and install quite a few .deb files.  I find a lot of the softwares in  the repo are terribly outdated and bugs don't get fixed. When people talk about the convenience of the repos they don't usually mention that. I always knew that updates are kind of slow in the repo, but I didn't know that they actually freeze them. From now on I will install all softwares by ppas if I can find them.

So what is the meaning of LTS? Does Ubuntu expect users to be e stuck with outdated and buggy softwares for three years just because it is more "stable" and "secure"?? This sounds really stupid

You don't quite understand.

Ubuntu is a commercial distribution. It's suitable for home users, but Canonical is also trying to get businesses to adopt it (many businesses do use Ubuntu). In business, you can't just have new versions of programs popping up on people's computers. Imagine if you were a system administrator and one morning you got fifty frantic phone calls from users saying that a button they use in their software has moved and they can't find it; or that there's a new bug that wasn't there before.

Ubuntu's software is "stable" - not stable as in "won't crash" but stable as in "won't change". You get bug fixes and security fixes where possible, but you won't get new features.

The PPAs system is partly designed for home users who want to run a stable version of Ubuntu but have the latest software. With Ubuntu 10.10, Canonical are introducing a new repository where upstream program developers can get the later versions of their software into an existing stable version of Ubuntu; this will be opt-in.

---

### Post by mastablasta on 2010-09-03
> **3rdalbum said:**
> You don't quite understand.
 
Ubuntu is a commercial distribution. It's suitable for home users, but Canonical is also trying to get businesses to adopt it (many businesses do use Ubuntu). In business, you can't just have new versions of programs popping up on people's computers. Imagine if you were a system administrator and one morning you got fifty frantic phone calls from users saying that a button they use in their software has moved and they can't find it; or that there's a new bug that wasn't there before.
 

 
 
Which brings us to security &stability - if a programme gets it's bugs fixed a holes filled should it be updated?
 
system administrators (at least in windows) go through updates and users get what they need. the important ones. such as browser updates, programme updates... even on a system as old as WinXP this is done constantly. for example in my company users received Office updates, main production programe updates, security updates,flash updates...
 
 
in linux oyu owuld be stuck with old and perhaps even not secure.

---

### Post by QLee on 2010-09-03
[QUOTE=mastablasta]...
 
in linux oyu owuld be stuck with old and perhaps even not secure.[/QUOTE]

No, versions get a "feature" freeze, security upgrades happen as long as the version is supported.

"Old", in this case  meaning not the newest (and possibly buggy) version of an application but one that has been shown to work. ...and which doesn't create "support nightmares" for the sys admin.

---

### Post by beew on 2010-09-03
3rdalblum

> Ubuntu's software is "stable" - not stable as in "won't crash" but stable as in "won't change". 

Wow! Who would have thought of that when they tell you as if it is such a great thing.

So I shouldn't have gone for LTS and definitely will switch to 10.10 in October. _It sounds mightily stupid that you have to upgrade the whole OS in order to get new software features _(not all softwares are available in ppas) and from what I read in this forum  upgrading Ubuntu is very tricky. 

When I tried out Maverick I was shocked that Evince has gotten so fast. Here I am always complaining that it is crap, not knowing that I am stuck with an ancient version. 

So much about Linux being "rock solid", solid as in inflexible. So much about not having to go online to look for softwares. 

I hope that experienced users would be more upfront about this drawback of the repository system when they tell newbies about its convenience.

> Imagine if you were a system administrator and one morning you got fifty frantic phone calls from users saying that a button they use in their software has moved and they can't find it; or that there's a new bug that wasn't there before.

You don't have to update if you don't want to. You can put a program's update on hold with gjig for example. I am sure there is a way to do it in batch. So this is not a valid reason to deny feature updates to those who do want them.

> With Ubuntu 10.10, Canonical are introducing a new repository where upstream program developers can get the later versions of their software into an existing stable version of Ubuntu; this will be opt-in.


I am looking forward to that. They should have done it long ago. But I now I am going to have to do a few fresh installs in October just to get rid of Lucid. It is going to be a pain since I have spent so much time on customizing my systems.

---

### Post by beew on 2010-09-03
OK, just to make sure I get it right. Instead of updating the repositories in an existing version of Ubuntu every 6 months they would rather release a new version of Ubuntu and if you don't upgrade you are stuck with old softwares forever?!!

It doesn't make any sense.

---

### Post by tgm4883 on 2010-09-03
Actually, it makes perfect sense. New features can introduce new bugs. As said before, security patches do come down in stable releases.

---

### Post by beew on 2010-09-03
> New features can introduce new bugs

It can also fix old bugs, and there are also stable and unstable releases and you don't have to go for the unstable ones.

No, it doesn't make any sense, it is like saying if you go out you may get run over by cars so you lock yourself in.

---

### Post by tgm4883 on 2010-09-03
> **beew said:**
> It can also fix old bugs, and there are also stable and unstable releases and you don't have to go for the unstable ones.


No it cannot. Adding features is different than fixing bugs. As previously stated, patches can still be applied to stable releases.

> **beew said:**
> 
No, it doesn't make any sense, it is like saying if you go out you may get run over by cars so you lock yourself in.

You aren't very good at analogies. It's more like saying you can't roll down the windows in your car (bug), so you want to upgrade to add a spoiler (feature) and somehow that spoiler will make your windows roll down.

---

### Post by uRock on 2010-09-03
Bugs? What bugs? :D

I plan to stick with Lucid for the next few years on most of the family machines. If I need a newer version of something, then I will install it from source, such as the newer Thunderbird I installed for usability with the Lightning extension. Very few of the newer programs offer anything other than a changed look.

---

### Post by beew on 2010-09-03
> You aren't very good at analogies. It's more like saying you can't roll down the windows in your car (bug), so you want to upgrade to add a spoiler (feature) and somehow that spoiler will make your windows roll down.

There is always risk in life and your approach is to avoid risk at all cost, so you won't open your windows even if everyone in the car is suffocating to death. My analogy is a good one, but I don't mind using yours.

Strange that you think of new features basically as "bugs".

---

### Post by uRock on 2010-09-03
I think he means that the new features don't fix the old bugs. But depending on the application a new feature may cause many new bugs.

---

### Post by beew on 2010-09-03
> If I need a newer version of something, then I will install it from source, such as the newer Thunderbird I installed for usability with the Lightning extension. 

Fine, but how is installing from source a fast and convenient way to install programs? If you are at it you can also create your own features if you know how to, it is open source afterall, right?

One click from Synaptic instead of go looking for .exe files on the net is something people constantly harp on about how user friendly Ubuntu is.

> Very few of the newer programs offer anything other than a changed look.

Maybe only the programs you use. Like I said, one simple thing is Evince. The version in the 10.04 repository is crappy. It is slow and takes up lots of resources but I can't believe how smooth it has become in Maverick and there has been several versions in between that I am not aware of. There are many little things like that which together enhance the computing environment.

---

### Post by tgm4883 on 2010-09-03
> **beew said:**
> One click from Synaptic instead of go looking for .exe files on the net is something people constantly harp on about how user friendly Ubuntu is.

I'm not sure, are you here just to complain about 10.04? We've already told you that patches can be backported and that there are PPA's if you do want a new version of the software. We have also pointed out that in 10.10, there is a new feature to get new versions into the stable release.

---

### Post by uRock on 2010-09-03
Opening a PDF is going to be heavy. It smells of Adobe. 

As for convenience, Ubuntu is not a rolling release, which is why they do not force people to upgrade their apps when the vendor comes out with a new version, which usually means the ubuntu guys will also have to upgrade the dependencies provided in the repo and will end up being a rewrite of everything but the kernel itself.

Some people prefer to stick with what works, look at the XP lovers. 

Installing a deb is really easy and installing a tarball is not very hard, though not easy for people who aren't terminal users.

---

### Post by beew on 2010-09-03
> I'm not sure, are you here just to complain about 10.04?

I come to ask a question about software versions (see the title of the thread) and get an answer. I commented on the answer and you keep the conversation going by offering some lame disagreements. 

So I am here to respond to you, why you are here only you know.

---

### Post by uRock on 2010-09-03
The answer is that Ubuntu only upgrades software in the repos if there is a security issue with an older version.

Ubuntu is not a rolling release, which means you have to either wait for the next release to get the newer apps or install them yourself.

---

### Post by tgm4883 on 2010-09-03
> **beew said:**
> I come to ask a question about software versions (see the title of the thread) and get an answer. I commented on the answer and you keep the conversation going by offering some lame disagreements. 

So I am here to respond to you, why you are here only you know.

:roll: you win. I'll take my "lame" disagreements somewhere else. ):P

---

### Post by beew on 2010-09-03
Urock

> Opening a PDF is going to be heavy. It smells of Adobe.

Not necessarily. Have you tried Foxit? The newest version of Evince is not bad either. I don't use Adobe, not on Windows, not on Linux.

> Installing a deb is really easy and installing a tarball is not very hard, though not easy for people who aren't terminal users.


It is not hard and ppa's are great (though that is frowned upon too by people who are "bug" phobic). There are workarounds and I know that. But the very idea of freezing new features in the repo by default is still nonsensical. The repo is a great way to get softwares and I am sure most Ubuntu users primarily get their softwares from the repo and only use ppas, download .deb files or compile from source occasionally if at all.

---

### Post by uRock on 2010-09-03
Then A rolling release, such as Arch or Debian testing, may suit you better.

---

### Post by mastablasta on 2010-09-03
> **uRock said:**
> 
Some people prefer to tick with what works, look at the XP lovers. 


XP lovers can update their programmes without updating the system.

I forgot about the PPA... 

It is good to hear that Ubuntu will have it possible to upgrade the programmes. it's just a bit strange that this is not included in LTS, which i planned to use for the 3 supported years.


BTW as an example of why upgrade i can give you the time when i had the issue with IM clients. i've noticed the issue was resolved in 10.04, but i wasn't prepared to move yet. so i had to use the PPA, otherwise i wouldn't be able to use the funciton i needed. PPA is an option but far from being user friendly. It is easy once you know how to add it, but a nice graphical interface would be better.


btw just yesterday i saq Win APT . some guy actually made APT for windows to make it easier to update the software ;-)

---

### Post by inameiname on 2010-09-03
To Beew from way up in the thread,
 

 As mentioned, PPAs are good if you want to get more up-to-date software, but there's of course a warning too, as you have to have a little faith in the particular PPA having decent versions of the packages, and/or that the latest package versions aren't full of new bugs. This is why there is a feature freeze in Ubuntu versions, as once stable as much as they can get, why cause more issues in a stable release? There are of course some things that they do test and test and eventually add to s stable release to fix bugs and whatnot. And I hear ya on LTS. Long term support can mean a lot of things, and I guess it means they are just trying to provide support, however much, longer than most of the versions. There's a point, I know, when you have to question if stable and secure and/or old is more preferable.
 

 3rdalbum is right in his previous posting up there. PPAs are merely for those home users wishing to upgrade. You can't expect Ubuntu and it's partners to update everything all the time, as, as he said, there'd be tons more issues with people having issues with either new features or bugs. Or whatever.  
 

 In all, I figure for those that seriously want the most up-to-date packages, simply install the latest Ubuntu version and use PPAs. And for those that want the most secure and stable, use the feature freeze older Ubuntu versions. It's that simple. Some people prefer the former, while others prefer the latter. It's why some folks are still using Ubuntu Edgy or Hardy or something, while others are using Maverick's Beta.
 

 As mastablasta was talking about, XP users can soup up their computer without upgrading their system. And if you ask them why they haven't upgrading to Vista, or even 7, they'd say they like the stability and the feature set in XP. So long as it can install and use the most recent applications and whatnot, if it's something they like, who cares if it's not updated? :P

---

### Post by uRock on 2010-09-03
> **mastablasta said:**
> XP lovers can update their programmes without updating the system.
I meant by the fact that they won't let XP go. And they have to go out and buy their software, which takes a lot longer than running a few commands to install a tarball in Ubuntu. The reason they stay is that they feel it is stable, some people never had it crash except for crashes caused by operator error. I know the only BSOD I encountered was from my own doing. And I know people who stayed with IE6 until after 8 came out. Some people prefer the stability of the old.

I am sure the OP's argument will come up even more often in a year from now, but the answer will be the same.

---

### Post by beew on 2010-09-03
inameiname

> As mentioned, PPAs are good if you want to get more up-to-date software, but there's of course a warning too, as you have to have a little faith in the particular PPA having decent versions of the packages, and/or that the latest package versions aren't full of new bugs. 

I hear you. I try to be careful as much as I can. There are some quite notorious PPAs' that one should stay away from like the vlc one by c korn. :)

---

### Post by beew on 2010-09-03
urock

> I meant by the fact that they won't let XP go.

One reason maybe that you have to pay quite a bit to let XP go. :)

---

### Post by uRock on 2010-09-03
> **beew said:**
> urock



One reason maybe that you have to pay quite a bit to let XP go. :)
I know a few people who have used the downgrade rights to go to XP from Vista and 7. I get the all for free, legally.

---

### Post by beew on 2010-09-03
Ok, I have installed the Maverick version of Evince in my Lucid box. I add the Maverick repository. Check all the dependecies to make sure that installing them would not remove anything that already exists. Use sudo aptititude instead of sudo apt-get to install Evince to make sure that I can remove it and all its dependencies if I have to. Then delete the Maverick repository by unchecking it in my source list. So far works like a charm, nothing is broken.

---

### Post by beew on 2010-09-03
> I know a few people who have used the downgrade rights to go to XP from Vista and 7. I get the all for free, legally.

That is true. Windows 7 apparently is incompatible with some older software (which may involve quite a bit of investment) and vista is known to be crap. Moreover, I have seen a few netbooks preinstalled with vista and they are just slow. I heard netbooks with Windows7 are slow too, not have enough resources to run the hungry OS.

---

### Post by mikewhatever on 2010-09-03
> **beew said:**
> Ok, I have installed the Maverick version of Evince in my Lucid box. I add the Maverick repository. Check all the dependecies to make sure that installing them would not remove anything that already exists. Use sudo aptititude instead of sudo apt-get to install Evince to make sure that I can remove it and all its dependencies if I have to. Then delete the Maverick repository by unchecking it in my source list. So far works like a charm, nothing is broken.

Nah, it's crap and buggy, and will become ancient in just a few month, don't get stuck with it. :p

---

### Post by beew on 2010-09-03
No, contrary to what some of you said, even with Maverick you still won't get feature updates in the repo, PPA is the way to go.
[http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html]("http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html")

It is patently absurd that you can't get updated softwares in the repo unless you upgrade the whole OS, which is likely to break something especially if you have third party programs installed. How about you getting some new hardware and they say, sorry, Ubuntu won't support gadget xyz because the supporting softwares in the repo is three year old?

---


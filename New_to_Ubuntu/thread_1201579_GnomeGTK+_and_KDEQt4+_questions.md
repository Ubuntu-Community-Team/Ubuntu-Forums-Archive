---
title: "Gnome/GTK+ and KDE/Qt4+ questions"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-01
I'm sorry if I am going to be vague but it is because I am confused. So I know GTK+ is the toolkit for GNOME and Qt is the one for KDE but beyond that, how does that affect a users decision to install from different programs?

Opera is not a KDE program right? but it still uses Qt right? So if I install Opera on Ubuntu, it will download qt libraries but not the KDE libraries? 

Also VLC seems to want to download a whole lot of Qt if I try to install it, despite being marked as both a GNOME and KDE player.

Initially, I thought installing KDE apps would pull in all the kde libraries and QT is a major PART of these KDE libraries. Obviously thats not right is it? QT libraries and KDE libraries are different things altogether and some programs might pull in support for one but not the other?

Hope you can make sense of that rambling :D
Thanks a lot.

---

### Post by ~sHyLoCk~ on 2009-07-01
You can just go to their {opera and vlc} respective websites and download the .deb packages and install them in your system.

---

### Post by Andy06 on 2009-07-01
Yeah I know that :D. My question was leaning more towards the relationship between GNOME using GTK+ and KDE using Qt+ and the differences between when both the KDE and Qt+ libraries are needed for an app and when only Qt or only KDE are needed. For example Opera and VLC pull in only Qt+ support but not KDE libraries whereas a lot of other KDE programs pull in KDE libraries. Why is this so and is there any basis or way to figure out when this will be the case and when it won't be the case?

Hope I've been a bit clearer (though I think not :D)

---

### Post by Andy06 on 2009-07-05
Anyone? Pls explain the differences :D

---

### Post by shae on 2009-07-05
GTK and QT are simply Graphical Toolkits.  They are what produce the buttons and scroll boxes and so on.  Gnome-native apps use GTK and KDE native apps use QT.  But some gnome apps use libgnome and other gnome libraries while some KDE apps use libkde and other kde libraries.  

You can use GTK in KDE and QT in Gnome.  You can even use kde apps in Gnome and visa versa, but these programs will require the installation of the related libraries to run.

Rather than thinking of GTK being for Gnome and qt for kde, it is the other way around.

Personally, I try to use only GTK apps in gtk based, while in kde, you have to basically use both gtk and qt.

See, when a program is written, the author uses certain libraries to obtain what he wants.  For example he may use qt or gtk to write the gui.  Then to run or compile the program, you need these libraries.

When you install a package from the repository, the package depends only on the libraries it needs to run.

So in conclusion: qt does not need kde, but some qt apps require both qt and kde libs.  gtk does not need gnome, but some gtk apps requre both gtk and gnome libs.

---

### Post by Andy06 on 2009-07-05
Thanks for that. Was very well explained.

I know Linux is all about choice and I read the history of both of them so I know why they came into being but is one getting dominant over the other (or is expected to in the future?)

Also what do Windows programs generally use? What about popular programs like Firefox (the non linux versions), Opera (I think Qt) etc, is there any way to find out which toolkit any given program uses since they don't really mention it on the home pages.

---

### Post by shae on 2009-07-06
Neither GTK nor QT are becoming dominant.  They will both continue to exist and be used for a long time to come.

Well in windows there are also several toolkits such as win32 and .NET.

Firefox uses its own toolkit with gtk functions in linux and windows ones in windows.  Opera may use QT in all its versions.  Usually you might be able to tell from the way it looks, but generally there is no foolproof way to figure out which is being used.

---

### Post by Andy06 on 2009-07-06
Wouldn't standardisation help here?

I mean choice is nice but this is not so much of a choice since you can change themes, UI etc and the actual toolkit does not make as big a difference as what you do with it.

As an analogy, choice is good while buying cars (desktop environments) but it does not really matter what brand of engine oil you use, it all functions the same way.

Thanks a lot.

P.S i read the history so I know why GTK+ came into being and how Qt wasn't always free and all but are they now working towards standardisation or are both camps happy?

Thanks a lot

---

### Post by Mornedhel on 2009-07-06
> **Andy06 said:**
> Wouldn't standardisation help here?

Linux newcomers often ask this, or a variant of this, for instance "why are there multiple distributions and wouldn't it be better if there was only one ?".

The answer is basically : all those different applications came to be because they fulfilled someone's need better than others, and then some more people started using them, and now they just coexist because they all do *something* better than the others. I wouldn't want to use KDE. My imaginary neighbor wouldn't want to use Gnome. We're both happy with our desktop environments. Well, we both have criticisms, but surely our DE is better than our neighbor's, right ?

Applications that are Pareto-dominated (ie, in no respect better than another) slowly die, but you still have to factor in the users who use them for old time's sake. I'm willing to bet there are still a few ed users around.

> **Andy06 said:**
> P.S i read the history so I know why GTK+ came into being and how Qt wasn't always free and all but are they now working towards standardisation or are both camps happy?

Not at all. Some do indeed propose unification, but mostly there's no chance of that ever happening. With the recent KDE 4 release and Gnome 3 incoming, there's even more competition.

---

### Post by Andy06 on 2009-07-06
No I won't ask why we don't have one distribution mainly because the differences between them are vast and they obviously serve a different purpose :D

Having said that, 90% of linux distros are not worth looking at, not because they are horribly bad but because, despite being different, they aren't really better or ACTUALLY that "different" from the best 10%. And I don't mean best by market share or popularity but by their ability to fulfill their goals.

For example, there are nearly half a dozen major distros which aim for a general audience and pretty much have the same goals as ubuntu, I see that as semi-useless choice, Ubuntu can replace them and be better at their intended function than them. I say only semi-useless because I am fine with their existence because they don't get in anyone's way do anything counter productive. Then there are Gentoo and Arch, distros much smaller than the afore mentioned half dozen yet I consider them vitual, they are different enough to be critically important since what they provide is very unique. Thats worthwhile choice (even though I will never ever touch Gentoo or Arch since I am just not that kind of user):P

However, with GTK and QT, they don't make much of a difference to the user experience and both are more of enabling technologies which enable something else to exist rather than existing as an end in themselves.

Choice is good, too much choice is definitely bad. Choice for the sake of choice however is just downright messy :D

I'm not saying GTK and QT is too much choice and I totally get your point about how open source projects can go on for ages with virtually no market share or awareness simply because they might be pet projects serving a niche (or very very small niches;)) and thats not a problem. The mainstream will learn to ignore 90% of anything open source because a lot of it is made for personal use or to satisfy very particular needs. The other 10% of projects will be the ones to actually impact 90% of users.

The problem I sort of see with GTK and QT is that the DIFFERENCE in this choice to the user is virtually nothing. If one disappeared, no one would notice or care, the other is almost a perfect substitute or can be with some minor work. However, the existence of both stands in the way of users almost every day when they decide they won't install apps built on the other one because they don't want all the extra libraries, dependencies and cruft. Sure it's a end user decision but I'm sure every user on this forum has at one time or another, used at least one less than ideal app because their absolute favorite was built with the other toolkit. I know I have.

I mean Ubuntu/Arch Linux/Gentoo/Debian/Fedora I can see the difference, I can feel it, I can imagine someone else might like the others. GNOME/KDE/XFCE/LXDE/Enlightenment etc again I can see the difference, its perceivable. But then when you have to make a choice between usplash and splashy, it's like.......who cares. Only interested in the end product and both are capable of ultimately the same sort of results with similar efforts. 

Its all fine if it serves a purpose and doesn't get in anyone's way. But with GTK and Qt, I find it getting in the way of people everyday. Am I a bit off with the assessment? :D 

What do you think?

---

### Post by Mornedhel on 2009-07-06
> **Andy06 said:**
> No I won't ask why we don't have one distribution mainly because the differences between them are vast and they obviously serve a different purpose :D

Having said that, 90% of linux distros are not worth looking at, not because they are horribly bad but because, despite being different, they aren't really better or ACTUALLY that "different" from the best 10%. And I don't mean best by market share or popularity but by their ability to fulfill their goals.

For example, there are nearly half a dozen major distros which aim for a general audience and pretty much have the same goals as ubuntu, I see that as semi-useless choice, Ubuntu can replace them and be better at their intended function than them. I say only semi-useless because I am fine with their existence because they don't get in anyone's way do anything counter productive. Then there are Gentoo and Arch, distros much smaller than the afore mentioned half dozen yet I consider them vitual, they are different enough to be critically important since what they provide is very unique. Thats worthwhile choice (even though I will never ever touch Gentoo or Arch since I am just not that kind of user):P

Well, 90% of distributions are remixes of a larger one, or built from scratch. In either case, they're tailored to a niche. Beginners won't even notice them (hopefully). Advanced users, if they do notice them, are presumably looking for something specific. Arch, Crunchbang, Puppy, all of those started as niches, and enough people liked them and said it that they evolved into larger contenders. They weren't even "the best" at what they did (DSL is *still* the smallest distribution around), just "good enough for me". Heck, Ubuntu started as a niche. It fulfilled a need and it grew up. Wasn't very stable at the beginnings, too.

Let's review the larger distributions, and please tell me if I forget one :

Debian -- Made .debs popular, has a dev cycle that fits users and servers both, a bit too open source nazi for some tastes. Ubuntu still can't compete with a vanilla Debian Stable as far as servers are concerned.
Fedora and RHEL, former Red Hat -- Used to compete with Mandrake for users, was a bit less user friendly, catering more to advanced users. Ubuntu still can't compete with RHEL as far as enterprise use and support are concerned.
Mandriva, former Mandrake -- Used to compete with Red Hat, was a bit more user friendly. Also has tech support, but Mandrakesoft is maybe overall a bit less focused on enterprise use even nowadays. Had advanced and friendly configuration (drake) and package management (urpmi) before Red Hat did.
Gentoo -- Relatively recent, appeals to those that like having everything tailored to their needs. Gentoo users will overall not like having to switch to Ubuntu, which uses precompiled binaries, and has a completely different community.
Slackware -- Has a history of being user-hostile, and they like it that way, I think. It's better nowadays, but it's still tinkerer-oriented.
SuSE -- Enterprisey enough and user-friendly enough, has a history of shady deals with Novell, uses yet another package manager.
Ubuntu -- User-friendly Debian. No one expected a Debian remix to attract thousands of non-technically oriented users. It served no purpose : before Ubuntu, there was no average Joe Linux user population, they were (almost) all computer enthusiasts ; I'm speaking of desktops in the home here, not enterprise/server use.

See what I'm getting at ? Supporters of each distribution think mostly the same as you : "it would be nice if all those devs and contributors to distribution X went to my distribution of choice, so we could have more manpower to make it even better". How do you choose one ? You can't even create a new distribution to cherry-pick each good thing in each distribution, as they mostly are incompatible with each other.

> **Andy06 said:**
> However, with GTK and QT, they don't make much of a difference to the user experience and both are more of enabling technologies which enable something else to exist rather than existing as an end in themselves.

Choice is good, too much choice is definitely bad. Choice for the sake of choice however is just downright messy :D

Oh, they do make a difference. Let's go into the Gnome vs KDE troll for a moment. Gnome's view on configuration is basically "sane defaults" : if the defaults are good enough, let the beginner user not worry about configuration. KDE's is "configure everything". If you've tried it, you may have noticed how everything can be configured. It's overwhelming at first.

Gnome's view on applications sticks to the Unix way of life : each application does only one thing but it must do it as well as possible. (This appears to be changing in recent Gnome releases, with more things integrated to each other, but still separate entities.) KDE's is diametrically opposed : each application does everything, including coffee.

As you can see, they're not really compatible. Their design guidelines reflect this. Their toolkits do exactly what they need to do, and they don't need to use the other (as a matter of fact, it would probably hamper them). Factor in XFCE, which uses GTK+ but not Gnome libraries. In KDE, a lot of things are handled by Qt only (it includes I/O, networking, even databases...). XFCE, which aims for weightlessness, has no interest in using the heavier Qt stack instead of GTK+, and is in fact complaining about the inclusion of printing support, among others, in GTK+.

> **Andy06 said:**
> the other is almost a perfect substitute or can be with some minor work.

Whoa, that's some assumption you're making. As stated before, Qt isn't just a GUI toolkit, and GTK+ does things quite differently. Also, GTK+ is meant to be used, through the GObject system, with C, while Qt is used with C++. Porting an application from one to another can be quite a bit of work, or so I'm told.

> **Andy06 said:**
> However, the existence of both stands in the way of users almost every day when they decide they won't install apps built on the other one because they don't want all the extra libraries, dependencies and cruft. Sure it's a end user decision but I'm sure every user on this forum has at one time or another, used at least one less than ideal app because their absolute favorite was built with the other toolkit. I know I have.

You have a point here. I used to run Amarok in a Gnome environment when I was younger (I don't any more, as I have found several applications that advantageously replace it for me). I often envied the KOffice suite (until I installed it and it was meh, didn't try KOffice 2, probably won't). Look at it this way : in Windows, when you install an application that uses another toolkit (pretty much all the time, in fact), you're installing a lot of libs underneath. The situation in Linux, although it's not perfect, is noticeably better. (Windows users : Put Office 2007, Live Messenger, Yahoo Messenger, Windows Explorer, etc. side to side, and tell me the Windows GUI is consistent with a straight face.)

> **Andy06 said:**
> But then when you have to make a choice between usplash and splashy, it's like.......who cares. Only interested in the end product and both are capable of ultimately the same sort of results with similar efforts.

I had never even heard of splashy before, but I get what you're saying. I think it pretty much all boils down to personal preferences. I know I won't give up on-the-fly-editable shortcuts and emacs-style keybindings, and my neighbor doesn't want anything to do with the GTK+ file chooser dialog.

Edit: Whuohkay, that was a long post. Now to sleep.

---

### Post by Andy06 on 2009-07-07
Thanks a lot for the detailed explanation. Helped immensely.
I am with your neighbour on the GTK file chooser :D 
I absolutely hate that thing, tried my best to get it included as a papercut @ launchpad for 9.10 but no luck.

I only started using linux since middle of last year but have made over 100 installation for dozens of people since. My first introduction with KDE was KDE4.1 and so I find KDE to be a whole lot of nothing :)

The mess of settings and sheer variety of things you can tinker in Compiz-settings-manager, cairo dock, emerald etc. I did not find in KDE at all. I know I should probably wait till at least KDE4.3 and will definitely try it again then. But for now, KDE just seems less configurable, less usable and less simple than GNOME. I just find that GNOME has outgrown its simplicity reputation and its apps pretty much do everything you expect them to, you cannot find it wanting anymore. Anyway Mint 7 KDE CE is imminent in the coming weeks, that should be one of the best KDE releases :)

---

### Post by shae on 2009-07-07
I think your number of useless distributions is grossly overestimated.  I would say just the distro's without active releases are not really useful.  Having 1000s of distributions does not hurt anyone.  If anything is hurting anyone, it is the one-size-fits-all attitudes with Windows and Mac OS.

Secondly, they may provide the same functions, but as mentioned GTK uses C and QT uses C++.  This might not seem important to you, but some programmers like one over the other.  Some people like GTK over QT just because the way one may feel compared to the other.  What is important is that Linux gives the user the choice to use one, the other, or both.

I have done some coding with GTK and think it is alright.  I am not sure if I really want to touch QT.  I also choose applications to not use QT, not because I dislike those applications, but because I dislike QT.  I would certainly notice if GTK disapeared and I would especially love if QT disappeared :D.

Remember, there are things that Ubuntu is not good at.  Most notably, building debians from source is much harder than rpm or my favorite package management system, pacman.  You might not find that interesting, but lots of people do.

In fact, recently there are several things that Ubuntu has done that I do not like.  A great example is removing the exit from the menu by default because it was "duplicate functionality."  If anything, they should remove the stupid exit thing in the panel.

Remember, applications even at the splashy vs usplash level has importance.  One might be faster while the other might be less rough.

---


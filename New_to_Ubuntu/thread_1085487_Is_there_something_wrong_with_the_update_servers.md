---
title: "Is there something wrong with the update servers?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by dandis on 2009-03-03
Hello everyone!

Long story short: I have Ubuntu version 6.06 installed on an old PC that has not been booted in years. This morning I booted the machine, connected it to the internet and downloaded all the updates it could find.

However, I seem to be stuck with old versions of Firefox, OpenOffice.org and VLC media player. I restarted the PC, unfortunately the problem persists. Now the updater says the system is up to date, but it's obviously not. Is there something wrong with the update servers or the operating system? Should I reinstall?

It's my second time using Linux, first being when I installed Ubuntu on that PC, so please excuse my noobness. Any help is appreciated.

---

### Post by skymera on 2009-03-03
6.06 is fully supported till June this year.

Maybe 6.06 only has those versions as thr latest?
Perhaps some compatibility issues with new packages.

---

### Post by techstop on 2009-03-03
> **skymera said:**
> Maybe 6.06 only has those versions as thr latest?


Indeed. Just because a distro is supported doesn't mean it will have the latest packages. For instance, Firefox is only up to 1.5 on dapper;

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=firefox](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=firefox)

Because of pending EOL, why not upgrade to 8.06LTS ?

EDIT: Nothing wrong with the update servers, it's just that you are running an old distro.

---

### Post by geirha on 2009-03-03
When an ubuntu release is in development, packages keep getting updated to the newest version all the time, until the package freeze date. After that, no newer versions of the packages will be installed, only bug fixes, so you won't find firefox 3 in 6.06's main repositories. You should consider upgrading to the newest LTS release though, since as skymera mentions, Dapper's three year support is nearing the end. [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by dandis on 2009-03-03
I understand, but then installing the latest version would only be a temporary fix, because in 6 months I would have to upgrade again in order to get newer software. It's just not a viable option.

How about an Ubuntu version useable for at least two years AND with up-to-date software? You know, like having Firefox 1.5, visiting getfirefox.com, downloading the latest version and replacing v1.5 with it. I can do that on Windows XP, and not only with Firefox, but with OpenOffice.org and VLC media player also.

So what are the reasons for the feature freeze? How come other operating systems do not have this problem?

---

### Post by redseventyseven on 2009-03-03
> I understand, but then installing the latest version would only be a temporary fix, because in 6 months I would have to upgrade again in order to get newer software. It's just not a viable option.

What are you basing "not a viable option" on? I can understand coming to that conclusion for Windows, as with each upgrade you'd have to fork out a hefty sum of cash. Also, Linux distribution upgrades take much less time than full Windows re-installs. If you've got your home folder separated out onto its own partition (something you'll only ever have to do once regardless of how many times you end up upgrading), you can keep all your configurations and personal documents for after the upgrade.

> 
How about an Ubuntu version useable for at least two years AND with up-to-date software? You know, like having Firefox 1.5, visiting getfirefox.com, downloading the latest version and replacing v1.5 with it. I can do that on Windows XP, and not only with Firefox, but with OpenOffice.org and VLC media player also.

So what are the reasons for the feature freeze? How come other operating systems do not have this problem? 

That's all fine and good, but that's essentially what an upgrade does, just all in one go. Also, as a rule of thumb, upgrades of Linux software are far less essential than for Windows, which usually contain a lot of security patches rather than innovative experimental ideas, some of which might not be that mature. Take the recent developments of KDE4 versus the older, more stable KDE3.5, for example.

Anyway, what I'm trying to explain is that upgrading your Ubuntu from 8.04 to 8.10 is much less of an overhaul than, say, upgrading from Windows XP to Windows Vista. Features are frozen to ensure compatibility and security, and ensure that upgrading one package doesn't break several others. And you're still free to find and download the latest versions of software direct from the developers - either by downloading a .deb file (this is the type of file that is roughly equivalent to the Windows setup.exe) or by adding the repository for that program (if they have one) to your system - if the project has a repository, it usually comes with instructions for how to access it using Ubuntu.

---

### Post by egalvan on 2009-03-03
> **dandis said:**
> How about an Ubuntu version **useable for at least two years AND with up-to-date software**?

There are HUGE differences between 6.06 and 8.10.
Probably greater that XP and ME.
Yet you were able to up-date that older version.
It still runs well on that "hadn't booted in years".
Many folks would call that "usable".
Would I use 6.06? Security issues would be a show-stopper for me,
unless it would not be connected to the Internet.
I use 8.04.2 because I prefer stability. 8.04 is LTS.

And "up-to-date' software means different things to different folks.
Some refer to "stability" and "security"... others to "features"..
Which is more important to you?

> 
So what are the reasons for the feature freeze?
 How come other operating systems do not have this problem?

Feature Freeze means that no more features are allowed in, or to be changed.
Security patches are allowed.
Stability patches are almost always allowed.
This is almost always stability/security oriented.
Software is tested, and once a certain point is reached, no more changes are allowed.
Every time a feature is added or changed, stability or security can be compromised.

Software does not run alone... it interacts with many other parts of the operating system.
These interactions can be very time-consuming to check.

Firefox 3. is VASTLY different from 1.x. 
All those changes can (and probably did) introduce stability issues, not to mention security issues,
 all of which must be tested if problems are to be kept to a minimum.

There ARE Linux distros which are freer along these lines.
It is all a matter of what is more important...
features/newness or stability.

I believe those other types are called "rolling releases".
Correct me if wrong.

Ubuntu, like its parent Debian, is a "point release".

Pick your Poison.

---

### Post by philinux on 2009-03-03
> **dandis said:**
> I understand, but then installing the latest version would only be a temporary fix, because in 6 months I would have to upgrade again in order to get newer software. It's just not a viable option.

How about an Ubuntu version useable for at least two years AND with up-to-date software? You know, like having Firefox 1.5, visiting getfirefox.com, downloading the latest version and replacing v1.5 with it. I can do that on Windows XP, and not only with Firefox, but with OpenOffice.org and VLC media player also.

So what are the reasons for the feature freeze? How come other operating systems do not have this problem?

If you always want the latest firefox then use ubuntuzilla.
[http://ubuntuzilla.wiki.sourceforge.net/?token=64344bbb0f81d1d060acc67ac3c21dfe](http://ubuntuzilla.wiki.sourceforge.net/?token=64344bbb0f81d1d060acc67ac3c21dfe)

---

### Post by dandis on 2009-03-03
I think I understood _what_ is happening, but I still don't understand _why_.

When I said that "other operating systems don't have this problem" I was referring to Apple OS X and Mircosoft Windows.

Windows XP is an operating system released in 2001, but it can flawlessly run any Firefox version ever released on the Windows platform. And it's not like Windows in 2001 is the same as Windows in 2009. There have been countless patches and 3 service packs since release day, yet I can install and run Firefox 0.25 and Firefox 3.1 side by side.

Don't you find it annoying that you have to upgrade the whole OS every 6 months just to run newer versions of commonly used software?

If Firefox is that tied into Ubuntu's internals that replacing it would cause a mess, then something went wrong somewhere. You can't design a long term OS with that much integration going on.

Being stuck in a closed repository is not what I imagined when I first heard about the free software movement and Ubuntu. I mean, where's the freedom in this? Freedom to install whatever I want... just as long as I don't leave a specific repository? Yes, yes, I know I can get the source and maybe compile it, but that's a try and pray kind of a thing. And compiled stuff is invisible to the package manager!

If Firefox 3 would compile on Dapper it would have already been in the repositories, but it's not, that means it cannot be compiled without recompiling more than half the other stuff in there and that actually means creating the next version of the Ubuntu OS by yourself and that is what the developers are doing so doing it would be pointless redundant and... GAAAAAAAH!

It's obvious I can't have my cake and eat it too, and that would be fine, but look, ma! The other kids CAN do it. They CAN provide me with newer versions of software WITHOUT borking the whole software ecosystem. Why, just why can't Ubuntu focus on the operating system and place the burden of providing packages on upstream's shoulders? Where's the fine line between the OS and the applications? Where's the platform? Why are we stuck with a moving target that continues to change every 6 months?

I don't want to upgrade my OS every 6 months. I want to be able to keep it at least two years **AND** to be able to run newer software during this time. Microsoft and Apple can do it, Ubuntu has no excuse.

In my view, the current state of things seems to be just an excuse for preserving this fallacious centralised repository system. It's just not right!

---

### Post by Roanoke on 2009-03-03
> **dandis said:**
> 
Windows XP is an operating system released in 2001, but it can flawlessly run any Firefox version ever released on the Windows platform. And it's not like Windows in 2001 is the same as Windows in 2009. There have been countless patches and 3 service packs since release day, yet I can install and run Firefox 0.25 and Firefox 3.1 side by side.
[/code]
But you wouldn't be able to run firefox 3 on windows NT.
[QUOTE=dandis;6830292]
Don't you find it annoying that you have to upgrade the whole OS every 6 months just to run newer versions of commonly used software?[/code]
Erm, we don't have to. It's just no one is running dapper anymore, or at least a very small minority.

[QUOTE=dandis;6830292]
In my view, the current state of things seems to be just an excuse for preserving this fallacious centralised repository system. It's just not right!
You can add and remove repos as you wish, it's hardly centralized.

---

### Post by sydbat on 2009-03-03
Repositories maintained by Canonical ensure malware-free software available to your computer, and version specific applications that WILL run on your system.

However, as stated by Roanoke, you can add whatever repository you want, from virtually anywhere (although I think it has to be for Debian distributions), and update/upgrade whatever application you want...but if something happens to your system because of malware from a dodgy repo/website download, please do not blame Canonical/Ubuntu for that.

---

### Post by redseventyseven on 2009-03-03
> When I said that "other operating systems don't have this problem" I was referring to Apple OS X and Mircosoft Windows.

Windows XP is an operating system released in 2001, but it can flawlessly run any Firefox version ever released on the Windows platform. And it's not like Windows in 2001 is the same as Windows in 2009. There have been countless patches and 3 service packs since release day, yet I can install and run Firefox 0.25 and Firefox 3.1 side by side.

Don't you find it annoying that you have to upgrade the whole OS every 6 months just to run newer versions of commonly used software?

Not really. As I said before, it's much easier to upgrade a Ubuntu installation than it is to re-install or upgrade a version of Windows. It's also much cheaper, both in terms of time and money. Ubuntu 8.10 costs £0, takes half an hour to install (with practice), all your settings are kept, and you don't need to buy any new versions of programs to retain compatibility with the operating system (though you may need to download some). A Windows Vista upgrade currently [costs about £65]("http://www.amazon.co.uk/Windows-Premium-Service-Upgrade-Version/dp/B0013O54P8/ref=sr_1_1?ie=UTF8&s=software&qid=1236101007&sr=8-1"), and takes much longer to install. I don't know for certain whether or not you can keep your settings and programs from one version of Windows to another but I'm sure someone with more knowledge about this will be able to provide the relevant information.

Besides, as has already been mentioned, you can still expand your list of available repositories beyond those that Canonical/Ubuntu provide. But these come at a price - the potential compromise of security. With Windows, you never had that security in the first place.

Also, in Open Source software, there's far less need to run the absolute latest version of any program. "New version" doesn't always mean "better". Often, updates are experimental and users prefer to remain with a previous stable version than remain on the bleeding edge and risk losing their work.

Incidentally, I dispute your statement that Windows XP "can *flawlessly* run any Firefox version ever released on the Windows platform".

---

### Post by cwsnyder on 2009-03-03
You obviously have forgotten everything you ever learned about Windows 98.  Can Windows 98 run all of the software for Windows XP?  They are only 3 years different!  Don't think that the Windows world has stood still.  There is a TON of software which will only run on Windows 2000, XP, or Vista.  Granted Windows 2000 is about 10 years old now, but many games will not run on Windows 2000.  The ONLY reason Windows XP is still receiving notice, as decrepit as it is from 2002, is because many people refused to give it up.  And there is a lot of software which will not run on XP prior to SP2, also.

---

### Post by achase79 on 2009-03-03
You said you would like it to last at least 2 years?  6.06 to 8.04 which are both the LTS versions were essentially 2 years apart.  6.06 is being phased out because 8.04LTS is available and has been tested rigorously.  This is the development cycle.  Just as Microslop is going to be dropping support for WinXP soon after Windows 7 comes out.

---

### Post by Roanoke on 2009-03-03
In essence, I fail to see why you can't just upgrade to Hardy LTS.

---

### Post by e_james on 2009-03-03
Perhaps the key distinction is that Ubuntu is not an operating system, it's a distribution - an operating system (Linux) plus a large selection of applications tested to work well with each other. Microsoft doesn't bundle Microsoft Office with Windows XP or Vista. You get Internet Explorer, Wordpad, Media Player, Movie Maker and that's about it.

I have never done an upgrade as such but I have installed newer versions of Ubuntu to replace older versions. The /home partition retains all the documents and settings. The procedure is mostly painless except for networking which keeps getting improved with new tools. As I understand it 8.04 comes with read / write NTFS support as standard. Installing a new version takes more than half an hour if you count about 250MB of downloaded updates, but then that applies to Windows too.

I believe there is a procedure whereby you can record all your current Ubuntu applications and have them all installed automatically with the next version. I suppose that's what the upgrade tries to do.

---

### Post by pparks1 on 2009-03-03
> **dandis said:**
> 
Windows XP is an operating system released in 2001, but it can flawlessly run any Firefox version ever released on the Windows platform. And it's not like Windows in 2001 is the same as Windows in 2009. There have been countless patches and 3 service packs since release day, yet I can install and run Firefox 0.25 and Firefox 3.1 side by side.
You can also run any version of firefox that you want on an older version of Ubuntu too...just like Windows...you go download it from Mozilla and then install it.    It's just that Ubuntu only maintains and supports certain versions in their repositories....but you certainly don't have to use those repositories.

> **dandis said:**
> Don't you find it annoying that you have to upgrade the whole OS every 6 months just to run newer versions of commonly used software? You don't have to update every 6 months.  You can run the Long Term Release versions and stay pretty darn current and maintained for 3 years.   And like I said above, you can go download and install whatever you want...so in those specialty circumstances you still have an option.  Not too shabby for a completely free operating system.

> **dandis said:**
> I don't want to upgrade my OS every 6 months. I want to be able to keep it at least two years **AND** to be able to run newer software during this time. Microsoft and Apple can do it, Ubuntu has no excuse.

In my view, the current state of things seems to be just an excuse for preserving this fallacious centralised repository system. It's just not right!

You are likely going to find this same problem with any distribution that has a package manager.  This is not just specific to Ubuntu, I've certainly experienced this same problem with SuSE, Red Hat Enterprise Linux, CentOS, and Fedora.

---

### Post by yther on 2009-03-03
To OP:  It's just the way Ubuntu works.  There are distributions like Arch that are always based on the latest versions of everything, or at least have it all available.  There are distros like Mint that have a release every 2-3 months, and there are distros like Ubuntu that only release twice a year.

Some people run Ubuntu but add extra repositories for certain software they want to keep up-to-date (such as the bleeding-edge **mplayer**).  There are also "backports" repositories and such.  This is what I've done, so I have Intrepid as the base but some more current stuff like KDE 4.2, mplayer from svn, etc.

If you want to stay current with everything, may I suggest you take a look at a rolling-release model of distribution?  [Gentoo]("http://gentoo.org") is excellent if you want to learn about how a Linux system really works, by building yours from the ground up; it's compile-as-you-go but with a dependency system in place so you don't (usually) have to figure out for yourself what's required to build something.  It's almost the polar opposite of a Debian-based distribution that values stability over all.  ;)

---

### Post by dandis on 2009-03-04
OK, then Ubuntu is obviously not for me. And neither is Fedora, Debian, OpenSUSE etc., as long as they use what in my opinion is a fundamentally flawed concept.

I found out about PC-BSD and their PBI packaging format, it's much closer to what I want in an OS. I also did a little research, and it's obvious distributions exist because developers can't be bothered to package their stuff, so another species had to emerge: the packager. And of course, the devs won't package because there are too many moving targets out there so it's a "chicken and egg" problem. It's a mess.

So yeah, the repository concept is actually a poor solution to the packaging problem. No base OS, no common Linux base among the distributions, no common packaging format and manager, no common kernel, compiler, file system hierarchy etc. = anarchy.

Think about it, if something like this existed, nobody would need repositories anymore. Or there would be a single, distribution agnostic repository that everyone trusts. But that's impossible from a logistic point of view, at least.

So yes, I think I have isolated the single, most important problem with the GNU/Linux operating systems: no authority, no clear, focused push toward common standards. And the repository mess is just one symptom.

Thank you for playing. I'm going to donate some money to the GoboLinux project, they're trying to fix at least some of my concerns.

---

### Post by lakersforce on 2009-03-04
*cough*troll*cough*

No one forces you to use Ubuntu 6.06 or any other release for that matter. Use the OS that suites you best!

---

### Post by skymera on 2009-03-04
> **dandis said:**
> OK, then Ubuntu is obviously not for me. And neither is Fedora, Debian, OpenSUSE etc., as long as they use what in my opinion is a fundamentally flawed concept.

I found out about PC-BSD and their PBI packaging format, it's much closer to what I want in an OS. I also did a little research, and it's obvious distributions exist because developers can't be bothered to package their stuff, so another species had to emerge: the packager. And of course, the devs won't package because there are too many moving targets out there so it's a "chicken and egg" problem. It's a mess.

So yeah, the repository concept is actually a poor solution to the packaging problem. No base OS, no common Linux base among the distributions, no common packaging format and manager, no common kernel, compiler, file system hierarchy etc. = anarchy.

Think about it, if something like this existed, nobody would need repositories anymore. Or there would be a single, distribution agnostic repository that everyone trusts. But that's impossible from a logistic point of view, at least.

So yes, I think I have isolated the single, most important problem with the GNU/Linux operating systems: no authority, no clear, focused push toward common standards. And the repository mess is just one symptom.

Thank you for playing. I'm going to donate some money to the GoboLinux project, they're trying to fix at least some of my concerns.

If you're moaning about GNU/Linux, then go out and BUY Windows Server 2008.
I'm sure THAT'S supported for years to come.

---

### Post by Roanoke on 2009-03-04
Wow, I never knew that not all linux systems have the same file tree *cough*they do*cough*. If you want bsd, then leave.

---

### Post by e_james on 2009-03-04
I believe Winston Churchill said 'Democracy is the worst form of government, apart from all the others'. I would put it another way, democracy is a deliberately inefficient form of government: it slows down the good guys, but it also slows down the bad guys and gives the voter time to think. 

I believe a similar philosphy applies to PCs and the internet. I am comfortable with a certain amount of anarchy. I think the proliferation of PCs and the spread of the internet is perhaps the main reason why George Orwell was wrong about 1984. If one person or a small group had control of the internet, the whole world could be in big trouble. This is why TPM / Trustworthy computing makes me very uncomfortable.

Agreed standards are extremely useful or we could not even communicate with each other, but so are the forks. There's usually an optimum fit but there's no such thing as perfection in this world.

Having said all that and going back to the original post, feisty recently stopped updating for me and it took me some time to realise that the feisty main repository had disappeared. Then I had to edit the resources list to stop the error messages. Perhaps it would be a good idea if the last update before a distribution goes 'unsupported' included a fix for resources and a message to the user.

---


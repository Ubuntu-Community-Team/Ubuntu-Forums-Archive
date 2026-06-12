---
title: "How do I install kde-minimal, I mean really minimal ?"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by uflieven on 2009-10-02
I'm using Ubuntu for about three years now (since just before 6.10), but I still can't figure out why some packages are dependencies of others. For example, when installing konqueror, dolphin is installed along. 

Apparently, konqueror needs dolphin to function. But my point is: konqueror is a file manager, why is dolphin, which is another file manager, considered a dependency and installed along?

Same case when installing Firefox. Why the heck is synaptic installed along? Just suppose I want to use kpackagekit, then I don't need synaptic (which is just another package management app), but again, it seems synaptic is considered a dependency (or a recommended package, that could also be the case) of firefox.

Can someone (at Ubuntu or another user) come up with a good solution, so I don't have to install packages along that I won't use (and that are just filling up space)?

Thats my first question, my second one is actually more related to the topic title. I noticed the kde-core package has been replaced by kde-minimal in karmic. My problem is, it doesn't seem minimal at first sight (need to download 131 MB).

Secondly, when I choose to download kde-standard, it contains exactly the same packages. So, is this intentionally, to make 2 meta-packages with the same contents? And, regardless whether it is or not, I would like to see a meta-package added to karmic that installs just the kde-window-manager (if kdm is included I will accept that, guess this was the case in Ubuntu 9.04 with kde-core).

But all the other stuff, like file-managers, text-editors, package-managers and so on should not be installed along. I'm asking this because Ubuntu is free, so I want the freedom to install the applications I want to use.

But I don't like the fact that many (meta)packages consist of too many packages, that are all installed along, which is not what I want. I guess there are other users who feel the same way.

So my ultimate question is: Can you make sure dependencies are real dependencies, I mean, to me it seems logical synaptic is NOT a dependency of firefox.

Or with other words, if i was using Windows right now, and I would choose to download firefox, I would not be happy if synaptic was installed along.

Same when installing a desktop environment. If a want to install kde and konqueror, it seems logical I have to type: **sudo apt-get install kde-minimal konqueror**. (or kde-core and konqueror if I was using 9.04) But right now, if I type: **sudo apt-get install kde-core**, then dolphin, konqueror, konsole, etc. are all installed along, which, for me, isn't a desired effect.

So please minimize dependencies, whenever possible.

Thanks for taking the time to read this, and if you have anything that could help, please let me know.

---

### Post by Mighty_Joe on 2009-10-02
If you want the attention of the Ubuntu developers, you should probably post a bug to [Launchpad]("https://launchpad.net/") or submit an entry to [Brainstorm]("http://brainstorm.ubuntu.com/").  These forums are more for the community to help each other rather than to submit feedback to the developers.

---

### Post by pythonscript on 2009-10-02
```
sudo apt-get install *package-name* --no-install-recommends
```

will only install the required packages, and if you add

```
APT::Install-Recommends "0";
APT::Install-Suggests "0";
```

to your /etc/apt/apt.conf file (create it if it doesn't exist). That should cut down on *some* of the installed apps that aren't actually dependencies. As for actually changing the apps to not include so many dependencies, that's something to post in launchpad.

---

### Post by LowSky on 2009-10-02
Part of the problem these days is that developers think that because hard drives and flash drives sizes are so big that they dont expect people to care how big an install is, and rather create a system people all around would like rather than a minimal working system that is too specialized.

That is Ubuntu, and it been brought up a bunch of times, especailly with openoffice being installed by default. that alone takes up a bunch of space. The argument for more user choice in applications is growing, as the deveolopers start to replace some programs for others, like Empathy for Pdgin, which caused a huge uproar.

If you want a more minimal install look at maybe switching distros, like Gentoo or Arch or even Debian, as they can be a light or heavy with little compromise from the user. Remember Ubuntu and its other flavors all try to be complete working systems built on applications most users will want or need.

---

### Post by pythonscript on 2009-10-02
Unless you *absolutely must* stick with KDE, for whatever reason, but still want to use Ubuntu for a variety of reasons (of which there are many positive ones, to be sure) you could start by installing a command line only version with the alternate CD and building your system from there. That's what I originally did with ubuntu and lxde, and I found a measurable performance and installation size difference (I turned off the installation of recommended packages, as shown in my previous post, too).

---

### Post by uflieven on 2009-10-02
Thanks for the replies, everyone.

I considered posting a bug in launchpad, but since the developers have already enough work with other bugs, I decided to give this forum a try, and so far I'm quite happy with the response I have in about an hour.

@pythonscript: I knew of the --no-install-recommends option, it seems to work better in some cases than in other. However, your second option using apt.conf, I haven't tried yet, so thanks for that one. I'll try it soon and see if it has the desired effect.

About starting from the command line install, that's what I'm actually doing. I've also tried lxde in the past, and I liked it, but I think it's actually a little less complete than kde. I hope you understand what I mean, but my purpose is to create a linux distro that Windows-users actually want to use, and I think for that purpose kde is well-suited.

Nonetheless, lxde is indeed fast and light, and that's also the reason I liked it. So although I think it's very good, it misses something to be a Windows-replacement. Originally we (I say we because I have some friends who also want to create a Linux-distro that could replace Windows) also wanted to fit it on a single cd, but right now, that seems close to impossible, so we will put it on a dvd.
We have yet to decide what packages we will put on the dvd, but will decide that in the next weeks. While we will indeed use a dvd, I still want the resulting iso-image to be as small as possible, so it's still downloadable without having to wait for hours until download is complete. I guess we will make the image available for download too, I'm not sure about that yet, but it surely would help getting the dvd distributed. We will probably use kde and ubuntu 9.04, not 9.10, because we need to be ready in early november, so we will have to work on it this month, which isn't possible with 9.10, because it won't be available until the end of this month. 

@lowsky: thanks for your input, but I guess I'll stick to ubuntu for now. However, I don't exclude a switch to another distro in the future.

---

### Post by SuperSonic4 on 2009-10-02
does the kde-core package still exist? 

```
sudo apt-get install kde-core
```

If I remember rightly it doesn't even install Konsole or Dolphin

---

### Post by uflieven on 2009-10-02
@supersonic4: Well, since we are using 9.04, that's a good option indeed, it indeed installs very little. In Karmic 9.10, however, kde-core doesn't exist anymore. I don't know why, have filed a bug-report about that about a week ago or something. The answer was they wouldn't fix it, it was a debian change, if i remember well, so the only option they gave me was to file a bug report at debian. Haven't done that yet. I doubt if i will do it, maybe I should, but I also don't want to submit bug reports no matter what.

---

### Post by SuperSonic4 on 2009-10-02
What if you do a search for KDE? ```
sudo apt-cache search kde
```

And look for minimal/core etc...

---

### Post by uflieven on 2009-10-02
thanks, supersonic4, but I will have to use apt-cache search kde | more, because the output is much too long, and scrolls all over the screen.

---

### Post by wojox on 2009-10-02
Isn't it kde4-core ?

---

### Post by uflieven on 2009-10-02
@supersonic4: got kde-full, kde-minimal, kde-standard, but no kde-core on ubuntu 9.10.

@wojox: thanks for trying, but no, I've tried and the reponse is: Couldn't find package kde4-core.
So the same as I get when trying kde-core, then it says: Couldn't find package kde-core.

@all: I'm sure kde-core (from 9.04) has switched to kde-minimal (in 9.10) The only thing that seems strange to me, is, as supersonic4 mentions, that kde-core installs very little, while kde-minimal seems to install the same packages as kde-standard, and that cannot be considered very little. So I will have a talk with my friends tomorrow, and ask if they consider it appropriate to file a bug report about this at ubuntu/debian. As lowsky mentions, this seems to be an increasing problem now that storage capacities are increasing. But even with that in mind, I find it useless to install packages I'm not gonna use. Thanks for your input so far.

---

### Post by vikjon0 on 2010-03-20
Edit: My misstake this worksfine 

I think kdebase-workspace-bin is to most minimal you will come. The difference between that and --no-install-recommends kde-minimal seem to be konqueror and some other stuff

---

### Post by mkvnmtr on 2010-03-20
I get a good minimal install using XFCE4. It seems to work with very few packages dragged in. I have tried LDXE but it does not seem as complete to me. Off of the minimal install I install xorg, xfce4 and synaptic. Then I have a working system.

---


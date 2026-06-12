---
title: "need help installing bittorrent, and installation in general."
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Jfuse on 2010-02-14
PLEASE someone help me before i go insane. just recently my system crashed, motherboard fried, and voila, got a donor computer from a pal and i'm using ubuntu. can't afford a new op system, so i got linux, but i didn't know it'd be at the cost of my sanity. i've been working for 2 days and getting nowhere, and these are the issues.

how on earth do in install bittorrent? there appear to be 2 different files in the download folder, and i can't figure out which to use, and for what reason. one says BitTorrent_mainline_library_python.tar 5.2MB, and the other says BitTorrent_mainline_python.tar 16.5MB. what on earth is this, and which one do i use? how do i install it?

and for that matter, how do i go about installing things like, for instance, wine or other things.

I'm using ubuntu 9.04, for whatever that's worth.

please help.

---

### Post by darkerlink on 2010-02-14
You already have a bit torrent client installed. It's called "transmission". Go to applications>internet>transmission. It should be there. As a beginner, stick with programs that are native to linux. Use the software center. I think in 9.04, you have to go to applications> add/remove programs.

---

### Post by lovinglinux on 2010-02-14
> **darkerlink said:**
> You already have a bit torrent client installed. It's called "transmission". Go to applications>internet>transmission. It should be there. As a beginner, stick with programs that are native to linux. Use the software center. I think in 9.04, you have to go to applications> add/remove programs.

You should avoid installing stuff downloaded from the web. As suggested above, the Software Center will get most softwares you need from Ubuntu repositories, which are tested and verified.

See [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

I would recommend installing Deluge. It's the best BitTorrent client for Gnome IMO. You might want to read the tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by LOLbuntu on 2010-02-14
Use Rtorrent, its a very lightweight bittorrent client.

---

### Post by mwcrowley on 2010-02-14
Don't download stuff from the web until you understand why it should be your third choice.  Two things that are going to make you love Ubuntu, the add/remove programs application and a program called synaptic.  They both do the same thing, but synaptic gives you more information about what it's doing.  Post back or pm me if you have more issues.  

My advice is to stay away from wine if you can. 95% of the time there is a linux app that does what you need to do.  

deluge is popular, ktorrent isn't bad, there is an azureus/vuze client that is good, but can be resource intensive because it runs on java.

---

### Post by The Real Dave on 2010-02-14
> **LOLbuntu said:**
> Use Rtorrent, its a very lightweight bittorrent client.

rTorrent, though brilliant, is a command line program, and not exactly the best for a beginner. Back when I used a GUI torrent program, I used transmission, and liked its clean interface. I've heard good things about Deluge though. Both are available through Add/Remove Programs

---

### Post by Jfuse on 2010-02-14
what are you guys even saying to me? Lol. i'm an experienced computer user and i know all about downloading things from the web. I prefer bittorrent because it's what i'm used to and it works great. I want to stuff like wine because i miss things like MSN and yahoo IM's. i know about about pidgin, but you have no access to features.

and i still have no idea how to install anything, but i will check that link out, so thanks lol. i just want help, not a lecture on the greatness of linux and it's native programs, i know it's decent enough. it's just, right now i feel powerless with this thing, so any help is appreciated.

---

### Post by lovinglinux on 2010-02-14
> **Jfuse said:**
> what are you guys even saying to me? Lol. i'm an experienced computer user and i know all about downloading things from the web. I prefer bittorrent because it's what i'm used to and it works great.

We are not saying you shouldn't use BitTorrent (I use all the time btw), we are saying you should avoid installing the BitTorrent client (or any software) from a file downloaded from an untrusted source. We are saying that the official repositories for Ubuntu has several BitTorrent clients that are safe to install and can be installed from the Software Center, with a single command or apturl. For instance, you can install Deluge and Ktorrent (the best clients in my opinion) with the commands below:

```
sudo apt-get install deluge
```

```
sudo apt-get install ktorrent
```

You can also isntall from the repositories, by clicking on apturl links. For example click to install [deluge](apt:deluge) or [ktorrent](apt:ktorrent).

In both methods you are downloading and installing the clients from the official Ubuntu repositories, so they have been approved by the Ubuntu developers. What you are trying to do is install the BitTorrent client from a downloaded file that we don't know where did you get it. That's not recommended.

> **Jfuse said:**
> I want to stuff like wine because i miss things like MSN and yahoo IM's. i know about about pidgin, but you have no access to features.

I agree that you should avoid using wine, unless you can't find an alternative application that is native to the Linux environment. In most cases, you will be able to find one. For example, lots of new Linux users want to use uTorrent with wine. This is unnecessary, because Linux has excellent BitTorrent clients, better than uTorrent imo.

What we are saying is not that you shouldn't use wine, but that you should first look for an native application. Not all applications will work on wine, some will work but not as expected, some will work just fine.


> **Jfuse said:**
> i just want help, not a lecture on the greatness of linux and it's native programs, i know it's decent enough. it's just, right now i feel powerless with this thing, so any help is appreciated.

No one is lecturing you. Everyone is giving you good information. Linux is not Windows and we are just pointing some things to let you start with the right foot. Perhaps you should ask which application would allow you to achieve the same results as those you are used to in Windows.

There are a couple of alternatives to MSN, like emesene and aMSN. See [http://linuxappfinder.com/communications](http://linuxappfinder.com/communications) 

When you find an application on the link above, don't download it from a web site. First, see if you can find it in the repositories. You can install [emesene](apt:emesene) and [amsn](apt:amsn) from the repositories.

---

### Post by Jfuse on 2010-02-14
okok guys lol, i get it.

it just seems like linux PURPOSELY makes eveyrthing so darn complicated. i've been working  on this comp for 2 days and havn't accomplished a single thing with it. it's all so convoluted. in windows you just click a file, it opens and you click next next next lol. in linux i find myself reading stuff like "compiling drivers", "apturl", "install from source", "repositories", "compiling" and various other terms and what not. i mean, i'm trying to figure out how to input driver/installation codes.... what is that? and where do i do it? =/

the whole thing just doesn't seem user friendly at all, and god FORBID that even my creative xmod work right on this thing. but i can't afford anything else, so i'll stick with it lol.

---

### Post by lovinglinux on 2010-02-14
> **Jfuse said:**
> okok guys lol, i get it.

it just seems like linux PURPOSELY makes eveyrthing so darn complicated. i've been working  on this comp for 2 days and havn't accomplished a single thing with it. it's all so convoluted. in windows you just click a file, it opens and you click next next next lol. in linux i find myself reading stuff like "compiling drivers", "apturl", "install from source", "repositories", "compiling" and various other terms and what not. i mean, i'm trying to figure out how to input driver/installation codes.... what is that? and where do i do it? =/

the whole thing just doesn't seem user friendly at all, and god FORBID that even my creative xmod work right on this thing. but i can't afford anything else, so i'll stick with it lol.

Installing applications on Linux is much easier than in Windows. Seriously!!!

[B]1) The most simple method (recommended)
[/B]
Use the Software Center or the Add/Remove manager. I'm not using Gnome, so I don't exactly remember where to locate them, but they should be available in the "System >> Administration" menu. All you you need to do is search for the software you want and click install.

**2) The "Windows" way**

Sometimes you cannot find a software in the repositories, but they are available in the developer web site as a .deb file. The .deb files are just like Windows exe. You just need to double click them to initiate the installation process, then click next next next....the only difference from Windows is that they don't come with viruses :)

**3) The command-line method**

It can be scary at first, but using the terminal to install applications and execute other commands is pretty easy and damn fast. Open "Applications >> Accessories >>> Terminal" and run the installation command:

```
sudo apt-get install deluge
```

[LIST]
[*]sudo = command to do something as administrator
[*]apt-get = command to use the package manager
[*]install = pretty obvious
[*]deluge = name of the application
[/LIST]

After typing or pasting the command, hit enter, type your password, confirm and voilà! 


**4) Web links** (apturl)

Ubuntu offers a method of posting links that launch application installers, directly from web sites and forums like this one. This is very useful to recommend software to other users. You can simply post something like this (between bbcode url tags):

```
apt:deluge
```

Which will be displayed as [deluge](apt:deluge) and will automatically install the application when you click it.

**5)Source code and tar files**

Compiling from source code is definitely not the recommended method, specially for beginners, but sometimes is the only way. You might need to compile when you want beta versions, when you want to enable special features in the software or when you want some obscure software that is not in the repositories and there isn't a deb file available for download. Nevertheless, most of the time you won't need to do it. I never needed, although I have already compiled Firefox to make it run faster on my machine.

Source code is usually distributed as tar compressed files that need to be extracted before compiling. But sometimes software that is ready-to-run can be distributed as tar files too. For example, when you download newest versions of Firefox from Mozilla web site. In these cases, you don't need to compile it, just extract it and run the executable file inside it. There is no installation process, it works out-of-the-box.

More info at [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---


---
title: "Help, flashplugin installer messed up my computer"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Isyaltut on 2010-10-07
Hi, I'm using Ubuntu 10.4 and just updated it with update manager. When it says that it needs 311mb files, I've decided to leave it on while I'm sleeping (I don't have really fast internet connection). After I woke up, I expected all is done with updating, but somehow I find that the update manager hang while downloading flashplugin installer. I've checked my internet connection with firefox and it's working fine. And since I want to going out bringing my laptop I tried to force cancel it with Ctrl+C and press yes to confirm. 

And then when I've tried to boot it, instead of bring me to ubuntu login menu I got this cryptic text message that I don't understand (I've already forgot it, but it then came up with inftrams word, I'm not sure). 

So, now I can't access my Ubuntu box at all, so please anyone can help me to solve this problem, much appreciated.

---

### Post by NightwishFan on 2010-10-07
Boot into recover mode. You can do this by holding in shift while booting until you get a menu. Pick recovery mode. When you boot into it you should see a blue menu. Choose fix packages if that is an option. If not, choose root prompt with networking and run:
```
sudo apt-get -f install
```

When it is done, reboot.

---

### Post by Isyaltut on 2010-10-07
It seems that I can't access recovery mode. When you say hold shift i'm nots ure when. I'm running ubuntu dual boot with windows, so should i press shift before or after grub?

---

### Post by NightwishFan on 2010-10-07
If you can see grub, you are already there, choose recovery mode. (Some computers need to hold shift to see grub menu)

---

### Post by Isyaltut on 2010-10-07
Ok, I've entered recovery mode. But it shows message until it stops at Busybox v1.13.3 (I'm not sure if I remember it right, right now I'm using Windows. Tried sudo apt-get -f install, but it says that /bin/sh sudo not found. And I can only access within initframs. 

Gahhhh, it's really frustating!! Why oh why must flashplugin installer downloaded separately?

---

### Post by NightwishFan on 2010-10-07
I dont think flashplugin did this.

---

### Post by NightwishFan on 2010-10-07
Try without sudo:
```
apt-get -f install
```

---

### Post by Isyaltut on 2010-10-07
Still, no luck. it says that apt-get not found. I typed help and shows some basic command available such as cd chmod test, etc.


> **NightwishFan said:**
> I dont think flashplugin did this.

Yeah, but I think in a way it does. If flashplugin installer can be downloaded from the same server as any other program, I  won't be having hang up problem and not force it to cancel. I run a quick google search, and found bug report in launchpad that have same problem as mine (flashplugin installer hang up). But it doesn's say whether their ubuntu box broken or not like me.

---

### Post by Isyaltut on 2010-10-07
Still, no luck. it says that apt-get not found. I typed help and shows some basic command available such as cd chmod test, etc.


> **NightwishFan said:**
> I dont think flashplugin did this.

Yeah, but I think in a way it does. If flashplugin installer can be downloaded from the same server as any other program, I  won't be having hang up problem and not force it to cancel. I run a quick google search, and found bug report in launchpad that have same problem as mine (flashplugin installer hang up). But it doesn's say whether their ubuntu box broken or not like me. 

Or should I just clean install ubuntu? But then I will be afraid to update it and come up with some problem. I'm half thinking that I will clean ubuntu partition and use Windows solely. I hate to do it, but if process such as updating (not upgrading, I heard that a lot of people having problem with upgrade) can potentially break my system, I rather not use it untul ubuntu can solve it. 

So, any advice?

---

### Post by NightwishFan on 2010-10-07
Use what works, its not like Windows is any more reliable. If it was I wouldn't be here.

However, I seriously think you did something severe. I have force canceled upgrades before and had no issue other than having to reconfigure the package. For now try this command. If you are unable to get into the recovery mode or run any commands, I am unsure how to help.
```
sudo dpkg --configure -a
```
or
```
dpkg --configure -a
```

---

### Post by Isyaltut on 2010-10-07
> **NightwishFan said:**
> Use what works, its not like Windows is any more reliable. If it was I wouldn't be here.


Me too, I'm using Ubuntu for almost a year now, and loving it. I've came across some update problem that leds to broken package and can be solved with dpkg --configure. So, yeah this is the first time updating break my system

Anyway, maybe I'm just clean install ubuntu and not let flash updating itself.

---

### Post by NightwishFan on 2010-10-07
I am sorry I could not be of more help at the moment, (also if I seemed rude above), it is just how I feel about the issue. All updates should be taken seriously though, and any action done as the root user. All could potentially have consequences. In my opinion, the less time spent as root the better. (Even for me).

A reinstall might just be the simplest option at this point. Thankfully it is easy to do so. If you want to retain your kept packages, if you can browse the Ubuntu disk with a live cd, copy the deb files in "/var/cache/apt/archives" to a flash drive. Then copy them back to there in the new install. (You will need to have root access to do this). That way when you upgrade packages will not need to be downloaded again. Naturally you will need to use the same Ubuntu version and arch as the current install for that to work though.

Good luck, and I hope I can be of help, feel free to ask.

---

### Post by Isyaltut on 2010-10-07
> **NightwishFan said:**
> I am sorry I could not be of more help at the moment, (also if I seemed rude above), it is just how I feel about the issue.

No, It's Ok, :)maybe I was a little bit annoying too with me whining about Ubuntu not working perfectly for me when a lot of volunteer's hard work has been put in to this.

And now I've just clean install Ubuntu. Do you have any idea how to get install flash without going to download it from repository

---

### Post by NightwishFan on 2010-10-07
I believe you can simply download a flashplugin.so file, and put in a mozilla folder somewhere. You will have to ask someone who knows their firefox, like lovinglinux, a user on here.

---

### Post by lovinglinux on 2010-10-07
> **Isyaltut said:**
> Yeah, but I think in a way it does. If flashplugin installer can be downloaded from the same server as any other program, I  won't be having hang up problem and not force it to cancel. I run a quick google search, and found bug report in launchpad that have same problem as mine (flashplugin installer hang up). But it doesn's say whether their ubuntu box broken or not like me.

The flashplugin-installer is downloaded from the server of your choice, listed in the Software Sources. Nevertheless, the plugin itself is downloaded from [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/), which means is the partner repository on Canonical servers. 

Anyway, I don't think flash download has anything to do with your problem. I'm not sure if it is possible, but I suspect that while the flash download stalled, other updates continued to be downloaded and started to install/configure. When you cancelled the update, you probably interrupted the installation or configuration of an important package. I did that other day, after totally forgetting I was updating the system on a minimized terminal. It broke my system completely and I also had to do a fresh install.

> **NightwishFan said:**
> I believe you can simply download a flashplugin.so file, and put in a mozilla folder somewhere. You will have to ask someone who knows their firefox, like lovinglinux, a user on here.

If you are using a 32bit system, then you can grab the deb package from the Adobe site:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

If you are using a 64bit system, then you need to get a preview version from Adobe Labs:

 [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by Isyaltut on 2010-10-07
> Anyway, I don't think flash download has anything to do with your  problem. I'm not sure if it is possible, but I suspect that while the  flash download stalled, other updates continued to be downloaded and  started to install/configure. When you cancelled the update, you  probably interrupted the installation or configuration of an important  package. I did that other day, after totally forgetting I was updating  the system on a minimized terminal. It broke my system completely and I  also had to do a fresh install.

I think it is, because when I updated yesterday it also includes some critical update like linux kernel, it already installing but have to wait for flashplugin installer to download.

But my main gripe is the sequences of updating itself. Why update manager want to download, unpack and configure some of the program first ("usual" program that isn't from partner repository) and then downloaded programs which is from partner repository such as flashplugin, ms core fonts, etc. Because when I got hang while downloading those third party repo, then the already configured process get broken??

 > The flashplugin-installer is downloaded from the server of your choice,  listed in the Software Sources. Nevertheless, the plugin itself is  downloaded from [http://archive.canonical.com/pool/pa...e-flashplugin/]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/"), which means is the partner repository on Canonical servers.

How can I do this, should I disable some sources first so it won't conflict with my repo?

---

### Post by lovinglinux on 2010-10-08
> **Isyaltut said:**
> How can I do this, should I disable some sources first so it won't conflict with my repo?

I don't understand the question. If you are talking about disabling the partner repository, it won't work. The flashplugin-installer downloads the flash tar.gz file from the partner repository even if this repository is not enabled in your Software Sources.

---

### Post by QLee on 2010-10-08
[QUOTE=Isyaltut]...
But my main gripe is the sequences of updating itself. Why update manager want to download, unpack and configure some of the program first ("usual" program that isn't from partner repository) and then downloaded programs which is from partner repository such as flashplugin, ms core fonts, etc. Because when I got hang while downloading those third party repo, then the already configured process get broken??
...[/QUOTE]
You're not looking at the problem correctly, it's not that flashplugin caused any of this, your choice to force quit a running update (upgrade) because you wanted to go out is what caused the problem. The package manager is crafted in such a way that it can determine the necessary order of installation so that dependencies can be satisfied, but it can only function correctly when it is allowed to complete. This really isn't too hard a concept to grasp, actually I've seen Windows system that were corrupted by a power loss (which cause another type of "force quit") during an update process. Any system, or script, or program needs to run through to completion to have a chance of accomplishing the task involved. Perhaps thinking of it that way can help you avoid some problems in the future.

Leave yourself plenty of time to do things, trying to rush or impatiently "cancelling, as you have discovered, can cause problems. It's very unfortunate that this happened to your system but it can be a good lesson. I understand the desire to leave the system unattended during the process but I would never do that on any system I cared about and I can't recommend it as a standard practice, sometimes the package manager gives me information about what it is doing and sometimes I want to specify the answer to a question. YMMV, and you may choose to act differently but please don't blame the operating system when it isn't at fault.

---

### Post by Isyaltut on 2010-10-09
> **lovinglinux said:**
> I don't understand the question. If you are talking about disabling the partner repository, it won't work. The flashplugin-installer downloads the flash tar.gz file from the partner repository even if this repository is not enabled in your Software Sources.

Yes. 
Ok, good to know.

> **QLee said:**
> You're not looking at the problem correctly, it's not that flashplugin caused any of this, your choice to force quit a running update (upgrade) because you wanted to go out is what caused the problem. The package manager is crafted in such a way that it can determine the necessary order of installation so that dependencies can be satisfied, but it can only function correctly when it is allowed to complete. This really isn't too hard a concept to grasp, actually I've seen Windows system that were corrupted by a power loss (which cause another type of "force quit") during an update process. Any system, or script, or program needs to run through to completion to have a chance of accomplishing the task involved. Perhaps thinking of it that way can help you avoid some problems in the future.

Leave yourself plenty of time to do things, trying to rush or impatiently "cancelling, as you have discovered, can cause problems. It's very unfortunate that this happened to your system but it can be a good lesson. I understand the desire to leave the system unattended during the process but I would never do that on any system I cared about and I can't recommend it as a standard practice, sometimes the package manager gives me information about what it is doing and sometimes I want to specify the answer to a question. YMMV, and you may choose to act differently but please don't blame the operating system when it isn't at fault.

I leave myself plenty of times to do things already, letting my laptop updating itself while I go to sleep because I don't have a really fast internet connection. About cancelling an ongoing process, well, maybe I'm wrong for doing that, but I needed my laptop at class, what am I have to do in that situation?

But as far as I know package manager download all necessary file first, then installing and configuring it ( I sometimes use option -d in terminal myself ). But when it comes to flash or Ms core fonts, instead the system configuring first and downloaded those files later. Hence, make a potential breaking the system when users choose to cancel it (I know it's not really a good decision, but as I stated above, what am I going to do?)

---

### Post by QLee on 2010-10-09
Just to be clear Isyaltut, I did not mean my comments as a criticism of you, just to point out what I think is important.

[QUOTE=Isyaltut]
But as far as I know package manager download all necessary file first, then installing and configuring it ( I sometimes use option -d in terminal myself ). [/QUOTE]
The key thing here is "as far as you know".


[QUOTE=Isyaltut]But when it comes to flash or Ms core fonts, instead the system configuring first and downloaded those files later. Hence, make a potential breaking the system when users choose to cancel it (I know it's not really a good decision, but as I stated above, what am I going to do?)[/QUOTE]
Remember that both of those are the property of other companies, Ubuntu does not have the right to distribute those. What Ubuntu has done is try to make it easier for a user to choose to download them.

Naturally, you have to choose to do what you need to do, and to deal with the results of your choices. I just wanted to make it clear to others reading this, possibly even reading it previous to trying the update, who might not yet be aware that force quitting an upgrade has a high potential of causing problems.   

I make mistakes all the time too, neither of us needs to worry about that, at least, as long as we don't make the same ones twice and, hopefully, others can learn from this thread.

---

### Post by Isyaltut on 2010-10-09
Alright, point taken.

I should have known better though. I mean, what do I expect from Adobe. Even in Windows they really make things as hard as possible just to install flash with adobe download manager.

---

### Post by QLee on 2010-10-10
[QUOTE=Isyaltut]
I should have known better though. I mean, what do I expect from Adobe. Even in Windows they really make things as hard as possible just to install flash with adobe download manager.[/QUOTE]
Personally I haven't had any unsolvable  problems with Flash but maybe it could change in the future and maybe it could get easier in Windows. The latest "buzz" I heard was that MS is talking to Adobe (unspecified) and Redmond does have a a lot of money. But speculation is always just that, speculation.

---


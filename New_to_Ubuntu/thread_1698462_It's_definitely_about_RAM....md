---
title: "It's definitely about RAM..."
date: 2011-03-02
forum: New to Ubuntu
---

### Post by lrs on 2011-03-02
Maverick shows horrific performance on my old Pentium 4, 512 MB RAM box. The mouse pointer occasionally jerks pretty much everywhere, Flash works very badly with most other things, and opening the Software Centre is fatal. Like, I have to shut down all the other processes, wait for minutes, and then the Centre shudders awake; if I try to install something the computer is basically unusable all throughout 'Applying changes'. The Software Centre has caused crashes on a few occasions.

ANYWAY, so I was looking at the System Monitor and it appears that my RAM bloats really easily; a Youtube video on Chrome along with the Software Centre can push it up to 95%+. Meanwhile my 1.2 GB of swap never goes above 20% used; but I hear it's not intelligent to swap memory upto a limit because hard drives write-read slower. (This is with swappiness raised to 100, by the way.) I've shut off visual effects, done that 200-lines patch, and a few other things, but there isn't much of an improvement. Anyone have any suggestions?

---

### Post by eriktheblu on 2011-03-02
LXDE.

Gnome is resource intensive, LXDE not so much.

Failing that, a lighter distro, or older Ubuntu.

---

### Post by cchhrriiss121212 on 2011-03-02
> Anyone have any suggestions?
Switch to a lighter DE? Try installing the XFCE package (not xubuntu-desktop as it is poor), or LDXE.

> a Youtube video on Chrome along with the Software Centre can push it up to 95%+
What kind of RAM usage do you get with nothing open? Chrome uses a lot of memory in comparison with firefox, so try switching browsers.

---

### Post by mick8985 on 2011-03-02
Dude, Ubuntu is in no way about to run on 512mb any more. I can run into issues with 2 gig if I have a lot of tabs open in chromium with flashplayer running.
I hear good things about crunchbang [http://crunchbanglinux.org/](http://crunchbanglinux.org/)
Alternatively you could start by turning as much as possible stuff you don't need off.
Start in gnome-session-properties.
No bluetooth in the system?... Turn it off.
Check for new hardware? You probably know when you have new hardware... Turn it off
Evolution Alarm Notify. I use webmail.. turn it off

You see where I am going with this?

---

### Post by pieisgood4589 on 2011-03-02
As everyone has suggested, switching to a lighter desktop environment could solve all your problems.

Fluxbox and LXDE are my two suggestions, maybe XFCE would even work, but it's a little more resource-intensive than Fluxbox or LXDE.

Also- Chrome uses processes a little differently. Each tab is like opening another Chrome browser, so if one tab dies, you don't have to restart every single tab you have open. This results in eating of a lot of RAM. Try switching to a lighter browser, like Dillo or Epiphany.

---

### Post by lrs on 2011-03-02
Crunchbang looks really good. I'll try that, or LXDE after that.

Empty Chrome with no other program shows 50% RAM usage; I'm assuming that's close to minimal for GNOME. (Transmission was running when I checked, but I'm not sure that that's a memory *****.)

---

### Post by mick8985 on 2011-03-02
Good luck it, report back how you take to it.

---

### Post by Kixtosh on 2011-03-02
The easiest thing to do is add the LXDE desktop environment. You don't even have to install a new O.S., just use the software center. I think that you will then have to log out of your Gnome session (just log out), and then, before logging back in, choose the LXDE environment which should be available to you.

It's much lighter than Gnome, or XFCE, when I've tried it on laptops limited to 256 MB of RAM (on an old P III too), and I've never run into problems. I have not tried it with 10.10 though.

Otherwise, if you're determined to try a new O.S. entirely, Lubuntu is one of the best lightweight LXDE distros available, but there is not LTS version for now. Peppermint is another one I have tried and liked.

---

### Post by LetUsDesign.it on 2011-03-02
> **lrs said:**
> Maverick shows horrific performance on my old Pentium 4, 512 MB RAM box. The mouse pointer occasionally jerks pretty much everywhere, Flash works very badly with most other things, and opening the Software Centre is fatal. Like, I have to shut down all the other processes, wait for minutes, and then the Centre shudders awake; if I try to install something the computer is basically unusable all throughout 'Applying changes'. The Software Centre has caused crashes on a few occasions.
 
ANYWAY, so I was looking at the System Monitor and it appears that my RAM bloats really easily; a Youtube video on Chrome along with the Software Centre can push it up to 95%+. Meanwhile my 1.2 GB of swap never goes above 20% used; but I hear it's not intelligent to swap memory upto a limit because hard drives write-read slower. (This is with swappiness raised to 100, by the way.) I've shut off visual effects, done that 200-lines patch, and a few other things, but there isn't much of an improvement. Anyone have any suggestions?
 
There is still the common thought that just about any linux distro will work on any old computer.
 
How many times have we heard the following? "Got an old computer? Just throw linux on it!"
 
That was fine when most users were just dealing with CLI or using a very early version of Gnome or KDE.
 
However, running a heavy (relative terms) distro such as Maverick on a P4 is like trying to get Vista or 7 installed on the same machine.
 
If I can echo the others, you're better off with a lighter distro if your system has a limited amount of ram.
 
Good luck.

---

### Post by uRock on 2011-03-02
I'd throw in a 1GB stick of RAM or use Xubuntu on it.

---

### Post by houseworkshy on 2011-03-02
Puppy and slitaz would go like rockets on 512.  I don't recommend an older version of Ubuntu for an online machine as it wouldn't be supported anymore, ok for offline use though.

---

### Post by uRock on 2011-03-02
> **houseworkshy said:**
> Puppy and slitaz would go like rockets on 512.  I don't recommend an older version of Ubuntu for an online machine as it wouldn't be supported anymore, ok for offline use though.
Puppy is great when used on a LiveCD, but even their site recommends against installing it.

There is always Arch, but it requires doing some reading before attempting to install the first time around.

---

### Post by houseworkshy on 2011-03-02
True about Puppy, I should have mentioned that ( thank you) , they do however go on to tell you how it is done.  I have an old machine which was my main one when it ran on Ubuntu 7's and 8's  and winXP.  I've been playing with low resourse distro in order to give it away as working.  Puppy actually worked among the best ( including when running cinelerra :) ), must admit I can't vouch for it's long term stability as I was testing another light distro on it only a couple of days later.  Searching through Distrowatch.com will find many candidates for low resourse systems.  It is worth bearing in mind when looking that "minimum requirements" refer to the ability of the system to run rather than actually doing things on top, so look for comfortably run ( 255 perhaps ) rather than pulling in OS's which are at the RAM ceiling just ticking over.

---

### Post by Kixtosh on 2011-03-02
I tried Puppy, and if you have a built in CD drive, it's a great option, especially if you want to dual boot Windows:

- Puppy CD in the CD drive on boot = Puppy starts.
- No Puppy CD in the CD drive on boot = Windows starts.

It's as easy as that, and yes: it works very well. However, I didn't find any detectable performance advantage (detectable by me, that is) to Puppy when compared to any of the following LXDE environments with a PIII 700 and just 256 MB of RAM:

- Lubuntu
- Xubuntu with the LXDE desktop package (not the default XFCE)
- Peppermint

I got not get SliTaz to install properly, so I did not investigate it further. Peppermint is a great choice, in my opinion (much more attractive for my tastes than Lubuntu, Puppy or Xubuntu), but it's a sort of pseudo "cloud" environment, nicely integrating online Google applications into the desktop applications menu. If you want something more conventional like OpenOffice and other desktop apps with Peppermint, you'll have to install those apps from the software center yourself.

Word of note: when dealing with a Pentium M 1.2 GHz laptop, with 1.28 GB of RAM installed, I found almost no advantage to any lightweight distro compared to regular Ubuntu 10.04 Lucid Lynx (LTS). Memory usage generally at 25-50% only, and swap usage is 0-2%, or thereabouts (whenever I check it, that is).

---

### Post by walt.smith1960 on 2011-03-02
> **uRock said:**
> I'd throw in a 1GB stick of RAM or use Xubuntu on it.

I was thinking the same thing but that may not fix the flash performance.  I had an AthlonXP 2600 which I think is sort of equivalent to a P4 and 1 Gb. RAM.  It did basic stuff OK but flash on some sites was really bad. Other sites flash was acceptable I don't know what the difference was.  On all flash sites CPU usage was running at or close to 100% so it looks like flash is a CPU hog.  Here are a couple screen shots while running one of the most resource intensive sites I visit.
[ATTACH]184884[/ATTACH]
[ATTACH]184885[/ATTACH]

In this case CPU usage is more an issue than RAM.  I wouldn't invest too much money in additional RAM that may not help; you might be better served to put that toward a new MoBo/Processor/RAM setup.  There was a guy asking on this board about building a new computer.  If you search on my user name it'll show up within the past week. If you have some serviceable parts e.g. hard drive, CD/DVD drive you can upgrade the MoBo/CPU/RAM  for around $200.  Of course more $ buys more performance.

---

### Post by egeezer on 2011-03-02
I've been reviving a few old boxes lately, most with 512 RAM, and Peppermint has always worked best for me, either Peppermint One or Peppermint Ice.  I don't use cloud, I just pick from Synaptic as little stuff as will give me a comfortably working system.  I'm beginning to like P-One better than P-Ice, if only for the Firefox 4 betas (up to about 11 or 12 by now).

(Then I eventually get around to upgrading the memory anyway!):oops:

---

### Post by DarthScape on 2011-03-02
Ubuntu 10.10 is a MODERN operating system, meant for running on MODERN systems. If you are running anything older, you would want to use something meant for that time. I would actually suggest running 8.04, works well for Pentium 4's for me.

---

### Post by The Linux Cynic on 2011-03-02
> **egeezer said:**
> Peppermint has always worked best for me, 

Best compared to what? (Not to be rude, just curious).

---

### Post by TenPlus1 on 2011-03-02
Xubuntu works perfectly for my on 512mb of memory and even then I have the swap partition disabled...  Certain services and startup programs can be disabled if you're not going to use them saving more memory and so far my desktop is sitting at 110mb...  Running flash videos and web surfing on Firefox or Opera works fine with no slowdown or hangs...

---

### Post by oldsoundguy on 2011-03-02
OR .. you could spend 20-30 bucks and get more ram from  eBay (provided your motherboard supports it.)
When I part out a machine, the most marketable parts are the drives and the ram.

---

### Post by beew on 2011-03-02
I have 10.10 on an old labtop with 512M of ram. It is fine if I turn off compiz. Forget about playing flash videos, if you want to watch youtube, you can use either minitube or if you use firefox use the flashvideoreplacer plugin (flash is in general bad in Lunux unless you have a newer Nvidia card then the latest version of flash works very nicely).Chrome is bad, it is fast because it uses a lot of ram. On this machine  if I open a few tabs for a 10-15 minutes the system freezes. Firefox3.x  is ok, kind of slugguish but works. FF4 beta is bad news too, same  reason as Chrome.

Don't use the software center, Synaptic appears to work fine and it is better anyway, or you can always use the terminal for installing and updating software.

You can also make the system use more swap (and less ram) by changing  vm.swappiness to 100 (the system doesn't freeze but it will be slow). 


```
gksudo gedit /etc/sysctl.conf
```When the editor opens find the line vm.swappiness=60 and change 60 to 100, save and reboot.

You can also install a light desktop like openbox.


P.S. Windows XP freezes on this thing too, it used to be installed with XP until I got rid of it and change to Ubuntu.

---

### Post by Kixtosh on 2011-03-02
> **beew said:**
> ... Chrome is bad, it is fast because it uses a lot of ram. On this machine  if I open a few tabs for a 10-15 minutes the system freezes. ...I have to admit that I haven't had any problems using Chromium (not Chrome - not sure if there are any real differences when run under any *buntu O.S., but you can get Chrome for *buntu instead of Chromium if you really want to), and certainly I don't think it has ever frozen, even with a dozen tabs being used in two or three simultaneous browsing sessions. This is with an old PIII, and just 256 MB of RAM. There may be something else in the equation that is determining why some people are getting good results with Chromium on very old laptops (P4 and older, 512 MB of RAM or less) and others, apparently, are not.

For that matter, I haven't had frequent problems with Internet Explorer freezing up either, no matter how many tabs I open up when using XP (again, a dozen or so in at least two simultaneous browsing sessions), but that's on a different laptop with 1.28 GB of RAM. On that laptop, I frequently have up to twenty tabs open in four different browsing sessions when using Ubuntu (one for each desktop). Sometimes it's even more.

---

### Post by lrs on 2011-03-03
I've dualbooted Crunchbang with 10.10, and it's going very well; I've even got Youtube running on Chromium along with an OpenOffice install and the computer isn't beginning to complain. (Oh yeah, I did mean Chromium, not Chrome.) Unless something dramatic happens over the long term, this should work really well. 

I'll set this thread to 'solved' now, but all the suggestions have been (and might be, later on) really helpful. Thanks, guys.

---

### Post by wizard10000 on 2011-03-03
> **uRock said:**
> Puppy is great when used on a LiveCD, but even their site recommends against installing it.

I'm a fan of Puppy but not a fan of their security model.  Out of the box Puppy is a single-user system and everything's done as root.  There are hacks to make Puppy multiuser but then you add overhead and the hacks aren't really supported.

It's been a few years but I had pretty good success with Vector Light on older hardware.  It's slack-based and actually runs fairly well on old, weird hardware  ;)

Hardware requirements are 

> Pentium 166 or better, 64MB RAM minimum, 1.8GB hard drive space for full system - more for your data. 

[http://vectorlinux.com/downloads](http://vectorlinux.com/downloads)

---

### Post by ajgreeny on 2011-03-03
I installed Lubuntu 10.10 from the disk with Linux Format magazine 142 from the UK, on a second disk of  my main desktop computer just to have a look at it, as it looked so  good as a live CD. 
 
The only problem was that grub never found the other OSs on the machine.   A search quickly showed that there is a bug in the Lubuntu 10.10 version, with no **os-prober** package installed, so other OSs are never found.  This is quickly sorted by installing os-prober and re-running ```
sudo update-grub
```I hope this may help other users of Lubuntu, who may also have found  this problem.

Apart from that problem, I am so impressed with Lubuntu that I have put  it on my old Acer Travelmate 2200 laptop, (celeron cpu 512 MB ram) which struggles with  Ubuntu 10.10; Lubuntu flies in comparison, using about 60 -70 MB ram most of the time. 
 
However, I did have to delete many of the old hidden config folders from  my separate /home partition, as they completely confused the desktop  setup when I logged in with all the old configuration from ubuntu 10.10  remaining.

---

### Post by Gaygerbil on 2011-03-04
Lubuntu really is the best and it's not as attractive as other OS's but IMO it's not ugly at all. It can be completely customized so that's really not a problem anyway as it runs on Openbox. And if you don't like the panel which is fine IMO, you can put other ones like tint or adeskbar, and conky and compiz work with it.

Overall Lubuntu is probably the best if you're sticking to what you know, (an Ubuntu based distro that's MUCH MUCH lighter).

---

### Post by Dutch70 on 2011-03-04
> **Kixtosh said:**
> The easiest thing to do is add the LXDE desktop environment. You don't even have to install a new O.S., just use the software center. I think that you will then have to log out of your Gnome session (just log out), and then, before logging back in, choose the LXDE environment which should be available to you.

It's much lighter than Gnome, or XFCE, when I've tried it on laptops limited to 256 MB of RAM (on an old P III too), and I've never run into problems. I have not tried it with 10.10 though.

Otherwise, if you're determined to try a new O.S. entirely, Lubuntu is one of the best lightweight LXDE distros available, but there is not LTS version for now. Peppermint is another one I have tried and liked.

+1 on all of this. 

To add to it, you can install Xubuntu, then open synaptic package manager and add the lubuntu desktop. On my old machine it gives several diff desktops to log into now. Just did this last week & it's great. This was the only way I could get Lubuntu installed. I think they're having problems with their installer.

I really like Peppermint One & Peppermint Ice too.

---

### Post by egeezer on 2011-03-06
> **The Linux Cynic said:**
> Best compared to what? (Not to be rude, just curious).

Sorry to reply so late!  Best compared to SliTaz, DSL, Puppy, Debris, TinyME, and antiX.  Probably one or two others I can't recall at the moment.  I keep CDs of Puppy and DSL, but don't use them much.  The others I installed and later removed.

---

